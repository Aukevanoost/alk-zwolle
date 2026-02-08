# ALK Theme

A custom Hugo theme designed for the ALK Zwolle research group website. This theme provides a professional, responsive design suitable for healthcare and research organizations.

## Features

- **Responsive Design**: Mobile-first approach that works on all devices
- **Modern Styling**: Clean, professional design with healthcare-appropriate color scheme
- **Dutch Language Support**: All templates configured for Dutch content
- **Accessible**: Semantic HTML and ARIA attributes for better accessibility
- **Card Layouts**: Modern card-based layouts for content sections
- **Hero Section**: Eye-catching gradient hero section on homepage
- **Sticky Navigation**: Fixed header for easy navigation
- **CSS Variables**: Easy customization through CSS custom properties

## Installation

This theme is included in the ALK Zwolle repository. If you want to use it in another Hugo project:

1. Copy the entire `themes/alk-theme` directory to your Hugo project's `themes` folder
2. Update your `hugo.toml` configuration:

```toml
theme = 'alk-theme'
```

## Configuration

### Site Configuration

Recommended configuration in `hugo.toml`:

```toml
baseURL = 'https://your-domain.nl/'
languageCode = 'nl'
title = 'Your Site Title'
theme = 'alk-theme'

[params]
  description = 'Your site description'
  author = 'Your Name'
```

### Colors

The theme uses CSS custom properties for easy customization. Edit `assets/css/main.css`:

```css
:root {
    --primary-color: #2c5aa0;
    --secondary-color: #4a90e2;
    --accent-color: #6ab04c;
    /* ... more variables */
}
```

### Menu Configuration

Define your menu in `hugo.toml`:

```toml
[menu]
  [[menu.main]]
    name = 'Home'
    url = '/'
    weight = 1
  [[menu.main]]
    name = 'About'
    url = '/about/'
    weight = 2
```

## Layouts

The theme includes the following layouts:

- `baseof.html` - Base template with header, main, and footer
- `home.html` - Homepage with hero section and card grid
- `single.html` - Single page template
- `list.html` - List page template with card layout

## License

MIT License - see LICENSE file for details.
