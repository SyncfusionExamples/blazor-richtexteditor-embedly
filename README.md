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
- **Multi-Content Support**: Works with articles, videos, images, documents, and embeddable web content
- **One-Click Linking**: Simple toolbar button to insert URLs
- **Real-time Processing**: Links are processed immediately upon insertion
- **Responsive Design**: Preview cards adapt to different screen sizes

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

```powershell
git clone https://github.com/SyncfusionExamples/blazor-richtexteditor-embedly.git; cd blazor-richtexteditor-embedly
```

### Step 2: Navigate to Project Directory

```powershell
cd Embedly_Integration
```

### Step 3: Restore NuGet Packages

```powershell
dotnet restore
```

This will download all required dependencies including:
- Syncfusion.Blazor.RichTextEditor
- Syncfusion.Blazor.Themes

### Step 4: Build the Project

```powershell
dotnet build
```

### Step 5: Run the Application

```powershell
dotnet run
```

The application will start and display the URL in the terminal (typically `https://localhost:5001`).

Open your browser and navigate to the displayed URL, then click on the "Embedly" link to see the application in action.

## Usage

### Accessing the Embedly Integration

1. **Launch the application** and navigate to your browser
2. Click on **"Embedly"** in the navigation menu or navigate directly to `/embedly`
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

### Example URLs to Try

```
https://www.youtube.com/watch?v=dQw4w9WgXcQ     # YouTube Video
https://www.github.com                           # GitHub (Webpage)
https://www.medium.com/@user/article             # Article
https://www.wikipedia.org/wiki/Web_development   # Wiki Article
https://www.amazon.com/product                   # Product Page
```

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

**Configuration Details**:
- CDN endpoint: `https://cdn.embedly.com/widgets/platform.js`
- Charset: UTF-8 (required for proper encoding)
- Loaded in `<body>` section for DOM availability

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

### Embedly API Key (Optional)

For production use with custom branding or enhanced features:

1. Create an Embedly account at [https://dash.embed.ly/](https://dash.embed.ly/)
2. Generate an API key from your dashboard
3. Add API key to the Embedly script:

```html
<script src="https://cdn.embedly.com/widgets/platform.js?key=YOUR_API_KEY"></script>
```

**Note**: The default public CDN works for most use cases. API key is needed for:
- Custom domain whitelisting
- Higher request limits
- Advanced analytics
- Support for restricted content

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

<!-- Blazor Framework Script -->
<script src="_framework/blazor.web.js"></script>
```

## Rich Text Editor Configuration

The editor is configured with a minimal toolbar containing only the CreateLink button:

```csharp
private List<ToolbarItemModel> ToolbarItems = new()
{
    new ToolbarItemModel { Command = ToolbarCommand.CreateLink }
};
```

**Toolbar Features**:
- **CreateLink**: Open link insertion dialog
- Simple, focused interface for URL embedding
- Can be extended with additional toolbar items as needed

## JavaScript Interop Details

### Event Flow

```
1. User clicks CreateLink button in toolbar
2. Syncfusion displays URL input dialog
3. User enters URL and confirms
4. OnActionComplete event fires with RequestType="Links"
5. C# code calls embedlyInterop.wrapLinkInEmbedlyCard()
6. JavaScript wraps link in blockquote element
7. Embedly library processes and renders preview card
```

### Key Functions

**embedlyInterop.wrapLinkInEmbedlyCard()**
- Finds all links in editor content
- Wraps each link in `<blockquote class="embedly-card">`
- Calls Embedly library to process and render
- Prevents duplicate wrapping with guard clause

**initializeEmbedly()**
- Called on component render
- Initializes Embedly library for initial page content
- Ensures preview cards render properly

## Content Samples

### Initial Editor Content

The editor includes helpful instructions:

```html
<p><strong>Embedly integration automatically transforms plain links into rich, 
interactive preview cards with titles, descriptions, and thumbnails.</strong></p>

<h4>How it works:</h4>
<ul>
    <li><strong>Paste or create links</strong> - Use the CreateLink toolbar button</li>
    <li><strong>Automatic card rendering</strong> - Links convert to rich preview cards</li>
    <li><strong>Supported content</strong> - Works with articles, videos, images, documents</li>
</ul>
```

## Customization

### Adding More Toolbar Items

Extend the toolbar by adding more ToolbarCommand items:

```csharp
private List<ToolbarItemModel> ToolbarItems = new()
{
    new ToolbarItemModel { Command = ToolbarCommand.Bold },
    new ToolbarItemModel { Command = ToolbarCommand.Italic },
    new ToolbarItemModel { Command = ToolbarCommand.CreateLink },
    new ToolbarItemModel { Command = ToolbarCommand.Image }
};
```

### Customizing Preview Card Styling

Embedly preview cards can be styled via CSS:

```css
blockquote.embedly-card {
    max-width: 600px;
    margin: 10px 0;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}
```

### Processing Custom Link Formats

Modify `embedly-interop.js` to handle custom link formats:

```javascript
wrapLinkInEmbedlyCard: function(selector) {
    const rteContent = document.querySelector(selector || '.e-rte-content');
    // Custom processing logic
    if (window.embedly && window.embedly.lib) {
        window.embedly.lib.process(rteContent);
    }
}
```

## Troubleshooting

### Preview Cards Not Displaying

1. **Check Internet Connection**: Embedly requires internet access
2. **Verify CDN Loading**: Check browser console for script errors
3. **Allow Cookies**: Some content may require cookies
4. **Embedly Service Status**: Check [status.embed.ly](https://status.embed.ly/)

### Links Not Converting to Cards

- Ensure URL is publicly accessible and embeddable
- Check Embedly API restrictions
- Try a different URL to verify functionality
- Clear browser cache and reload page

### JavaScript Interop Issues

- Verify `embedly-interop.js` is loaded
- Check browser console for JavaScript errors
- Ensure Syncfusion scripts load before Embedly
- Confirm Embedly CDN is accessible

### Performance Issues

- Limit number of embeds on single page
- Use lazy loading for multiple embeds
- Consider implementing pagination
- Monitor Embedly API response times

## API Reference

### Supported Content Types

Embedly automatically detects and embeds:
- **Videos**: YouTube, Vimeo, Dailymotion, etc.
- **Articles**: News sites, blogs, Medium, etc.
- **Social Media**: Twitter, Instagram, LinkedIn, etc.
- **Images**: Hosted images with metadata
- **Documents**: PDF, presentations, spreadsheets
- **Products**: Amazon, eBay, and other retailers
- **Recipes**: Food blogs and recipe sites
- **Tweets**: Twitter content with threading
- **Podcasts**: Audio content platforms

### Event Handlers

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
- [.NET 10 Release Notes](https://learn.microsoft.com/dotnet/core/whats-new/dotnet-10)

## Security Considerations

### URL Validation

- Embedly validates URLs before processing
- Only publicly accessible URLs are embedded
- Some restricted content may not display
- Adult content may be filtered based on settings

### Content Safety

- Embedly performs security scanning
- Malicious URLs are blocked
- SSL/HTTPS is recommended for all links
- Privacy settings can control content display

### CORS Handling

- Embedly handles cross-origin resource sharing
- Works across different domains
- Respects CORS headers from embedded sites

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

## License

This project is provided as part of Syncfusion examples. See the LICENSE file for more details.

**Note**: This is a demonstration project. For production use:
- Ensure you have valid licenses for Syncfusion components
- Register Embedly API key for production use
- Implement appropriate security measures
- Monitor API usage and rate limits
