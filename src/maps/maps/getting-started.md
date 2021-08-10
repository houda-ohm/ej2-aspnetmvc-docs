# Getting Started

You can explore some useful features in the Maps component using the following video.

`youtube:kwE6ikF7QYQ`

## Prerequisites

To get started with the ASP.NET MVC application, make sure you have the following software installed on your computer.

1. .Net Framework 4.5 and above.
2. ASP.NET MVC 4 or ASP.NET MVC 5
3. Visual Studio 2017

## Preparing ASP.NET MVC application

The steps to create an ASP.NET MVC Application are as follows.

**Step 1:** Click Create new project in Visual Studio 2017, and the popup window below will appear. Click the OK button after selecting the **ASP.NET Web Application(.NET Framework)** template. You can also change the name of the project.

![All Text](../images/mvc-template.PNG)

**Step 2:** Following the above steps, the popup window below will appear. Select **MVC** in this window. Now the project will be created successfully.

![All Text](../images/MVC.PNG)

**Step 3:** After you have created your project, use NuGet Package Manager to install the **Syncfusion.EJ2.MVC5** package.

Open the **Manage NuGet packages**.

![Solution Explorer](../images/solution-Explorer.png)

The **Syncfusion.EJ2.MVC5** package should be installed in the application.

![Nuget Demo](../images/mvc-nuget.PNG)

This package will be included in the project once the installation is complete. You can refer to it from the Project Assembly Reference.

> We need to install **NewtonSoft.JSON** as dependency since it **Syncfusion.EJ2.MVC5** dependent on NewtonSoft.JSON package.

**Step 4:** In Web.Config file, include the Syncfusion.EJ2 namespace.

```javascript

<namespaces>
    <add namespace="Syncfusion.EJ2"/>
</namespaces>

```

```javascript

<system.web>
    <compilation>
      <assemblies>
        <add assembly="Syncfusion.EJ2, Version=15.3400.0.27, Culture=neutral, PublicKeyToken=31BF3856AD364E35"  />
      </assemblies>
    </compilation>
  </system.web>

```

**Step 4:** Add client-side resources through [CDN](http://ej2.syncfusion.com/documentation/base/deployment.html?lang=typescript#cdn) or local [package](https://www.npmjs.com/package/@syncfusion/ej2) in the layout page **_Layout.cshtml.** which is located in the Views/Shared folder.

```cs
@* Syncfusion Essential JS 2 Scripts *@
<script src="https://cdn.syncfusion.com/ej2/dist/ej2.min.js"></script>

```

**Step 5:** Script Manager and namespace should be added to the **_Layout.cshtml** layout page, which is located in the Views/Shared folder.

```cs

@using Syncfusion.EJ2;

    . . .
    . . .
<body>
    . . .
    . . .
    @Html.EJS().ScriptManager()
</body>

```

**Step 6:** To initialize the Maps, add the following code to your **Index.cshtml** view page, which is located in the Views/Home folder.

```cs

<h2> Essential JS 2 for ASP.NET MVC Maps </h2>

 @Html.EJS().Maps("container").Layers(layer => { layer.ShapeData(ViewBag.shapeData).Add(); }).Render();

```
