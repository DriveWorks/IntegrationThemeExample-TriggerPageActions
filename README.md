# DriveWorks Live - Integration Theme Example - Trigger Page Actions
### Version: 1.0.0
#### Minimum DriveWorks Version: 18.0

A distributable example that demonstrates how to listen to Form events and trigger on-page actions.

---

Please note: DriveWorks are not accepting pull requests for this example.  
Join our [online community](https://my.driveworks.co.uk) for discussion, resources and to suggest other examples.

---

### This example:

Demonstrates how to react to the following:
- Macro Button presses - in 3 different ways, each with their own pros/cons:
    1. Attach a click event listener directly to a Control.
    2. Attach a click event listener to the Form's permanent parent element.
    3. Attach a click event listener every time the Control is made visible.
- Control Property changes
- Constant changes
- Form Data changes (e.g. active Form name)

### To use:
1. Clone this repository, or download as a .zip

2. Extract the supplied .drivepkg file using the DriveWorks Package Wizard to access the included Project file.

3. Open the extracted Group in DriveWorks Administrator and use 'Form Design' to view each Control and its properties.
    * Most importantly: the **Metadata** property that can be easily targeted via JavaScript.

4. In `DriveWorksLiveConfigUser.xml`, add a new Group Alias for the included example Group e.g. `name="TriggerPageActions"`.
    * See [Integration Theme Connection Settings](https://docs.driveworkspro.com/Topic/IntegrationThemeSettings#Connection-Settings) for additional guidance.

5. To react to a Constant value changing, ensure it is exposed via `DriveWorksConfigUser.xml`
    * In the included example Project (`TriggerPageActions`), the Constant `MyConstantName` is used and listened for in the custom JS click events.
    * This Constant can be exposed like so:
        ```
        <connections>
            <sharedGroupAlias OR individualGroupAlias ...>
                <permissions>
                    <project name="TriggerPageActions">
                        <constant name="MyConstantName">
                            <team name="Administrators" canEdit="true"/>
                        </constant>
                    </project>
                </permissions>
            </sharedGroupAlias OR /individualGroupAlias>
        </connections>
        ```
    * For further help, see [Integration Theme Permission Settings](https://docs.driveworkspro.com/Topic/IntegrationThemeSettings#Permissions).

6. Enter your Integration Theme details into `config.js`.
    * `serverUrl` - The URL that hosts your Integration Theme, including any ports.
    * `groupAlias` - The public alias created for the Group containing the DriveApps to render - as configured in DriveWorksConfigUser.xml.
        * This *must* be specified for each Group you wish to use.
        * This allows you to mask the true Group name publicly, if desired.
        * See [Integration Theme Connection Settings](https://docs.driveworkspro.com/Topic/IntegrationThemeSettings#Connection-Settings) for additional guidance.
    * `projectName` (optional) - The name of the Project to render a Specification from.
        * These is pre-filled with the supplied Project's name, but can be changed if required.

7. Ensure that the Integration Theme server is running, using any of the available methods (e.g. Personal Web Edition, DriveWorks Live, IIS)
    * For more information, see [Selecting the Integration Theme](https://docs.driveworkspro.com/Topic/IntegrationThemeSelect).

8. Open the example HTML files locally (localhost) or on a remote server.
    * Ensure `<corsOrigins>` in DriveWorksConfigUser.xml permits requests from this location.
    * See [Integration Theme Configuration Settings](https://docs.driveworkspro.com/Topic/IntegrationThemeSettings#Configuration-Settings) for additional guidance.

9. If encountering any issues, check the browser's console for error messages (F12)

### Potential Issues:
* When serving this example for a domain different to your DriveWorks Live server, e.g. api.my-site.com from company.com, 'SameSite' cookie warnings may be thrown when the Client SDK attempts to store the current session id.
    * This appears as "Error: 401 Unauthorized" in the browser console, even with the correct configuration set. 
    * To resolve:
        * Ensure you are running DriveWorks 18.2 or above, HTTPS is enabled in DriveWorks Live's settings and a valid SSL certificate has been configured via DriveWorksConfigUser.xml.
        * See [Integration Theme Settings](https://docs.driveworkspro.com/Topic/IntegrationThemeSettings) for additional guidance.

---

This source code has been made available to demonstrate how you can integrate with DriveWorks using the DriveWorks Live API.
This code is provided under the MIT license. For more details, see the included LICENSE file.

The example requires that you have the latest DriveWorks Live SDK installed, operational and remotely accessible.
