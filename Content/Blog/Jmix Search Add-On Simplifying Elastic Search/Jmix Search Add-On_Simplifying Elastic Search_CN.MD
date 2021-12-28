# Jmix 搜索扩展插件 - 简化 Elastic Search

summary: 对于数据类型的应用程序来说，提供强大的搜索能力是非常有用的。

## 简介

对于数据类型的应用程序来说，提供强大的搜索能力是非常有用的。在 CUBA 平台，有一个基于 [Lucene](https://lucene.apache.org/) 的扩展插件 “FTS”。而在 Jmix，我们对搜索引擎进行了重构，改为使用 [Elasticsearch（以下简称 ES）](https://www.elastic.co/)。

ES 是基于 Lucene 的，而且使用了相同的概念 - 文档和索引。Jmix 是用于以数据为中心的应用程序，因此，我们需要根据关系型数据库存储的数据来创建文档和建立索引。
 
本文将讨论在 Spring Boot 中使用 ES 的方案，以及在基于 Spring Boot 的 Jmix 中如何实现。

## Spring Boot 方案

Spring Boot 有个[单独的项目](https://docs.spring.io/spring-data/elasticsearch/docs/current/reference/html/) 来支持 ES。

为了在 Spring Boot 应用程序中使用 ES，与 JPA 实体类似，我们需要用 Java 类来定义“文档”。下面是 Spring 手册中的一个例子：

```java
@Document(indexName="books")
class Book {
    @Id
    private String id;

    @Field(type = FieldType.text)
    private String name;

    @Field(type = FieldType.text)
    private String summary;

    @Field(type = FieldType.Integer)
    private Integer price;

	// getter/setter ...
}
```  

这里定义了一个可索引的文档，包括字段和索引名称。为了使用索引、保存文档以及实现搜索功能，我们需要创建类似下面的 Spring Data repository：

```java
interface BookRepository extends Repository<Book, String> {
  List<Book> findByNameAndPrice(String name, Integer price);
}
``` 

Spring Boot 的 ES API 很成熟，而且开发者对它们也比较熟悉，但是如果想实现对数据库进行搜索，就不那么容易了。需要实现下面这些内容：

创建索引：
1. 创建带有 ID 字段和表名的文档，关联至真正的数据
2. 当数据发生保存或者更新时，需要拷贝更新的数据行来创建一个文档
3. 将文档发送至 ES

进行搜索：
1. 根据查询语句找到文档
2. 根据文档的表名和 ID 找到对应的实体

虽然这也不是很复杂的工作，但还是需要编写一些代码。所以，有没有办法能简化这个过程呢？

## Jmix 方案

在 Jmix 中，我们提供了[配置 ES 索引](https://docs.jmix.io/jmix/1.0/search/create_index_definitions.html)的简便方法。如果开发者使用过 CUBA 的 BPM 或 Security，那就不会觉得陌生，对于有经验的 Spring Boot 开发者来说，这个方案也不会很难懂。下面看看为 Book 这个 JPA 实体配置索引的过程：

```java
@Table(name = "book")
@Entity
public class Book {

    @Id
    private UUID id;

    private String name;

    private String summary;

    private Integer price;


    // getter/setter ...
}

```

如果我们想用 ES 来定义搜索 book 的索引，只需要定义带有一个方法的接口：

```java
@JmixEntitySearchIndex(entity = Book.class)
public interface BookIndexDefinition {
	@AutoMappedField(includeProperties = {"name", "summary", "price"})
	void bookMapping();
}
```

之后，索引会在启动时自动创建。创建索引时有很多可选参数：比如可以用掩码从索引中添加或者删除某些实体字段、可以包含关联实体，甚至为上传的文件也创建索引等等。参考扩展插件的[文档](https://docs.jmix.io/jmix/1.0/search/advanced_mapping.html)了解更多信息。

好了，现在我们创建了索引，如何为索引增加数据呢？在 Jmix 中，我们配置了一个实体追踪监听器以及一个队列（queue），用来存储实体的改动。监听器会跟踪实体内那些包含在索引中的字段变化，然后将这些变化添加到队列中。另外，我们还有第三个组件，一个 quartz job，用来更新 ES 索引。

下图是详细的搜索架构：

![search_architecture.png]({{strapiUrl}}/uploads/search_architecture_5f06326fa4.png)

因此，Jmix 框架能自动创建和更新索引。然后，我们只需要使用 EntitySearcher 服务将查询发送至 ES，接收结果并返回相应的实体集即可。

Jmix 搜索扩展插件非常容易配置和使用，但是有一定局限性：不支持原生 ES 查询语句，因而在灵活性上有一些不足。如果需要使用这个功能，可以添加 Spring Boot ES 依赖库，用它提供的 API 来执行任意的查询。

### 在后台 UI 使用搜索

为了在后台（backoffice） UI 实现搜索功能，Jmix 框架提供了一个组件。这个组件基本上就是一个文本框，与我们在谷歌或者百度搜索引擎看到的差不多，并且提供了一些[高级功能](https://docs.jmix.io/jmix/1.0/search/search_ui_component_fine_tuning.html)。

![search.png]({{strapiUrl}}/uploads/Search_UI_143fd48910.png)

在界面描述中用一个 xml 标签表示：

```xml
<search:searchField id="bookSearchField" entities="Book"/>
```

按照上面的代码配置之后，该组件会对所有添加至索引的 book 进行搜索。比如，如果 book 有下面这些数据：

![Books.png]({{strapiUrl}}/uploads/Books_bf65243c2e.png)

当搜索 “jungle” 这个词时，搜索组件会打开一个界面展示字段中包含该单词的所有 book。

![Search_Result.png]({{strapiUrl}}/uploads/Search_Result_9a698fe156.png)

如果点击实体名称，能打开所选实体的编辑界面。

除此之外，我们还能为通用过滤器[添加全文检索](https://docs.jmix.io/jmix/1.0/search/full_text_search_in_filters.html)功能。除了已有的 JPQL、属性和分组条件之外，我们可以看到一个新的 “Full-text condition” 选项。选择这个选项，可以选择并使用特定的搜索策略。

![condition_editor.png]({{strapiUrl}}/uploads/condition_editor_dbe15d92d1.png)

## 结论

在 Jmix 中，我们还是坚持了一直遵循的方案：挑选经过实战检验的框架、在此之上构建 API，然后尽可能的简化用法，但另一方面，我们不会对开发者隐藏任何实现细节。

使用 Jmix 可以更加快捷、容易的为数据库构建全文检索索引。开发者要做的仅限于定义接口并为方法添加注释，剩下的工作就交给我们的自动数据队列和定时任务。除了使用 Jmix 的 API 搜索数据之外，还支持任何兼容 ES 的工具进行搜索，当然，也支持 Jmix 的后台 UI。


