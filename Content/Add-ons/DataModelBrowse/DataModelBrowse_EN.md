# DataModelBrowse Add-on

Adds a screen for displaying the application's data structure in a human-readable HTML format.

## Integration into a Project

To integrate the add-on into your project, add the following line with the current version of the add-on to your `build.gradle`:

`implementation 'ru.cs_consult:datamodelbrowseaddon-starter:Х.Х.Х'`

## Usage

The add-on adds a screen with the ID `dmb_DataModelBrowseScreen` to your project.
You can place a menu item for this screen wherever needed. Below is an example of placing the data model browser screen under the standard "Help" menu item:

```xml
<menu-config xmlns="http://jmix.io/schema/ui/menu">
    ...
    <menu id="Help">
        <item screen="dmb_DataModelBrowseScreen"
              caption="msg://ru.cs_consult.datamodelbrowseaddon.screen.datamodelbrowse/dataModelBrowseScreen.caption"/>
    </menu>
</menu-config>
```

You can also use standard Jmix mechanisms for opening screens.
The following example demonstrates opening the data model browser screen via `ScreenBuilders`:

```java
@Autowired
private ScreenBuilders screenBuilders;

private void openDataModelBrowseScreen(FrameOwner origin) {
    screenBuilders.screen(origin)
        .withScreenClass(DataModelBrowseScreen.class)
        .show();
}
```

If you need to exclude certain entities from the model description (e.g., system entities or entities used in automated tests), specify the names of the excluded metaclasses in `application.properties`:

```
jmix.datamodelview.excludedMetaClasses = DummyEntity, DummyIdentityIdEntity
```

Access to the data model browser screen can be granted using the `DataModelBrowseUserRole` resource role included with the add-on.
This role defines both screen and menu policies to allow access to the screen or menu item with the ID `dmb_DataModelBrowseScreen`.

## Supported Languages

HTML content for the screen is generated using language-specific templates.

The add-on supports the following languages:

- Russian (ru);
- English (en).

If the user session locale is not supported by the add-on, the English template will be used by default.