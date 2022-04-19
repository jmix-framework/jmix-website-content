# Sneferu
# Sneferu

## Jmix integration UI testing library
## Jmix UI 集成测试库

Sneferu is a testing library to simplify integration testing for a Jmix application. It contains APIs that allows you to express interactions and verifications with UI screens via a high-level testing language.
Sneferu 是一个测试库，用于简化 Jmix 应用程序的集成测试。其 API 支持使用高级别的测试语言编写 UI 界面的交互和验证。

### Overview
### 简介

Instead of spending too much time and money maintaining a selenium test suite, Sneferu is the way to have very good test coverage and quality assurance at a fraction of the cost.
无需花费大量的时间和成本维护 selenium 测试套件，Sneferu 以极低的成本提供很好的测试覆盖率和质量保障。

Via its easy-to-read language you can create integration tests that are optimized for readability, because this is what matters most for keeping a test suite maintainable & cheap to operate.
通过其易于理解的语言，您可以创建高可读性的集成测试用例，这对于保持测试套件的可维护性和低成本至关重要。

Sneferu enables you to:
Sneferu 特性：

* verify any business logic in a Screen Controller
* ensure the correct linking between a Screen XML and its Controller counterpart
* verify correct display of any programmatic creation of Screen Components / Dialogs
* verify the data loading from the database through declarative data loading

* 验证界面控制器中的任何业务逻辑
* 确保界面 XML 及其控制器之间的正确链接
* 验证任何以编程方式创建的“界面组件/对话框”的正确显示
* 验证声明式的数据加载

What Sneferu _does not cover_:
Sneferu 不涵盖的内容：

* perform client-side JS based Vaadin UI logic that is executed _only_ in the browser (like showing the date picker popup where it is possible to select a particular date)
* verify rendering issues in the browser

* 仅在浏览器中执行的客户端 Vaadin UI 逻辑（例如展示日期选择器中的弹窗）
* 验证浏览器中的渲染问题

![Sneferu Landscape](https://raw.githubusercontent.com/mariodavid/jmix-sneferu/main/img/sneferu-overview.png)

### Example


```java
import de.diedavids.sneferu.UiTestAPI;
import de.diedavids.sneferu.SneferuUiTest;

import static de.diedavids.sneferu.ComponentDescriptors.*;
import static de.diedavids.sneferu.Interactions.*;
import static org.assertj.core.api.Assertions.assertThat;

@SpringBootTest
@SneferuUiTest(authenticatedUser = "admin", mainScreenId = "petclinic_MainScreen", screenBasePackages = "io.jmix.petclinic")
class FirstSneferuTest {

    @Test
    void openScreen_clickButton_verifyWhichScreenIsActive(UiTestAPI uiTestAPI) {

        // given:
        final StandardLookupTestAPI<Visit, VisitBrowse> visitBrowse = uiTestAPI.openStandardLookup(Visit.class, VisitBrowse.class);

        // when:
        visitBrowse.interact(click(button("createBtn")));

        // then:
        assertThat(uiTestAPI.isActive(uiTestAPI.getOpenedEditorScreen(VisitEdit.class))).isTrue();
    }
}
```
