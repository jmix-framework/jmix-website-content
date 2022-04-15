# Sneferu

## Jmix integration UI testing library

Sneferu is a testing library to simplify integration testing for a Jmix application. It contains APIs that allows you to express interactions and verifications with UI screens via a high-level testing language.


### Overview

Instead of spending too much time and money maintaining a selenium test suite, Sneferu is the way to have very good test coverage and quality assurance at a fraction of the cost.

Via its easy-to-read language you can create integration tests that are optimized for readability, because this is what matters most for keeping a test suite maintainable & cheap to operate.

Sneferu enables you to:

* verify any business logic in a Screen Controller
* ensure the correct linking between a Screen XML and its Controller counterpart
* verify correct display of any programmatic creation of Screen Components / Dialogs
* verify the data loading from the database through declarative data loading

What Sneferu _does not cover_:

* perform client-side JS based Vaadin UI logic that is executed _only_ in the browser (like showing the date picker popup where it is possible to select a particular date)
* verify rendering issues in the browser

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