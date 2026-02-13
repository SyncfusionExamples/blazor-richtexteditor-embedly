# Blazor Rich Text Editor with Embedly Integration

[![.NET Version](https://img.shields.io/badge/.NET-10.0-512BD4?logo=dotnet)](https://dotnet.microsoft.com/)
[![Syncfusion](https://img.shields.io/badge/Syncfusion-Blazor-orange)](https://www.syncfusion.com/blazor-components)
[![Embedly](https://img.shields.io/badge/Embedly-Platform-blue)](https://embed.ly/)

## Overview

This project demonstrates a professional integration of **Syncfusion Blazor Rich Text Editor** with **Embedly Platform** for building modern content management applications. The sample showcases automatic transformation of plain text links into rich, interactive preview cards with titles, descriptions, images, and thumbnails.

### Key Components

- **Syncfusion Blazor Rich Text Editor**: Enterprise-grade WYSIWYG editor with comprehensive formatting capabilities
- **Embedly Platform**: Intelligent link embedding service that auto-generates rich preview cards

## Features

- **Rich Text Editing**: Full-featured WYSIWYG editor for content creation
- **Automatic Link Embedding**: Plain text URLs automatically transform into rich preview cards
- **Rich Preview Cards**: Display titles, descriptions, images, and metadata

## Getting Started

### Prerequisites

Ensure you have the following installed on your development machine:

- **.NET 10.0 SDK** or later ([Download](https://dotnet.microsoft.com/download))
- **Visual Studio 2022 (v17.12+)** or **Visual Studio Code** with C# extension
- **Git** for version control ([Download](https://git-scm.com/))
- A modern web browser (Chrome, Edge, Firefox, or Safari)
- **Embedly Account** (Optional for enhanced features) ([Sign Up](https://dash.embed.ly/))

## Installation

### Step 1: Clone the Repository

```bash
git clone https://github.com/SyncfusionExamples/blazor-richtexteditor-embedly.git
cd blazor-richtexteditor-embedly
```

### Step 2: Navigate to Project Directory

```bash
cd Embedly_Integration
```

### Step 3: Restore NuGet Packages

```bash
dotnet restore
```

This will download all required dependencies including:
- Syncfusion.Blazor.RichTextEditor
- Syncfusion.Blazor.Themes

### Step 4: Build the Project

```bash
dotnet build
```

### Step 5: Run the Application

```bash
dotnet run
```

The application will start and display the URL in the terminal (typically `https://localhost:5001`).

Open your browser and navigate to the displayed URL, then click on the **Embedly** link to see the application in action.

## Usage

### Accessing the Embedly Integration

1. **Launch the application** and navigate to your browser
2. Click on **Embedly** in the navigation menu or navigate directly to `/`
3. **Insert a URL** using the **CreateLink** toolbar button
4. **Observe automatic transformation**: The link automatically converts to a rich preview card
5. **View preview details**: See title, description, image, and metadata

### Sample Workflow

1. Click the **link icon** in the toolbar
2. Enter a URL in the dialog (e.g., `https://www.youtube.com/watch?v=dQw4w9WgXcQ`)
3. Click **OK** to insert the link
4. Watch as Embedly automatically generates a rich preview card with:
   - Website/video title
   - Description or video details
   - Thumbnail image
   - Clickable preview card

## Project Structure

```
blazor-richtexteditor-embedly/
├── Embedly_Integration/
│   ├── Components/
│   │   ├── Layout/
│   │   │   ├── MainLayout.razor              # Main application layout
│   │   │   └── NavMenu.razor                 # Navigation menu
│   │   ├── Pages/
│   │   │   ├── Embedly.razor                 # Main Embedly integration page
│   │   │   ├── Home.razor                    # Home page
│   │   │   ├── Counter.razor                 # Counter component example
│   │   │   ├── Weather.razor                 # Weather component example
│   │   │   └── Error.razor                   # Error handling page
│   │   ├── _Imports.razor                    # Global using statements
│   │   ├── App.razor                         # Root application component
│   │   └── Routes.razor                      # Routing configuration
│   ├── wwwroot/
│   │   ├── scripts/
│   │   │   └── embedly-interop.js            # Embedly JavaScript interop
│   │   ├── bootstrap/                        # Bootstrap CSS files
│   │   └── app.css                           # Custom styles
│   ├── Program.cs                            # Application entry point
│   ├── appsettings.json                      # Application configuration
│   └── Embedly_Integration.csproj            # Project file
├── README.md                                 # This file
```

## Configuration

### Embedly Integration

The Embedly platform is configured through the Embedly CDN script loaded in `App.razor`:

```html
<script src="https://cdn.embedly.com/widgets/platform.js" charset="UTF-8"></script>
```

### JavaScript Interop

The integration uses JavaScript interop in `wwwroot/scripts/embedly-interop.js`:

```javascript
window.embedlyInterop = {
    wrapLinkInEmbedlyCard: function() {
        // Wraps plain links in blockquote elements
        // Calls Embedly library to process and render preview cards
    }
};

function initializeEmbedly() {
    // Initializes Embedly processing on page load
}
```

### Syncfusion License

For production use, you need a valid Syncfusion license.

Register your license in `Program.cs`:

```csharp
Syncfusion.Licensing.SyncfusionLicenseProvider.RegisterLicense("YOUR_LICENSE_KEY");
```

Visit [Syncfusion Licensing](https://www.syncfusion.com/sales/pricing) for more information.

## Add Stylesheet and Script Resources

The required stylesheets and scripts are configured in the `App.razor` file:

```html
<!-- Syncfusion Blazor Theme -->
<link href="_content/Syncfusion.Blazor.Themes/bootstrap5.css" rel="stylesheet" />

<!-- Syncfusion Blazor Core Script -->
<script src="_content/Syncfusion.Blazor.Core/scripts/syncfusion-blazor.min.js"></script>

<!-- Embedly Platform Script (provides embed functionality) -->
<script src="https://cdn.embedly.com/widgets/platform.js" charset="UTF-8"></script>

<!-- Custom Embedly Interop Script -->
<script src="/scripts/embedly-interop.js"></script>

```

## Rich Text Editor Configuration

The editor is configured with a minimal toolbar containing only the CreateLink button:

```csharp
private List<ToolbarItemModel> ToolbarItems = new()
{
    new ToolbarItemModel { Command = ToolbarCommand.CreateLink }
};
```

## Event Handlers

**OnActionComplete**
```csharp
private async Task OnActionComplete(ActionCompleteEventArgs args)
{
    if (args.RequestType == "Links")
    {
        // Handle link insertion
        await JS.InvokeVoidAsync("embedlyInterop.wrapLinkInEmbedlyCard");
    }
}
```

**OnAfterRenderAsync**
```csharp
protected override async Task OnAfterRenderAsync(bool firstRender)
{
    if (firstRender)
    {
        // Initialize Embedly on first render
        await JS.InvokeVoidAsync("initializeEmbedly");
    }
}
```

## Documentation

- [Syncfusion Blazor Rich Text Editor](https://blazor.syncfusion.com/documentation/rich-text-editor/getting-started)
- [Embedly Official Documentation](https://embed.ly/docs)
- [Embedly Supported Providers](https://embed.ly/providers)
- [Blazor Documentation](https://learn.microsoft.com/aspnet/core/blazor/)
- [.NET 10 Release Notes](https://dotnet.microsoft.com/en-us/download)

**Note**: This is a demonstration project. For production use, ensure you have valid licenses for Syncfusion components and implement appropriate security measures.
