---
title: Adaptive Rendering
page_title: Adaptive Rendering | Telerik UI for ASP.NET Core Scheduler HtmlHelper
description: "Get started with the Scheduler HtmlHelper for ASP.NET Core and learn how to configure adaptive rendering."
slug: htmlhelpers_scheduler_adaptiverendering_aspnetcore
position: 2
---

### Adaptive Rendering Mode

Kendo Scheduler supports adaptive enhancements like changes in styling and behavior in order to remain consistent with the specific user device experience. For instance, when editing on a mobile device, the edit container will slide in a new screen for the user, which is a departure from the more desktop-like popup behaviors.

To enable the adaptive rendering feature, set the [`Mobile`](https://docs.telerik.com/aspnet-core/api/Kendo.Mvc.UI.Fluent/SchedulerBuilder#mobile) property to `MobileMode.Auto`,  `MobileMode.Phone` or `"MobileMode.Tablet"`:

* If set to `MobileMode.Auto`, the widget will use adaptive rendering when viewed on a mobile browser.
* If set to `MobileMode.Phone"` or `MobileMode.Tablet`, the widget will be forced to use adaptive rendering regardless of the browser type.

The example below demonstrates how to configure the adaptive rendering mode of the Scheduler.

###### Example

```Razor
@(Html.Kendo().Scheduler<KendoSchedulerAjaxEditing.Models.TaskViewModel>()
    .Name("scheduler")
    .Mobile(MobileMode.Auto)
    .Date(new DateTime(2013, 6, 13))
    .StartTime(new DateTime(2013, 6, 13, 7, 00, 00))
    .Height(600)
    .Views(views =>
    {
        views.DayView();
        views.WeekView(weekView => weekView.Selected(true));
        views.MonthView();
        views.AgendaView();
    })
    .Timezone("Etc/UTC")
    .DataSource(d => d
        .Model(m => {
            m.Id(f => f.TaskID);
            m.Field(f => f.OwnerID).DefaultValue(1);
            m.RecurrenceId(f => f.RecurrenceID);
        })
        .Read("Tasks_Read", "Home")
        .Create("Tasks_Create", "Home")
        .Destroy("Tasks_Destroy", "Home")
        .Update("Tasks_Update", "Home")
    )
)
```

## See Also

* [Overview of the Scheduler HtmlHelper]({% slug htmlhelpers_scheduler_aspnetcore %})
* [Adaptive Rendering of the Scheduler (Demo)](https://demos.telerik.com/aspnet-core/scheduler/adaptiverendering)
* [Telerik UI for ASP.NET MVC Troubleshooting]({% slug knownissues_aspnetmvc6_aspnetmvc %})
