# How to install BlazorBootstrap Components in your Blazor Web Application

**Note:** For more information about this sample visit these URLs:

https://demos.blazorbootstrap.com/

https://docs.blazorbootstrap.com/getting-started/blazor-webapp-server-global-net-8

## 1. Load the Nuget package Blazor.Bootstrap

![image](https://github.com/user-attachments/assets/40e886f5-0367-43ae-aa95-d6271bf73149)

## 2. Modify the App.razor component

Add CSS references:

```
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
<link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css" rel="stylesheet" />
<link href="_content/Blazor.Bootstrap/blazor.bootstrap.css" rel="stylesheet" />
```

Add script references:

```
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-C6RzsynM9kWDrMNeT87bh95OGNyZPhcTNXj1NW7RuBCsyN/o0jlpcV8Qyq46cDfL" crossorigin="anonymous"></script>
<!-- Add chart.js reference if chart components are used in your application. -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.0.1/chart.umd.js" integrity="sha512-gQhCDsnnnUfaRzD8k1L5llCCV6O9HN09zClIzzeJ8OJ9MpGmIlCxm+pdCkqTwqJ4JcjbojFr79rl2F1mzcoLMQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<!-- Add chartjs-plugin-datalabels.min.js reference if chart components with data label feature is used in your application. -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/chartjs-plugin-datalabels/2.2.0/chartjs-plugin-datalabels.min.js" integrity="sha512-JPcRR8yFa8mmCsfrw4TNte1ZvF1e3+1SdGMslZvmrzDYxS69J7J49vkFL8u6u8PlPJK+H3voElBtUCzaXj+6ig==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<!-- Add sortable.js reference if SortableList component is used in your application. -->
<script src="https://cdn.jsdelivr.net/npm/sortablejs@latest/Sortable.min.js"></script>
<script src="_content/Blazor.Bootstrap/blazor.bootstrap.js"></script>
´``

Remove default reference:

```
<link rel="stylesheet" href="bootstrap/bootstrap.min.css" />
```

This is the **App.razor** component including Radzen Components

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <base href="/" />
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css" rel="stylesheet" />
    <link href="_content/Blazor.Bootstrap/blazor.bootstrap.css" rel="stylesheet" />
    <link rel="stylesheet" href="app.css" />
    <link rel="stylesheet" href="BlazorApp3.styles.css" />
    <link rel="icon" type="image/png" href="favicon.png" />
    <HeadOutlet @rendermode="@InteractiveServer" />
</head>

<body>
    <Routes @rendermode="@InteractiveServer" />
    <script src="_framework/blazor.web.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-C6RzsynM9kWDrMNeT87bh95OGNyZPhcTNXj1NW7RuBCsyN/o0jlpcV8Qyq46cDfL" crossorigin="anonymous"></script>
    <!-- Add chart.js reference if chart components are used in your application. -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.0.1/chart.umd.js" integrity="sha512-gQhCDsnnnUfaRzD8k1L5llCCV6O9HN09zClIzzeJ8OJ9MpGmIlCxm+pdCkqTwqJ4JcjbojFr79rl2F1mzcoLMQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
    <!-- Add chartjs-plugin-datalabels.min.js reference if chart components with data label feature is used in your application. -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/chartjs-plugin-datalabels/2.2.0/chartjs-plugin-datalabels.min.js" integrity="sha512-JPcRR8yFa8mmCsfrw4TNte1ZvF1e3+1SdGMslZvmrzDYxS69J7J49vkFL8u6u8PlPJK+H3voElBtUCzaXj+6ig==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
    <!-- Add sortable.js reference if SortableList component is used in your application. -->
    <script src="https://cdn.jsdelivr.net/npm/sortablejs@latest/Sortable.min.js"></script>
    <script src="_content/Blazor.Bootstrap/blazor.bootstrap.js"></script>
</body>

</html>
```

## 3. Include in the _Imports.razor

Add this line in the **_Imports.razor**:

```
@using BlazorBootstrap;
```

This is the _Imports.razor whole code

```razor
@using System.Net.Http
@using System.Net.Http.Json
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using static Microsoft.AspNetCore.Components.Web.RenderMode
@using Microsoft.AspNetCore.Components.Web.Virtualization
@using Microsoft.JSInterop
@using BlazorApp3
@using BlazorApp3.Components
@using BlazorBootstrap;
```

## 4. Modify the middleware(program.cs)

Include the following line in the **program.cs**:

```
builder.Services.AddBlazorBootstrap();
```

This is the whole **program.cs** file:

```csharp
using BlazorApp3.Components;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddBlazorBootstrap();

// Add services to the container.
builder.Services.AddRazorComponents()
    .AddInteractiveServerComponents();

var app = builder.Build();

// Configure the HTTP request pipeline.
if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error", createScopeForErrors: true);
    // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
    app.UseHsts();
}

app.UseHttpsRedirection();

app.UseStaticFiles();
app.UseAntiforgery();

app.MapRazorComponents<App>()
    .AddInteractiveServerRenderMode();

app.Run();
```

## 5. Modify the MainLayout.razor 

This is the new code:

```razor
@inherits LayoutComponentBase

<div class="bb-page">

    <Sidebar @ref="sidebar"
             IconName="IconName.BootstrapFill"
             Title="Blazor Bootstrap"
             DataProvider="SidebarDataProvider" />

    <main>
        <div class="bb-top-row px-4 d-flex justify-content-end">
            <a href="https://docs.microsoft.com/aspnet/" target="_blank">About</a>
        </div>

        <article class="content px-4">
            <div class="py-2">
                @Body
            </div>
        </article>
    </main>

</div>

@code {
    private Sidebar sidebar = default!;
    private IEnumerable<NavItem> navItems = default!;

    private async Task<SidebarDataProviderResult> SidebarDataProvider(SidebarDataProviderRequest request)
    {
        if (navItems is null)
            navItems = GetNavItems();

        return await Task.FromResult(request.ApplyTo(navItems));
    }

    private IEnumerable<NavItem> GetNavItems()
    {
        navItems = new List<NavItem>
        {
            new NavItem { Id = "1", Href = "/", IconName = IconName.HouseDoorFill, Text = "Home", Match=NavLinkMatch.All},
            new NavItem { Id = "2", Href = "/counter", IconName = IconName.PlusSquareFill, Text = "Counter"},
            new NavItem { Id = "3", Href = "/weather", IconName = IconName.Table, Text = "Fetch Data"},
            new NavItem { Id = "4", Href = "/accordion", IconName = IconName.Table, Text = "Accordion"},
        };

        return navItems;
    }
}
```

## 6. Comment all code in the MainLayout.razor.css

![image](https://github.com/user-attachments/assets/a6ec764f-57f0-4fc9-a532-101d04c84f92)

## 7. Create a new Razor Component to validate the Radzen installation

We create a new component doing right click on the **Pages** folder and selecting **Add->Razor Component**:

![image](https://github.com/user-attachments/assets/37933abb-c0e6-4d84-afcc-19d531a4ff94)

We set the new Razor Component name: **AccordionComponent.razor**

```razor
@page "/accordion"

<h3>Accordion</h3>

<Accordion>
    <AccordionItem>
        <TitleTemplate>
            <Icon Name="IconName.HouseFill" Class="me-1" /> Accordion Item #1
        </TitleTemplate>
        <Content>
            <b>This is the first item's accordion body.</b> It is shown by default, until the collapse plugin adds the appropriate classes that we use to style each element. These classes control the overall appearance, as well as the showing and hiding via CSS transitions. You can modify any of this with custom CSS or overriding our default variables. It's also worth noting that just about any HTML can go within the .accordion-body, though the transition does limit overflow.
        </Content>
    </AccordionItem>
    <AccordionItem>
        <TitleTemplate>
            <Icon Name="IconName.PersonFill" Class="me-1" /> Accordion Item #2
        </TitleTemplate>
        <Content>
            <b>This is the second item's accordion body.</b> It is hidden by default, until the collapse plugin adds the appropriate classes that we use to style each element. These classes control the overall appearance, as well as the showing and hiding via CSS transitions. You can modify any of this with custom CSS or overriding our default variables. It's also worth noting that just about any HTML can go within the .accordion-body, though the transition does limit overflow.
        </Content>
    </AccordionItem>
    <AccordionItem>
        <TitleTemplate>
            <Icon Name="IconName.PhoneFill" Class="me-1" /> Accordion Item #3
        </TitleTemplate>
        <Content>
            <b>This is the third item's accordion body.</b> It is hidden by default, until the collapse plugin adds the appropriate classes that we use to style each element. These classes control the overall appearance, as well as the showing and hiding via CSS transitions. You can modify any of this with custom CSS or overriding our default variables. It's also worth noting that just about any HTML can go within the .accordion-body, though the transition does limit overflow.
        </Content>
    </AccordionItem>
</Accordion>


@code {

}
```

## 8. Run the application to validate the result

![image](https://github.com/user-attachments/assets/18cf09ec-210a-4e0d-9bf9-896e8a8e62b6)

