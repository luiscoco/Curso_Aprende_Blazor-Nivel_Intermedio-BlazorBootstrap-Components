# How to install BlazorBootstrap Components in your Blazor Web Application

**Note:** For more information about this sample visit these URLs:

https://demos.blazorbootstrap.com/

https://docs.blazorbootstrap.com/getting-started/blazor-webapp-server-global-net-8

## 1. Load the Nuget package Blazor.Bootstrap

![image](https://github.com/user-attachments/assets/40e886f5-0367-43ae-aa95-d6271bf73149)

## 2. Modify the App.razor component to include the Radzen references

Add CSS references

```
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
<link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css" rel="stylesheet" />
<link href="_content/Blazor.Bootstrap/blazor.bootstrap.css" rel="stylesheet" />
´``

Add script references

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

Remove default reference

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

## 3. Include in the _Imports.razor the Radzen.Blazor

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

## 5. Create a new Razor Component to validate the Radzen installation

We create a new component doing right click on the **Pages** folder and selecting **Add->Razor Component**:

![image](https://github.com/user-attachments/assets/37933abb-c0e6-4d84-afcc-19d531a4ff94)

We set the new Razor Component name: **RadzenButtons.razor**

```razor
@page "/radzen-buttons"
@inject NotificationService NotificationService


@* https://blazor.radzen.com/button?theme=material3 *@

<RadzenButton Click="@ButtonClicked" Text="Hi"></RadzenButton>

<br />
<br />

<p>@message</p>

<br />
<br />

<RadzenStack Orientation="Orientation.Horizontal" AlignItems="AlignItems.Center" Gap="1rem" Wrap="FlexWrap.Wrap">
    <RadzenButton Click=@(args => OnClick("Primary button")) Text="Primary" ButtonStyle="ButtonStyle.Primary" />
    <RadzenButton Click=@(args => OnClick("Secondary button")) Text="Secondary" ButtonStyle="ButtonStyle.Secondary" />
    <RadzenButton Click=@(args => OnClick("Base button")) Text="Base" ButtonStyle="ButtonStyle.Base" />
    <RadzenButton Click=@(args => OnClick("Info button")) Text="Info" ButtonStyle="ButtonStyle.Info" />
    <RadzenButton Click=@(args => OnClick("Success button ")) Text="Success" ButtonStyle="ButtonStyle.Success" />
    <RadzenButton Click=@(args => OnClick("Warning button ")) Text="Warning" ButtonStyle="ButtonStyle.Warning" />
    <RadzenButton Click=@(args => OnClick("Danger button")) Text="Danger" ButtonStyle="ButtonStyle.Danger" />
</RadzenStack>

@code {
    private string message = "";

    void ButtonClicked()
    {
        message = "Hello World!";
    }
    private void OnClick(string text)
    {
        NotificationService.Notify(new NotificationMessage { Severity = NotificationSeverity.Info, Summary = "Button Clicked", Detail = text });
    }

}
```

## 6. Modify the NavMenu.razor component and add a new NavLink

Add a new NavLink in the NavMenu.razor component to navigate to the new component:

```
<div class="nav-item px-3">
   <NavLink class="nav-link" href="radzen-buttons">
       <span class="bi bi-list-nested-nav-menu" aria-hidden="true"></span> RadzenButtons
   </NavLink>
</div>
```

## 7. Run the application to validate the result

![image](https://github.com/user-attachments/assets/1149cf90-4b85-446a-a16d-4e16a2413a06)
