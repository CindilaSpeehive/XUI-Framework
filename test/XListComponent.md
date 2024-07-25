<html>
<body>
<!--StartFragment--><p>The <code>XListComponent</code> is used to display and manage a list of items in a structured manner. It allows for operations such as viewing, creating, and manipulating the list items.</p>
<h2>Code Structure:</h2>
<pre><code class="language-tsx">this.component = XListComponent;
    this.injector = Injector.create({
      providers: [
        {
          provide: XListParamProvider,
          useValue: new XListParam(xListInput),
        },
      ],
      parent: this.inj,
    });
</code></pre>
<ul>
<li><strong>Component Assignment</strong>:
<ul>
<li><code>this.component = XListComponent;</code> sets the component type to <code>XListComponent</code>, indicating that this is the component to be rendered.</li>
</ul>
</li>
<li><strong>Injector Creation</strong>:
<ul>
<li>An <code>Injector</code> instance is created to provide dependencies for the <code>XListComponent</code>.</li>
</ul>
</li>
<li><strong>Providers</strong>:
<ul>
<li>A provider is defined to supply an instance of <code>XListParamProvider</code>.</li>
</ul>
</li>
<li><strong>XListParamProvider</strong>:
<ul>
<li>An abstract class used as a base for providing list parameters in the component. It holds the <code>xListInput</code> object, which contains configuration and data for list management.</li>
</ul>
</li>
<li><strong>XListParam</strong>:
<ul>
<li>A concrete class extending <code>XListParamProvider</code>. It provides a specific implementation of the <code>XListParamProvider</code> service, initialized with <code>xListInput</code>. This class is used to pass list configuration to the component.</li>
</ul>
</li>
<li><strong>xListInput</strong>:
<ul>
<li>An interface defining the structure and properties required for list management, including entity details, list items, and various settings. It is used to configure the list and control its behavior in the component.</li>
</ul>
</li>
</ul>
<h2>Properties of xListInput:</h2>

Property | Type | Function
-- | -- | --
entityName | string | Specifies the entity the component will interact with. It is used to determine the appropriate backend API endpoints for data fetching.
items | any[] | Array of data objects representing the rows in the list. Each object in the array is a row, with its structure defined by the columns and properties configured in the component.
parentEntity | string | Specifies the entity name of the parent item.
parentId | string | Holds the identifier of the parent item.
parentPageMode | PageMode | Specifies the mode of the parent page, which can be 'create', 'update', or 'read'.
parentItem | any | Holds the entire parent item object.
parentProp | any | - -
onInit | (instance: any) => void | A callback function that is executed when the component is initialized. It provides access to the component instance, allowing for custom initialization logic.
init | (instance: any) => void | - -
save | (items: any[]) => void | - -
onListChange | () => void | A callback function that is triggered when there is a change in the list data. It allows for custom logic to be executed in response to modifications in the list, such as updating data, filtering items, or adjusting UI elements based on the new state of the list.
detailsComp | Type<any> | Specifies a component used for displaying the editable or action-oriented view of an entity. This component allows users to modify, edit, or perform actions related to the entity.
header | TemplateRef<any> | - -
replaceListTpl | TemplateRef<any> | - -
replaceHeaderTpl | TemplateRef<any> | - -
listMode | boolean | - -
columns | Property[] | Defines an array of Property objects that specify additional configurations and customizations for each property of the entity to be displayed as a column. This includes specifying custom templates (cellTemplate), custom names (name), and other configurations like hiding columns (hidden).
disableActiveFilter | boolean | Determines whether the active filter functionality is disabled. When set to true, the active filter will be disabled.
paginator | boolean | Enables pagination in the UI. When set to true, a paginator is displayed, allowing users to navigate through multiple pages of data.
paginatorright | TemplateRef<any> | Template reference for custom pagination controls placed on the right side of the paginator. This allows for the inclusion of additional buttons or controls, such as "Save" or "Cancel", to be displayed alongside the paginator.
nextBtnText | string | Defines the text to be displayed on the "Next" button. This property customizes the button's label.
isDialogEdit | boolean | - -
  |   |  


<h2>Output:</h2>
<p>The <code>XListComponent</code> is a crucial component designed to facilitate the display and management of a list of items within a table format. In the context of the Agent Mapping page, it allows users to view and manage agent-related data efficiently.</p>
<p><img src="https://prod-files-secure.s3.us-west-2.amazonaws.com/974f9e60-2d10-4518-be8e-2d119cfceb57/b5c2de62-ca05-4a36-b168-ea15e455be35/Untitled.png" alt="Untitled"></p>
<ol>
<li><strong>Data Display:</strong> The component organizes and displays agent mapping records, such as agent names, countries, and ports, in a structured table, enhancing data accessibility and readability.</li>
<li><strong>Actions:</strong> Users can perform actions like editing and viewing details for each agent directly within the table, improving interactivity and usability.</li>
<li><strong>Filtering and Sorting:</strong> The component supports filtering and sorting of records based on various columns, enabling users to easily navigate and find specific data.</li>
<li><strong>Pagination:</strong> The component includes pagination controls, allowing users to efficiently browse through large sets of records.</li>
</ol>
<p>In this particular implementation, the <code>XListComponent</code> is integrated into the parent component managing the Agent Mapping page. It provides a user-friendly interface for maintaining agent-related data, ensuring that users can efficiently view, edit, and manage this information.</p>
<!-- notionvc: 8798ad1c-d348-4b04-b37c-d53ff350dd86 --><!--EndFragment-->
</body>
</html>
