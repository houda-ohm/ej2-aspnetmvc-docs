---
title: "Data binding"
component: "TreeGrid"
description: "Learn how to bind local and remote data in the Essential JS 2 TreeGrid control."
---

# Data binding

The TreeGrid uses **DataManager**, which supports both RESTful JSON data services binding and local JavaScript object array binding. The [`DataSource`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.TreeGrid.TreeGrid~DataSource.html) property can be assigned either with the instance of **DataManager** or JavaScript object array collection.

It supports two kinds of data binding method:
* Local data
* Remote data

## Local Data

In Local Data binding, data source for rendering the TreeGrid control is retrieved from the same application locally.

Two types of Data binding are possible with the TreeGrid control.

* Hierarchical Datasource binding
* Self-Referential Data binding (Flat Data)

To bind local data to the treegrid, you can assign a JavaScript object array to the [`DataSource`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.TreeGrid.TreeGrid~DataSource.html) property. The local data source can also be provided as an instance of the **DataManager**.

> By default, **DataManager** uses **JsonAdaptor** for local data-binding.

### Hierarchy data source binding

The [`ChildMapping`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.TreeGrid.TreeGrid~ChildMapping.html) property is used to map the child records in hierarchy data source.

The following code example shows you how to bind the hierarchical local data into the TreeGrid control.

{% aspTab template="tree-grid/data-binding-mvc/local-data", sourceFiles="local-data.cs" %}

{% endaspTab %}

### Self-Referential Data binding (Flat Data)

TreeGrid is rendered from Self-Referential data structures by providing two fields, ID field and parent ID field.

* **ID Field**: This field contains unique values used to identify nodes. Its name is assigned to the [`IdMapping`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.TreeGrid.TreeGridBuilder~IdMapping.html) property.

* **Parent ID Field**: This field contains values that indicate parent nodes. Its name is assigned to the [`ParentIdMapping`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.TreeGrid.TreeGridBuilder~ParentIdMapping.html) property.

{% aspTab template="tree-grid/data-binding-mvc/self-reference", sourceFiles="self-reference.cs" %}

{% endaspTab %}

## Remote data

To bind remote data to TreeGrid component, assign service data as an instance of **DataManager** to the [`DataSource`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.TreeGrid.TreeGridBuilder~DataSource.html) property. To interact with remote data source,  provide the endpoint **url** and define the [`HasChildMapping`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.TreeGrid.TreeGridBuilder~HasChildMapping.html) property of treegrid.

The [`HasChildMapping`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.TreeGrid.TreeGridBuilder~HasChildMapping.html) property maps the field name in data source, that denotes whether current record holds any child records. This is useful internally to show expand icon while binding child data on demand.

The TreeGrid provides **Load on Demand** support for rendering remote data. The Load on demand is considered in TreeGrid for the following actions.

* Expanding root nodes.
* Navigating pages, with paging enabled in TreeGrid.

When load on demand is enabled, all the root nodes are rendered in collapsed state at initial load.

When load on demand support is enabled in TreeGrid with paging, the current or active page’s root node alone will be rendered in collapsed state. On expanding the root node, the child nodes will be loaded from the remote server.

When a root node is expanded, its child nodes are rendered and are cached locally, such that on consecutive expand/collapse actions on root node, the child nodes are loaded from the cache instead from the remote server.

Similarly, if the user navigates to a new page, the root nodes of that specific page, will be rendered with request to the remote server.

{% aspTab template="tree-grid/data-binding-mvc/remote-data", sourceFiles="remote-data.cs" %}

{% endaspTab %}

> By default, **DataManager** uses **ODataAdaptor** for remote data-binding.
> Based on the RESTful web services, set the corresponding adaptor to DataManager. Refer [`here`](https://ej2.syncfusion.com/documentation/data/adaptors/?no-cache=1) for more details.
> Filtering and searching server-side data operations are not supported in load on demand

### Offline Mode

On remote data binding, all treegrid actions such as paging, loading child on-demand, will be processed on server-side. To avoid postback, set the treegrid to load all data on initialization and make the actions process in client-side. To enable this behavior, use the **offline** property of **DataManager**.

{% aspTab template="tree-grid/data-binding-mvc/offline", sourceFiles="offline.cs" %}

{% endaspTab %}

### Custom Adaptor

You can create your own adaptor by extending the built-in adaptors. The following demonstrates custom adaptor approach and how to add a serial number for the records by overriding the built-in response processing using the **processResponse** method of the **ODataAdaptor**.

{% aspTab template="tree-grid/data-binding-mvc/customadaptor", sourceFiles="customadaptor.cs" %}

{% endaspTab %}

### Sending additional parameters to the server

To add a custom parameter to the data request, use the **addParams** method of [`Query`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.TreeGrid.TreeGrid~Query.html) property. Assign the Query object with additional parameters to the treegrid [`Query`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.TreeGrid.TreeGrid~Query.html) property.

{% aspTab template="tree-grid/data-binding-mvc/param", sourceFiles="params.cs" %}

{% endaspTab %}

### Handling HTTP error

During server interaction from the treegrid, some server-side exceptions may occur, and you can acquire those error messages or exception details
in client-side using the [`ActionFailure`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.TreeGrid.TreeGrid~ActionFailure.html) event.

The argument passed to the [`ActionFailure`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.TreeGrid.TreeGrid~ActionFailure.html) event contains the error details returned from the server.

{% aspTab template="tree-grid/data-binding-mvc/http-error", sourceFiles="http-error.cs" %}

{% endaspTab %}

> The [`ActionFailure`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.TreeGrid.TreeGrid~ActionFailure.html) event will be triggered not only for the server errors, but also when there is an exception while processing the treegrid actions.

## Binding with ajax

You can use TreeGrid [`DataSource`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.TreeGrid.TreeGrid~DataSource.html) property to bind the data source to TreeGrid from external ajax request. In the below code we have fetched the data source from the server with the help of ajax request and provided that to [`DataSource`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.TreeGrid.TreeGrid~DataSource.html) property by using **onSuccess** event of the ajax.

{% aspTab template="tree-grid/data-binding-mvc/ajaxbind", sourceFiles="ajaxbind.cs" %}

{% endaspTab %}

> If you bind the dataSource from this way, then it acts like a local dataSource. So you cannot perform any server side crud actions.