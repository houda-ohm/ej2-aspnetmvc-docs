---
title: "Scheduler Header customization"
component: "Scheduler"
description: "This section explains how to customize the header bar of Scheduler and to add custom items into it."
---

# Header customization

The header part of Scheduler can be customized easily with the built-in options available.

## Show or Hide header bar

By default, the header bar holds the date and view navigation options, through which the user can switch between the dates and various views. This header bar can be hidden from the UI by setting `false` to the `ShowHeaderBar` property. It's default value is `true`.

{% aspTab template="schedule/header-bar/show-hide", sourceFiles="data.cs"  %}

{% endaspTab %}

## Customizing header bar

Apart from the default date navigation and view options available on the header bar, you can add custom items into the Scheduler header bar by making use of the `ActionBegin` event. Here, an employee image is added to the header bar, clicking on which will open the popup showing that person's short profile information.

{% aspTab template="schedule/header-bar/custom-header-bar", sourceFiles="data.cs"  %}

{% endaspTab %}

## Date header customization

The Scheduler UI that displays the date text on all views are considered as the date header cells. You can customize the date header cells of Scheduler either using `DateHeaderTemplate` or `RenderCell` event.

### Using date header template

The `DateHeaderTemplate` option is used to customize the date header cells of day, week and work-week views.

{% aspTab template="schedule/header-bar/custom-date-header", sourceFiles="data.cs"  %}

{% endaspTab %}

### Using renderCell event

In month view, the date header template is not applicable and therefore the same customization can be added beside the date text in month cells by making use of the `RenderCell` event.

{% aspTab template="schedule/header-bar/render-cell", sourceFiles="data.cs"  %}

{% endaspTab %}