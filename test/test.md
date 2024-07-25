# Documentation in GitHub (2)

## XUI Components

This UI library is designed to simplify and enhance the development of user interfaces in Angular applications.

- XPgListComponent
    
    
    The `xpglist` component in the XUI framework is responsible for displaying lists of entities in the UI. It dynamically loads schemas, defines properties, and fetches data based on configurations.
    
    ## Code Structure:
    
    ```jsx
    loadComponent() {
        this.component = XPgListComponent;
        this.injector = Injector.create({
          providers: [
            {
              provide: XPgListParamProvider,
              useValue: new XPgListParam({
                entityName: 'template',
                detailsComp: TemplateDetComponent,
                onInit: (instance: XPgListComponent) => {},
                sidebarFullSize: true,
              } as XpgListPageConfig),
            },
          ],
          parent: this.inj,
        });
      }
    
    ```
    
    - **Component Assignment**: The `this.component` assignment sets the component type to `XPgListComponent`, indicating that this is the component to be rendered for displaying a list of items.
    
    **Injector Creation**: An `Injector` instance is created to provide dependencies for the `XPgListComponent`.
    - **Providers**: A provider is defined to supply an instance of `XPgListParamProvider`.
    - **XPgListParamProvider**: An abstract class used as a base for providing list parameters in the component. It holds the `xpgListPageConfig` object, which contains configuration and data for list management.
    - **XPgListParam**: A concrete class extending `XPgListParamProvider`. It provides a specific implementation of the `XPgListParamProvider` service, initialized with `xpgListPageConfig`. This class is used to pass list configuration to the component.
    - **xpgListPageConfig**: An interface defining the structure and properties required for list management,
    
    ## Properties of `xpgListPageConfig`:
    
    | Property | Type | Function |
    | --- | --- | --- |
    | entityName | string | Specifies the entity the component will interact with. It is used to determine the appropriate backend API endpoints for data fetching. |
    | columns | Property[] | Defines an array of Property objects that specify additional configurations and customizations for each property of the entity to be displayed as a column. This includes specifying custom templates (cellTemplate), custom names (name), and other configurations like hiding columns (hidden). |
    | onInit | (instance?: any) => void | A callback function that is executed when the component is initialized. It provides access to the component instance, allowing for custom initialization logic |
    | onListChange | () => void
     | A callback function that is triggered when there is a change in the list data. It allows for custom logic to be executed in response to modifications in the list, such as updating data, filtering items, or adjusting UI elements based on the new state of the list. |
    | readComp | Type<any>; | Specifies a component used for displaying the read-only view of an entity. This component allows users to view details without modifying or interacting with the data. |
    | detailsComp | Type<any>; | Specifies a component used for displaying the editable or action-oriented view of an entity. This component allows users to modify, edit, or perform actions related to the entity. |
    | sidebarFullSize | boolean | Determines if the sidebar should take up the full width of the screen (true) or a smaller portion of it (false). Enhances layout flexibility and adjusts the UI based on design requirements. |
    | parentEntity | string | Specifies the entity name of the parent item. |
    | parentId | string | Holds the identifier of the parent item. |
    | parentProp | string | Specifies a particular property of the parent entity. |
    | parentPageMode | PageMode | Specifies the mode of the parent page, which can be 'create', 'update', or 'read'. |
    | parentItem | any | Holds the entire parent item object. |
    | filterTpl | TemplateRef<any> | Specifies the template to use for custom filtering in different parts of the component. |
    | filterBeforeTpl | TemplateRef<any> | Defines a custom template for filtering before the main filter template is applied. |
    | afterActionTemplate | TemplateRef<any>; | - - |
    | headerTpl | TemplateRef<any>; | A template reference that defines the custom header content for the component. This template can include any HTML or Angular components and is typically used to customize the appearance and functionality of the header section of a list, table, or page. |
    | replaceTitleTpl | TemplateRef<any>; |  |
    | staticFilter | string | A static filter applied to the list query to filter the items based on a specific condition. |
    | update | (row: any) => void; | A function that updates a specified row's details in a list.  |
    | read | (row: any) => void; | A function that reads the details of a specified row.  |
    | onDataRequest | (query: any) => any; | - - |
    | replaceListTpl | TemplateRef<any>; |  |
    | requestMethod | string | - - |
    | disablePaginator | boolean | A flag to enable or disable the pagination control for the list. If true, pagination is disabled. |
    | enableCheckBox | boolean | A flag to enable or disable checkboxes in the list. |
    | checkboxTpl | TemplateRef<any> | A template reference for the checkbox column, defining the structure and behavior of the checkboxes. |
    | rowClass | { [x: string]: string } | - - |
    | hiddenColumns | string[] | An array of strings specifying the columns to be hidden in the UI. These columns will not be displayed in the table but can still be part of the data set and used programmatically. In the project it uses  defaultHiddenColumns.filter to specify columns that should not be displayed. |
    
    ## Output
    
    Here is a description for the `XPgListComponent` usage based on the screenshot and provided details:
    
    ---
    
    **Template Management Overview**
    
    In the example shown, the `XPgListComponent` is used in the `template.component.ts` to manage and display various template types. This page is part of the Template Management system and includes sections for Template Types and Template Master.
    
    ![Untitled](Documentation%20in%20GitHub%20(2)%20e3669e943a314c4996a129e2dc1e8ff9/Untitled.png)
    
    - **Template Types**: This section displays a list of different template types such as HTML, Document, and Email. Each template type is listed with attributes like code, name, and document type.
    - **Actions**: For each template type, users can perform actions such as editing or deleting the template type. These actions are enabled by the `XPgListComponent` to facilitate interaction with the template data.
    - **UI Elements**: The page includes UI elements like tables, action buttons (edit, delete), and filters to help users manage template types efficiently. The table displays the data in a structured format, allowing users to view and interact with the template types easily.
- XPgDetailsComponent
    
    
    The `XPgDetailsComponent` is an Angular component used for displaying and editing detailed information about a specific item in an application. This component provides an interactive interface where users can view, modify, and save changes to the item's data.
    
    ## Code Structure:
    
    ```
    loadComponent() {
    this.component = XPgDetailsComponent;
        this.injector = Injector.create({
          providers: [
            {
              provide: XPgDetailsParamProvider,
              useValue: new XPgDetailsParam(xpgDetailsPageConfig),
            },
          ],
          parent: this.inj,
        });
      }
    
    ```
    
    - `this.component = XPgDetailsComponent;` sets the component type to `XPgDetailsComponent`, indicating that this is the component to be rendered for displaying and editing details. This assignment specifies that the `XPgDetailsComponent` will be dynamically loaded and used for presenting the detail view.
    
    **Injector Creation**:
    
    - An `Injector` instance is created to provide dependencies for the `XPgDetailsComponent`.
    - **Providers**:
        - A provider is defined to supply an instance of `XPgDetailsParamProvider` using the `XPgDetailsParam` class, which is initialized with `xpgDetailsPageConfig`. This allows the `XPgDetailsComponent` to access configuration and parameters necessary for its operation.
    - **XPgDetailsParamProvider**:
        - An abstract class used as a base for providing details page parameters. It holds the `xpgDetailsPageConfig` object, which contains configuration settings and callbacks for the detail page.
        
        **XPgDetailsParam**:
        
        - A concrete class extending `XPgDetailsParamProvider`. It provides a specific implementation of the `XPgDetailsParamProvider` service, initialized with `xpgDetailsPageConfig`. This class is used to pass configuration details to the component.
        
        **XpgDetailsPageConfig**:
        
        - An interface defining the structure and properties required for configuring the details page. It includes various settings such as `entityName`, `columns`, `onInit`, `close`, `save`, and several other optional properties. This interface is used to set up the detail page and control its behavior within the `XPgDetailsComponent`.
    
    ## Properties of xpgDetailsPageConfig:
    
    | Property | Type | Function |
    | --- | --- | --- |
    | entityName | string | Specifies the entity the component will interact with. It is used to determine the appropriate backend API endpoints for data fetching. |
    | orgPageMode | PageMode | Represents the original page mode. It is used to store and determine the initial state of the page mode, which can be critical for maintaining consistent behavior when the page is first loaded or revisited. Typically set to values like 'read' or 'create', it serves as a reference point for conditional logic throughout the page lifecycle. |
    | pageMode | PageMode | This property reflects the current mode of the page, which can be dynamically updated based on various conditions and user interactions. It ensures that the UI correctly adapts to the current state, whether it needs to be in 'read', 'create', or any other mode. |
    | id | string | - - |
    | item | ItemEntityDto<string> | Represents the data object for the component. In this context, ItemEntityDto<string> is a generic DTO that includes properties and methods for managing the item data. It can be used to pass data into the component and access various item-related functionalities within the component. |
    | columns | Property[] | Defines an array of Property objects that specify additional configurations and customizations for each property of the entity to be displayed as a column. This includes specifying custom templates (cellTemplate), custom names (name), and other configurations like hiding columns (hidden). |
    | onInit | (instance?: any) => void | A callback function that is executed when the component is initialized. It provides access to the component instance, allowing for custom initialization logic |
    | close | (refresh?: boolean, message?: Message) => void | Defines a callback function to be executed when closing the component or page. The refresh parameter indicates whether the data should be refreshed after closing, and the message parameter can be used to pass any specific messages to be displayed or processed. |
    | onBeforeSave | (stayafter?: boolean, callback?: any) => void | Function executed before saving the current state. It handles pre-save logic, such as setting processing states or triggering additional actions like permission submission. Ensures that necessary conditions or processes are met before the actual save operation is performed. |
    | save | (row: any, message?: Message, refresh?: boolean) => void | - - |
    | onAfterSave | (nItem: ItemEntityDto<string>, resultMsg: string, stayafter: boolean) => void | This function is invoked after the save operation has completed. It performs necessary post-save actions such as displaying a success message, refreshing the relevant components, and updating the page mode to 'update'. It ensures that the UI reflects the new state of the saved item and provides feedback to the user. |
    | onItemSave | (activeTab: any, result: XFormResult) => void | Function executed upon saving an item. It handles post-save logic, such as refreshing the page or navigating to a specific tab. Ensures that the UI is updated and the item save process is completed smoothly. |
    | onTabLoaded | (tabItem: any) => void | Function executed when a tab is loaded. It handles post-load logic specific to the tab, such as triggering additional actions or navigating to specific elements. Ensures that necessary operations are performed once the tab is fully loaded. |
    | editProperties | Property[] | Array of Property objects that define the editable properties of a form. It includes properties and their configurations, such as visibility and editability, which can be dynamically modified based on user actions or other conditions. |
    | _onLoad | (instance?: any) => void | - - |
    | menuMode | 'top' 'left' | An  property that specifies the position of the menu items. It can be set to either 'top' or 'left', indicating whether the menu should be displayed at the top or on the left side of the component. |
    | breadcrumbItems | MenuItem[] | A array of menu items that represent the breadcrumb navigation. Breadcrumb items are typically displayed at the top of the page, showing the user's current location within the application and allowing navigation to previous pages. Each MenuItem can have properties such as label, icon, command, and more, to define its appearance and behavior. |
    | breadcrumbAfter | TemplateRef<any> | Template reference for content to be displayed after the breadcrumb section in the UI. It allows for additional components or information to be shown alongside or following the breadcrumb navigation. |
    | formContentTpl | TemplateRef<any> | - - |
    | headerTpl | TemplateRef<any> | A template reference that defines the custom header content for the component. This template can include any HTML or Angular components and is typically used to customize the appearance and functionality of the header section of a list, table, or page. |
    | afterTemplate | TemplateRef<any> | - - |
    | rightTpl | TemplateRef<any> | A template reference that defines custom content to be displayed on the right side of the component. This template can be used to render specific sections or details, such as a preview pane, additional information, or a custom layout for data presentation. |
    | afterFooterBtn | TemplateRef<any> | Template reference for custom content or buttons to be displayed after the main footer area. This can include actions like "Submit" that are context-sensitive and appear only when certain conditions are met, such as when the form is not in read-only mode. It provides additional functionality relevant to the user’s current interaction. |
    | beforeFooterBtn | TemplateRef<any> | Template reference for custom content or buttons to be displayed before the main footer area. It allows for conditional controls or information to be presented based on the state of the page, such as showing cancellation options or status-specific buttons before the footer. This enhances user interaction by offering relevant actions in the appropriate context. |
    | arrayFooterBtn | TemplateRef<any> | Template reference for custom footer buttons or content to be displayed at the bottom of the page. It allows for dynamic and context-specific actions, such as navigation or additional controls, to be included in the footer area based on the page mode or other conditions. This enhances user interaction by providing relevant functionality in a consistent footer layout. |
    | formBeforeTpl | TemplateRef<any> | Defines the template for content displayed before the main form. Used to provide preliminary instructions or information relevant to the form. |
    | formAfterTpl | TemplateRef<any> | Specifies the template for content displayed after the main form. Used for displaying additional actions or messages, such as consent or confirmation. |
    | formRightTpl | TemplateRef<any> | Indicates the template for content displayed to the right of the main form. Used for supplementary components or information that complements the form. |
    | parentEntity | string | Specifies the entity name of the parent item. |
    | parentId | string | Holds the identifier of the parent item. |
    | parentPageMode | PageMode | Specifies the mode of the parent page, which can be 'create', 'update', or 'read'. |
    | parentItem | any | Holds the entire parent item object. |
    | enableWatchList | boolean | Option to enable watch list. |
    | disableTabs | boolean | - - |
    | disableGeneralTab | boolean | Option to disable the general tab. |
    | batchSave | boolean | Option to enable batch save.+ |
    | refresh | () => void | Optional function to refresh the page.+ |
    | gotoRead | (row: any) => void | - - |
    | disableConcurrency | boolean | This boolean property controls whether concurrency checks are enforced during data operations. Setting it to true disables concurrency control, allowing multiple processes or users to modify the data simultaneously without triggering conflicts or locks. |
    | hidePrevNext | boolean | Option to hide previous and next buttons. |
    | hideSaveStay | boolean | Option to hide the save and stay button. |
    | saveLabel | string | Optional label for the save button. |
    | saveIcon | string | Optional icon for the save button. |
    | hideSave | boolean | Option to hide the save button. |
    
    ## Output:
    
    The `XPgDetailsComponent` is used for displaying and editing detailed information of selected items in the application. Unlike read-only components, the `XPgDetailsComponent` allows for user interaction to update and save changes to the data. In this context, it is specifically used in the Ebury Outbound page to manage mass payment operations and view detailed transaction data.
    
    ![Untitled](Documentation%20in%20GitHub%20(2)%20e3669e943a314c4996a129e2dc1e8ff9/Untitled%201.png)
    
    - In the screenshot, you can see the Ebury Outbound page where the `XPgDetailsComponent` is used to display a detailed view of a selected mass payment operation.
    - The right side of the screenshot shows the pop-up with detailed information, including various data fields and options for interacting with the data, such as viewing and editing JSON responses.
    
- XPgDetComponent
    
    
    The `XPgDetComponent` is a key component within the XUI framework that enables the creation of editable detail pages. This component allows users to modify specific entity details through an intuitive and dynamic interface.
    
    ## Code Structure:
    
    ```jsx
    this.component = XPgDetComponent;
    this.injector = Injector.create({
    providers: [
    {
    provide: XPgDetailsParamProvider,
    useValue: new XPgDetailsParam(xpgDetailsPageConfig),
    },
    ],
    parent: this.inj,
    });
    ```
    
    **Component Assignment**:
    
    - `this.component = XPgDetComponent;` sets the component type to `XPgDetComponent`, indicating that this is the component to be rendered for displaying and editing details.
    
    **Injector Creation**:
    
    - An `Injector` instance is created to provide dependencies for the `XPgDetComponent`.
    - **Providers**:
        - A provider is defined to supply an instance of `XPgDetailsParamProvider` using the `XPgDetailsParam` class, which is initialized with `xpgDetailsPageConfig`. This allows the `XPgDetComponent` to access configuration and parameters necessary for its operation.
    - **XPgDetailsParamProvider**:
        - An abstract class used as a base for providing details page parameters. It holds the `xpgDetailsPageConfig` object, which contains configuration settings and callbacks for the detail page.
        
        **XPgDetailsParam**:
        
        - A concrete class extending `XPgDetailsParamProvider`. It provides a specific implementation of the `XPgDetailsParamProvider` service, initialized with `xpgDetailsPageConfig`. This class is used to pass configuration details to the component.
        
        **XpgDetailsPageConfig**:
        
        - An interface defining the structure and properties required for configuring the details page. It includes various settings such as `entityName`, `columns`, `onInit`, `close`, `save`, and several other optional properties. This interface is used to set up the detail page and control its behavior within the `XPgDetComponent`.
    
    ## Properties of xpgDetailsPageConfig:
    
    | Property | Type | Function |
    | --- | --- | --- |
    | entityName | string | Specifies the entity the component will interact with. It is used to determine the appropriate backend API endpoints for data fetching. |
    | orgPageMode | PageMode | Represents the original page mode. It is used to store and determine the initial state of the page mode, which can be critical for maintaining consistent behavior when the page is first loaded or revisited. Typically set to values like 'read' or 'create', it serves as a reference point for conditional logic throughout the page lifecycle. |
    | pageMode | PageMode | This property reflects the current mode of the page, which can be dynamically updated based on various conditions and user interactions. It ensures that the UI correctly adapts to the current state, whether it needs to be in 'read', 'create', or any other mode. |
    | id | string | - - |
    | item | ItemEntityDto<string> | Represents the data object for the component. In this context, ItemEntityDto<string> is a generic DTO that includes properties and methods for managing the item data. It can be used to pass data into the component and access various item-related functionalities within the component. |
    | columns | Property[] | Defines an array of Property objects that specify additional configurations and customizations for each property of the entity to be displayed as a column. This includes specifying custom templates (cellTemplate), custom names (name), and other configurations like hiding columns (hidden). |
    | onInit | (instance?: any) => void | A callback function that is executed when the component is initialized. It provides access to the component instance, allowing for custom initialization logic |
    | close | (refresh?: boolean, message?: Message) => void | Defines a callback function to be executed when closing the component or page. The refresh parameter indicates whether the data should be refreshed after closing, and the message parameter can be used to pass any specific messages to be displayed or processed. |
    | onBeforeSave | (stayafter?: boolean, callback?: any) => void | Function executed before saving the current state. It handles pre-save logic, such as setting processing states or triggering additional actions like permission submission. Ensures that necessary conditions or processes are met before the actual save operation is performed. |
    | save | (row: any, message?: Message, refresh?: boolean) => void | - - |
    | onAfterSave | (nItem: ItemEntityDto<string>, resultMsg: string, stayafter: boolean) => void | This function is invoked after the save operation has completed. It performs necessary post-save actions such as displaying a success message, refreshing the relevant components, and updating the page mode to 'update'. It ensures that the UI reflects the new state of the saved item and provides feedback to the user. |
    | onItemSave | (activeTab: any, result: XFormResult) => void | Function executed upon saving an item. It handles post-save logic, such as refreshing the page or navigating to a specific tab. Ensures that the UI is updated and the item save process is completed smoothly. |
    | onTabLoaded | (tabItem: any) => void | Function executed when a tab is loaded. It handles post-load logic specific to the tab, such as triggering additional actions or navigating to specific elements. Ensures that necessary operations are performed once the tab is fully loaded. |
    | editProperties | Property[] | Array of Property objects that define the editable properties of a form. It includes properties and their configurations, such as visibility and editability, which can be dynamically modified based on user actions or other conditions. |
    | _onLoad | (instance?: any) => void | - - |
    | menuMode | 'top' 'left' | An  property that specifies the position of the menu items. It can be set to either 'top' or 'left', indicating whether the menu should be displayed at the top or on the left side of the component. |
    | breadcrumbItems | MenuItem[] | A array of menu items that represent the breadcrumb navigation. Breadcrumb items are typically displayed at the top of the page, showing the user's current location within the application and allowing navigation to previous pages. Each MenuItem can have properties such as label, icon, command, and more, to define its appearance and behavior. |
    | breadcrumbAfter | TemplateRef<any> | Template reference for content to be displayed after the breadcrumb section in the UI. It allows for additional components or information to be shown alongside or following the breadcrumb navigation. |
    | formContentTpl | TemplateRef<any> | - - |
    | headerTpl | TemplateRef<any> | A template reference that defines the custom header content for the component. This template can include any HTML or Angular components and is typically used to customize the appearance and functionality of the header section of a list, table, or page. |
    | afterTemplate | TemplateRef<any> | - - |
    | rightTpl | TemplateRef<any> | A template reference that defines custom content to be displayed on the right side of the component. This template can be used to render specific sections or details, such as a preview pane, additional information, or a custom layout for data presentation. |
    | afterFooterBtn | TemplateRef<any> | Template reference for custom content or buttons to be displayed after the main footer area. This can include actions like "Submit" that are context-sensitive and appear only when certain conditions are met, such as when the form is not in read-only mode. It provides additional functionality relevant to the user’s current interaction. |
    | beforeFooterBtn | TemplateRef<any> | Template reference for custom content or buttons to be displayed before the main footer area. It allows for conditional controls or information to be presented based on the state of the page, such as showing cancellation options or status-specific buttons before the footer. This enhances user interaction by offering relevant actions in the appropriate context. |
    | arrayFooterBtn | TemplateRef<any> | Template reference for custom footer buttons or content to be displayed at the bottom of the page. It allows for dynamic and context-specific actions, such as navigation or additional controls, to be included in the footer area based on the page mode or other conditions. This enhances user interaction by providing relevant functionality in a consistent footer layout. |
    | formBeforeTpl | TemplateRef<any> | Defines the template for content displayed before the main form. Used to provide preliminary instructions or information relevant to the form. |
    | formAfterTpl | TemplateRef<any> | Specifies the template for content displayed after the main form. Used for displaying additional actions or messages, such as consent or confirmation. |
    | formRightTpl | TemplateRef<any> | Indicates the template for content displayed to the right of the main form. Used for supplementary components or information that complements the form. |
    | parentEntity | string | Specifies the entity name of the parent item. |
    | parentId | string | Holds the identifier of the parent item. |
    | parentPageMode | PageMode | Specifies the mode of the parent page, which can be 'create', 'update', or 'read'. |
    | parentItem | any | Holds the entire parent item object. |
    | enableWatchList | boolean | Option to enable watch list. |
    | disableTabs | boolean | - - |
    | disableGeneralTab | boolean | Option to disable the general tab. |
    | batchSave | boolean | Option to enable batch save.+ |
    | refresh | () => void | Optional function to refresh the page.+ |
    | gotoRead | (row: any) => void | - - |
    | disableConcurrency | boolean | This boolean property controls whether concurrency checks are enforced during data operations. Setting it to true disables concurrency control, allowing multiple processes or users to modify the data simultaneously without triggering conflicts or locks. |
    | hidePrevNext | boolean | Option to hide previous and next buttons. |
    | hideSaveStay | boolean | Option to hide the save and stay button. |
    | saveLabel | string | Optional label for the save button. |
    | saveIcon | string | Optional icon for the save button. |
    | hideSave | boolean | Option to hide the save button. |
    
    ## Output:
    
    In the example below, you can see the Veson IMOS Config page where the `XPgDetComponent` is utilized. This component provides a detailed view that allows users to edit the configuration data.
    
    ![Untitled (7).png](Documentation%20in%20GitHub%20(2)%20e3669e943a314c4996a129e2dc1e8ff9/Untitled_(7).png)
    
    - The `XPgDetComponent` is used for creating editable detail pages in the application. Unlike read-only components, the `XPgDetComponent` allows for user interaction to update and save changes to the data. In this context, it is specifically used in the Veson IMOS Config page to manage configurations such as client information, API tokens, and other settings.
    - When a user clicks the edit button, the `XPgDetComponent` is loaded, providing a form-like interface to modify details. This component handles the display of various properties, enforces validation, and processes the save operations.
    
- XFormComponent
    
    
    The `XFormComponent` is a versatile form component within the XUI framework designed to handle both data entry and data display tasks. It provides a standardized way to create and manage forms, supporting both editable and read-only modes. This component can be easily customized and integrated into different parts of an application to handle various form-related tasks.
    
    ## Code Structure:
    
    ```
    this.component = XFormComponent;
        this.injector = Injector.create({
          providers: [
            {
              provide: XFormParamProvider,
              useValue: new XFormParam(xFormInput),
            },
          ],
          parent: this.inj,
        });
      }
    ```
    
    - **Component Assignment**: The `this.component` assignment sets the component type to `XFormComponent`, indicating that this is the component to be rendered.
    - **Injector Creation**: An `Injector` instance is created to provide dependencies for the `XFormComponent`.
    - **Providers**:
        - A provider is defined to supply an instance of `XFormParamProvider`.
    - **XFormParamProvider**:
        - An abstract class used as a base for providing form parameters in the component. It holds the `xFormInput` object, which contains configuration and data for form management.
    - **XFormParam**:
        - A concrete class extending `XFormParamProvider`. It provides a specific implementation of the `XFormParamProvider` service, initialized with `xFormInput`. This class is used to pass form configuration to the component.
    - **xFormInput**:
        - An interface defining the structure and properties required for form management, including entity details, form items, and various settings. It is used to configure the form and control its behavior in the component.
    
      
    
    ## Properties of XFormInput :
    
    | Property | Type | Function |
    | --- | --- | --- |
    | mode | 'inline' \| 'popup' | Defines the display mode for a form or component |
    | entityName | string | Specifies the entity the component will interact with. It is used to determine the appropriate backend API endpoints for data fetching. |
    | pageMode | PageMode | This property reflects the current mode of the page, which can be dynamically updated based on various conditions and user interactions. It ensures that the UI correctly adapts to the current state, whether it needs to be in 'read', 'create', or any other mode. |
    | id | string | - - |
    | item | any | Array of data objects representing the rows in the list. Each object in the array is a row, with its structure defined by the columns and properties configured in the component.  |
    | items | ItemEntityDto<string>[] | Represents the data object for the component. In this context, ItemEntityDto<string> is a generic DTO that includes properties and methods for managing the item data. It can be used to pass data into the component and access various item-related functionalities within the component. |
    | parentEntity | string | Specifies the entity name of the parent item. |
    | parentId | string | Holds the identifier of the parent item. |
    | parentPageMode | PageMode | Specifies the mode of the parent page, which can be 'create', 'update', or 'read'. |
    | parentItem | any | Holds the entire parent item object. |
    | save | (xFormResult: XFormResult) => void | - -
     |
    | init | (instance: XFormComponent) => void | - - |
    | close | () => void | FA function used to handle the closing or dismissal of a component, dialog, or form. It typically performs any necessary cleanup or finalization and may trigger events or updates to reflect that the component is no longer visible or active. |
    | columns | Property[] | Defines an array of Property objects that specify additional configurations and customizations for each property of the entity to be displayed as a column. This includes specifying custom templates (cellTemplate), custom names (name), and other configurations like hiding columns (hidden). |
    | schema | EntitySchemaDto | - - |
    | onInit | (instance?: XFormComponent) => void | A callback function that is executed when the component is initialized. It provides access to the component instance, allowing for custom initialization logic |
    | hideSuccessMessage | boolean | Determines whether to hide or display success messages. When set to true, it hides success messages. |
    | onSave | (xFormResult: XFormResult) => void | Defines a callback function to be executed when the form is successfully saved. This function typically processes the result of the form submission and may perform additional actions such as updating the UI or setting component state. |
    | onBeforeSave | (xFormResult: XFormResult) => void | Defines a callback function to be executed before the form is saved. This function is typically used to prepare or validate data before the actual save operation occurs. |
    | saveText | string | Optional text for the save button. |
    | saveIcon | string | Optional icon for the save button. |
    | headerTpl | TemplateRef<any> | A template reference that defines the custom header content for the component. This template can include any HTML or Angular components and is typically used to customize the appearance and functionality of the header section of a list, table, or page. |
    | rightTpl | TemplateRef<any> | A template reference that defines custom content to be displayed on the right side of the component. This template can be used to render specific sections or details, such as a preview pane, additional information, or a custom layout for data presentation. |
    | formBeforeTpl | TemplateRef<any> | Defines the template for content displayed before the main form. Used to provide preliminary instructions or information relevant to the form. |
    | formRightTpl | TemplateRef<any> | Indicates the template for content displayed to the right of the main form. Used for supplementary components or information that complements the form. |
    | contentTpl | TemplateRef<any> | Optional template reference for the content. |
    | beforeFooterBtn | TemplateRef<any> | Template reference for custom content or buttons to be displayed before the main footer area. It allows for conditional controls or information to be presented based on the state of the page, such as showing cancellation options or status-specific buttons before the footer. This enhances user interaction by offering relevant actions in the appropriate context. |
    | afterFooterBtn | TemplateRef<any> | Template reference for custom content or buttons to be displayed after the main footer area. This can include actions like "Submit" that are context-sensitive and appear only when certain conditions are met, such as when the form is not in read-only mode. It provides additional functionality relevant to the user’s current interaction. |
    | saveBtnTpl | TemplateRef<any> | Optional template reference for customizing the appearance and behavior of the save button. |
    | hideSaveStay | boolean | Option to hide the save and stay button.. |
    | hideSpinner | boolean | - - |
    
    ## Output:
    
    In the provided example, the `PortCallTncDetComponent` demonstrates how to utilize the XFormComponent to create a form for editing terms and conditions related to port calls. The component initializes the XFormComponent, sets up the form fields, and binds data to the form. This setup allows users to edit and save terms and conditions efficiently.
    
    ![Untitled (3).png](Documentation%20in%20GitHub%20(2)%20e3669e943a314c4996a129e2dc1e8ff9/Untitled_(3).png)
    
    - In this example, the form allows users to edit and save terms and conditions for a port call.
    - The fields include a title and a body, where users can input relevant information.
    - The form is part of the `PortCallTncDetComponent`.
    - This illustrates how the XFormComponent can be integrated into an application to manage form data dynamically and interactively.
    
- XListComponent
    
    <aside>
    👉 **The XListComponent is utilized in our project to dynamically render and manage lists within various components. It** is typically used in child components to display data in a tabular format.
    
    </aside>
    
    ## Code Structure:
    
    ```jsx
    this.component = XListEditComponent;
    this.injector = Injector.create({
    providers: [
    {
    provide: XListParamProvider,
    useValue: new XListParam(this.xListInput),
    },
    ],
    parent: this.inj,
    });
    ```
    
    - The `this.component` assignment sets the component type to , indicating that this is the component to be rendered.
        
        XListEditComponent
        
    - **Injector Creation**: An `Injector` instance is created to provide dependencies for the
        
        XListEditComponent.
        
    - Providers: A provider is defined to supply an instance of
        
        XListParamProvider.
        
    - XListParamProvider: 
    An abstract class used as a base for providing list parameters in the component. It holds the`xListInput` object, which contains configuration and data for list management.
    - XListParam:
    A concrete class extending`XListParamProvider`. It provides a specific implementation of the `XListParamProvider` service, initialized with `xListInput`. This class is used to pass list configuration to the component.
    - xListInput:  An interface defining the structure and properties required for list management, including entity details, list items, and various settings. It is used to configure the list and control its behavior in the component.
    
    ## Properties of xListInput:
    
    | Property | Type | Function |
    | --- | --- | --- |
    | entityName | string | Specifies the entity the component will interact with. It is used to determine the appropriate backend API endpoints for data fetching. |
    | items | any[] | Array of data objects representing the rows in the list. Each object in the array is a row, with its structure defined by the columns and properties configured in the component.  |
    | parentEntity | string  | Specifies the entity name of the parent item. |
    | parentId | string | Holds the identifier of the parent item. |
    | parentPageMode | PageMode  | Specifies the mode of the parent page, which can be 'create', 'update', or 'read'. |
    | parentItem | any  | Holds the entire parent item object. |
    | parentProp | any  | - - |
    | onInit | (instance: any) => void | A callback function that is executed when the component is initialized. It provides access to the component instance, allowing for custom initialization logic. |
    | init | (instance: any) => void | - - |
    | save | (items: any[]) => void | - - |
    | onListChange | () => void | A callback function that is triggered when there is a change in the list data. It allows for custom logic to be executed in response to modifications in the list, such as updating data, filtering items, or adjusting UI elements based on the new state of the list. |
    | detailsComp | Type<any>  | Specifies a component used for displaying the editable or action-oriented view of an entity. This component allows users to modify, edit, or perform actions related to the entity. |
    | header | TemplateRef<any> | - - |
    | replaceListTpl | TemplateRef<any>  | - - |
    | replaceHeaderTpl | TemplateRef<any>  | - - |
    | listMode | boolean | - - |
    | columns | Property[]  | Defines an array of Property objects that specify additional configurations and customizations for each property of the entity to be displayed as a column. This includes specifying custom templates (cellTemplate), custom names (name), and other configurations like hiding columns (hidden). |
    | disableActiveFilter | boolean  | Determines whether the active filter functionality is disabled. When set to true, the active filter will be disabled. |
    | paginator | boolean | Enables pagination in the UI. When set to true, a paginator is displayed, allowing users to navigate through multiple pages of data. |
    | paginatorright | TemplateRef<any> | Template reference for custom pagination controls placed on the right side of the paginator. This allows for the inclusion of additional buttons or controls, such as "Save" or "Cancel", to be displayed alongside the paginator.  |
    | nextBtnText | string  | Defines the text to be displayed on the "Next" button. This property customizes the button's label. |
    | isDialogEdit | boolean | - - |
    |  |  |  |
    
    ## Output:
    
    In the provided example, you can see the Port Mapping page where the Alerts tab displays a list with editable rows. This section utilizes the `XListEditComponent`.
    
    ![Untitled (4).png](Documentation%20in%20GitHub%20(2)%20e3669e943a314c4996a129e2dc1e8ff9/Untitled_(4).png)
    
    The `XListEditComponent` is designed to facilitate the display and editing of a list of items within a table format. In this context, it allows users to view, modify, and manage port-related alerts efficiently. The key functionalities provided by `XListEditComponent` include:
    
    1. **Editable Rows:** Each row in the list is editable, allowing users to update information directly within the table.
    2. **Dynamic Dropdowns:** The component supports dynamic dropdowns for selecting values, ensuring that users can easily choose from predefined options.
    3. **Read-Only Conditions:** Certain conditions can be applied to make rows or specific cells read-only, preventing unwanted modifications based on the row status.
    4. **Configuration Flexibility:** The component is highly configurable, with properties like columns and data items being set through the `xListInput` object. This allows for a tailored setup based on the specific requirements of the page.
    
    In this particular implementation, the `XListEditComponent` is integrated into the `client-agent-alert.component.ts` file. It manages the display and editing of alerts related to port mapping, providing a user-friendly interface for maintaining this data. The `XListEditComponent` ensures that users can efficiently manage alerts by providing a structured and interactive table layout.
    
- XPgReadComponent
    
    
    <aside>
    👉 
    The `XPgReadComponent` is designed to display detailed information about an entity in a read-only format. It is commonly used when the user needs to view, but not edit, the details of an item. This component integrates with other services and configurations to display data effectively.
    
    </aside>
    
    ## Code Structure:
    
    ```jsx
    this.component = XPgReadComponent;
    this.injector = Injector.create({
    providers: [
    {
    provide: XPgReadParamProvider,
    useValue: new XPgReadParam(xPgReadPageConfig),
    },
    ],
    parent: this.inj,
    });
    
    ```
    
    - The `this.component` assignment sets the component type to `XPgReadComponent`, indicating that this is the component to be rendered.
    - **Injector Creation**: An `Injector` instance is created to provide dependencies for the `XPgReadComponent`
    - Providers:  A provider is defined to supply an instance of `XPgReadParamProvider`.
    - **XPgReadParamProvider**:
        - This is an abstract class used to provide the `XPgReadPageConfig` to the `XPgReadComponent`.
        - It is initialized with the `XPgReadPageConfig` object, which contains configuration details for the read page.
    - **XPgReadParam**:
        - This class wraps the `XPgReadPageConfig` and is used as the value for the `XPgReadParamProvider`.
        - The `XPgReadPageConfig` includes properties like `entityName`, `id`, `item`, `columns`, and various callbacks for initialization, deletion, editing, and closing the component.
    
    ## Properties of  XPgReadPageConfig:
    
    | Property | Type | Function |
    | --- | --- | --- |
    | entityName | String | Specifies the entity the component will interact with. It is used to determine the appropriate backend API endpoints for data fetching. |
    | id | String | - -  |
    | item | ItemEntityDto<string> | Represents the data object for the component. In this context, ItemEntityDto<string> is a generic DTO that includes properties and methods for managing the item data. It can be used to pass data into the component and access various item-related functionalities within the component. |
    | columns | Property[];
     | Defines an array of Property objects that specify additional configurations and customizations for each property of the entity to be displayed as a column. This includes specifying custom templates (cellTemplate), custom names (name), and other configurations like hiding columns (hidden). |
    | onInit | (instance?: any) => void | A callback function that is executed when the component is initialized. It provides access to the component instance, allowing for custom initialization logic. |
    | delete | (event: any) => void | A function that handles the delete action, typically triggered by an event. The implementation may involve showing a confirmation dialog and performing the delete operation. |
    |  edit | () => void | - - |
    | close | () => void | A function used to handle the closing or dismissal of a component, dialog, or form. It typically performs any necessary cleanup or finalization and may trigger events or updates to reflect that the component is no longer visible or active. |
    |  menuMode | 'top' | 'left’ | An  property that specifies the position of the menu items. It can be set to either 'top' or 'left', indicating whether the menu should be displayed at the top or on the left side of the component. |
    | breadcrumbItems |  MenuItem[] | A array of menu items that represent the breadcrumb navigation. Breadcrumb items are typically displayed at the top of the page, showing the user's current location within the application and allowing navigation to previous pages. Each MenuItem can have properties such as label, icon, command, and more, to define its appearance and behavior. |
    | leftBottomTpl | TemplateRef<any> | A template reference that defines custom content to be displayed at the bottom left of the component. This template can be used to render specific sections or details, such as an address or other information. |
    | rightBottomTpl | TemplateRef<any> | A template reference that defines custom content to be displayed at the bottom right of the component. This template can be used to render sections like additional details, lists, or accordion tabs for further information. |
    |  hideTab | boolean | A boolean flag that determines the visibility of tabs within a component. If set to true, the tabs are hidden. If set to false, the tabs are visible, allowing navigation between different sections within the component. This is useful in detail components where different categories of information are displayed under separate tabs. |
    | afterTemplate | TemplateRef<any> | - - |
    | rightTpl | TemplateRef<any> | A template reference that defines custom content to be displayed on the right side of the component. This template can be used to render specific sections or details, such as a preview pane, additional information, or a custom layout for data presentation. |
    | headerTpl | TemplateRef<any> | A template reference that defines the custom header content for the component. This template can include any HTML or Angular components and is typically used to customize the appearance and functionality of the header section of a list, table, or page. |
    | footerTpl | TemplateRef<any> | A template reference that defines the custom footer content for the component. This template can include any HTML or Angular components and is typically used to customize the appearance and functionality of the footer section of a list, table, or page. The footer can include elements such as summary data, action buttons, or any other custom content. |
    
    ## Output:
    
    The `XPgReadComponent` is used to display detailed information about an entity in a read-only format. This component is particularly useful for presenting data that users can view but not modify.
    
    ![Untitled (5).png](Documentation%20in%20GitHub%20(2)%20e3669e943a314c4996a129e2dc1e8ff9/Untitled_(5).png)
    
    - In the example shown the `XPgReadComponent` is used in the agent-read.component .ts   to display comprehensive details about an agent. The page includes multiple sections such as personal information, ports, bank accounts, and contact information.
    - **Agent Details**: On the left, the agent's personal information including name, status, address, country, phone number, email, and sanction check status is displayed.
    - **Tabs and Sections**: The main section includes tabs for Ports, Bank Accounts, and Contact Information. Each tab provides relevant details in a structured format. For example, the Bank Accounts tab lists multiple bank accounts with detailed information about each account.
    - **UI Elements**: The page includes various UI elements like tables, tabs, and informational panels to enhance the readability and usability of the information.
- XListEditComponent
    
    
    👉 The`XListEditComponent` is an Angular component designed to facilitate inline editing of list    items. It allows users to modify individual entries in a tabular format directly within the application.
    
    ## Code Structure:
    
    ```jsx
    this.component = XListEditComponent;
    this.injector = Injector.create({
    providers: [
    {
    provide: XListParamProvider,
    useValue: new XListParam(this.xListInput),
    },
    ],
    parent: this.inj,
    });
    ```
    
    - The `this.component` assignment sets the component type to , indicating that this is the component to be rendered.
        
        XListEditComponent
        
    - **Injector Creation**: An `Injector` instance is created to provide dependencies for the
        
        XListEditComponent.
        
    - Providers: A provider is defined to supply an instance of
        
        XListParamProvider.
        
    - XListParamProvider: 
    An abstract class used as a base for providing list parameters in the component. It holds the`xListInput` object, which contains configuration and data for list management.
    - XListParam:
    A concrete class extending`XListParamProvider`. It provides a specific implementation of the `XListParamProvider` service, initialized with `xListInput`. This class is used to pass list configuration to the component.
    - xListInput:  An interface defining the structure and properties required for list management, including entity details, list items, and various settings. It is used to configure the list and control its behavior in the component.
    
    ## Properties of xListInput:
    
    | Property | Type | Function |
    | --- | --- | --- |
    | entityName | string | Specifies the entity the component will interact with. It is used to determine the appropriate backend API endpoints for data fetching. |
    | items | any[] | Array of data objects representing the rows in the list. Each object in the array is a row, with its structure defined by the columns and properties configured in the component.  |
    | parentEntity | string  | Specifies the entity name of the parent item. |
    | parentId | string | Holds the identifier of the parent item. |
    | parentPageMode | PageMode  | Specifies the mode of the parent page, which can be 'create', 'update', or 'read'. |
    | parentItem | any  | Holds the entire parent item object. |
    | parentProp | any  | - - |
    | onInit | (instance: any) => void | A callback function that is executed when the component is initialized. It provides access to the component instance, allowing for custom initialization logic. |
    | init | (instance: any) => void | - - |
    | save | (items: any[]) => void | - - |
    | onListChange | () => void | A callback function that is triggered when there is a change in the list data. It allows for custom logic to be executed in response to modifications in the list, such as updating data, filtering items, or adjusting UI elements based on the new state of the list. |
    | detailsComp | Type<any>  | Specifies a component used for displaying the editable or action-oriented view of an entity. This component allows users to modify, edit, or perform actions related to the entity. |
    | header | TemplateRef<any> | - - |
    | replaceListTpl | TemplateRef<any>  | - - |
    | replaceHeaderTpl | TemplateRef<any>  | - - |
    | listMode | boolean | - - |
    | columns | Property[]  | Defines an array of Property objects that specify additional configurations and customizations for each property of the entity to be displayed as a column. This includes specifying custom templates (cellTemplate), custom names (name), and other configurations like hiding columns (hidden). |
    | disableActiveFilter | boolean  | Determines whether the active filter functionality is disabled. When set to true, the active filter will be disabled. |
    | paginator | boolean | Enables pagination in the UI. When set to true, a paginator is displayed, allowing users to navigate through multiple pages of data. |
    | paginatorright | TemplateRef<any> | Template reference for custom pagination controls placed on the right side of the paginator. This allows for the inclusion of additional buttons or controls, such as "Save" or "Cancel", to be displayed alongside the paginator.  |
    | nextBtnText | string  | Defines the text to be displayed on the "Next" button. This property customizes the button's label. |
    | isDialogEdit | boolean | - - |
    |  |  |  |
    
    ## Output:
    
    In the provided example, you can see the Port Mapping page where the Alerts tab displays a list with editable rows. This section utilizes the `XListEditComponent`.
    
    ![Untitled (6).png](Documentation%20in%20GitHub%20(2)%20e3669e943a314c4996a129e2dc1e8ff9/Untitled_(6).png)
    
    The `XListEditComponent` is designed to facilitate the display and editing of a list of items within a table format. In this context, it allows users to view, modify, and manage port-related alerts efficiently. The key functionalities provided by `XListEditComponent` include:
    
    1. **Editable Rows:** Each row in the list is editable, allowing users to update information directly within the table.
    2. **Dynamic Dropdowns:** The component supports dynamic dropdowns for selecting values, ensuring that users can easily choose from predefined options.
    3. **Read-Only Conditions:** Certain conditions can be applied to make rows or specific cells read-only, preventing unwanted modifications based on the row status.
    4. **Configuration Flexibility:** The component is highly configurable, with properties like columns and data items being set through the `xListInput` object. This allows for a tailored setup based on the specific requirements of the page.
    
    In this particular implementation, the `XListEditComponent` is integrated into the `client-agent-alert.component.ts` file. It manages the display and editing of alerts related to port mapping, providing a user-friendly interface for maintaining this data. The `XListEditComponent` ensures that users can efficiently manage alerts by providing a structured and interactive table layout.
    

---

## Common:

# 

### 

###
