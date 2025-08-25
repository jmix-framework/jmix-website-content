## Подключение в проект

Для подключения в проект добавьте в `build.gradle` строку с указанием актуальной версии аддона:

`implementation 'ru.cs_consult:datamodelbrowseaddon-starter:Х.Х.Х'`

## Использование

Аддон добавляет в проект экран с id `dmb_DataModelBrowseScreen`.
Разместите вызов экрана в нужном месте Меню. Ниже приведен пример размещения экрана отображения модели данных под стандартным пунктом меню "Помощь":

```xml
<menu-config xmlns="http://jmix.io/schema/ui/menu">
    ...
    <menu id="Help">
        <item screen="dmb_DataModelBrowseScreen"
              caption="msg://ru.cs_consult.datamodelbrowseaddon.screen.datamodelbrowse/dataModelBrowseScreen.caption"/>
    </menu>
</menu-config>
```

Также, вы можете воспользоваться стандартными способами открытия экранов в Jmix.
Ниже приведен пример открытия в UI экрана отображения модели данных с помощью `ScreenBuilders`

```java
@Autowired
private ScreenBuilders screenBuilders;

private void openDataModelBrowseScreen(FrameOwner origin) {
    screenBuilders.screen(origin)
        .withScreenClass(DataModelBrowseScreen.class)
        .show();
}
```

Если из отображения описания модели данных нужно исключить некоторые сущности (например, служебные сущности или сущности, используемые в автоматических тестах), то укажите имена исключаемых метаклассов в `application.properties`:

```
jmix.datamodelview.excludedMetaClasses = DummyEntity, DummyIdentityIdEntity
```

Предоставить пользователям доступ к экрану отображения модели данных можно с помощью поставляемой с аддоном ресурсной роли `DataModelBrowseUserRole`.
Данная роль определяет политику экранов и политику меню, предоставляя доступ к экрану или пункту меню с id `dmb_DataModelBrowseScreen`.

## Доступные языки

Для формирования контента экрана в формате HTML используются шаблоны на определенных языках.

Аддон поддерживает следующие языки:

- Русский (ru);
- Английский (en).

Если локаль сессии пользователя отличается от поддерживаемых аддоном, будет использован шаблон на английском языке.