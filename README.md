# QR-Gen: Advanced QR Code Generator

**QR-Gen** is a robust, responsive, and highly customizable QR code generator built with PHP, jQuery, and Bootstrap. It allows users to generate QR codes for a variety of data types (Links, WiFi, V-Card, Crypto, etc.) with advanced styling options like custom markers, patterns, gradients, frames, and logos.

## 🚀 Features

*   **Multiple Data Types**: Support for URL, Text, E-mail, Location (Google Maps), Telephone, SMS, WhatsApp, Skype, Zoom, WiFi access, V-Card, PayPal, and Bitcoin.
*   **Advanced Styling**:
    *   **Custom Colors**: Solid colors, gradients (linear/radial), and transparency support.
    *   **Patterns & Markers**: Choose from various dot patterns and eye stylings.
    *   **Frames**: Wrap your QR code in call-to-action frames (e.g., "SCAN ME").
    *   **Logos/Watermarks**: Upload your own logo or choose from presets. It supports embedding logos centrally without corrupting the code.
*   **High-Quality Output**: Generates vector SVG files for infinite scaling and high-resolution PNGs.
*   **Responsive Design**: Built with Bootstrap for a seamless mobile and desktop experience.
*   **Multi-language Support**: Built-in localization system.

## 🛠️ Architecture Overview

The project follows a modular structure:

*   **Core Logic**: `lib/class-qrcdr.php` acts as the rendering engine, extending standard QR libraries to support SVGs with custom paths for eyes and data modules.
*   **Frontend**: `js/qrcdr.js` is a jQuery plugin that manages the entire UI state, handling real-time previews via AJAX and managing chunked data uploads for stability.
*   **Configuration**: `config.php` provides a centralized control for enabling/disabling features, setting API keys, and defining default aesthetic values.

## 📂 Project Structure

```
QR-Gen/
├── index.php           # Application Entry point
├── config.php          # Main configuration settings
├── lib/                # Core libraries (QR generation, styling logic)
│   ├── class-qrcdr.php # Main SVG rendering class
│   ├── functions.php   # Helper functions & Singleton
│   ├── markers.php     # SVG path data for eye styles
│   └── frames.php      # SVG path data for frames
├── include/            # UI Components
│   ├── generator.php   # Main form interface
│   └── options.php     # Styling accordion menu
├── ajax/               # Backend Endpoints
│   ├── process.php     # Logic for generating previews
│   └── create.php      # Logic for final file creation
├── template/           # HTML Layout partials (Header, Footer, Navbar)
└── js/                 # Client-side scripts
    └── qrcdr.js        # Main application controller
```

## ⚙️ Requirements

*   **PHP**: Version 5.4 or higher.
*   **Extensions**: `gd` (for image processing), `mbstring` (for multibyte string handling), `fileinfo`.
*   **Server**: Apache/Nginx.

## 🔧 Installation

1.  **Clone the repository**:
    ```bash
    git clone https://github.com/ShoaibAhmedSoomro/QR-Gen.git
    ```
2.  **Configure**:
    *   Rename `config.example.php` to `config.php` (if applicable) or edit `config.php` directly.
    *   Set your Google Maps API Key in `config.php` (`google_api_key`) if using the Location feature.
3.  **Permissions**:
    *   Ensure the `qrcodes/` directory is writable by the web server (chmod 755 or 777).

## 📄 Operational Workflows

1.  **Generation**: Users input data -> JS sends AJAX request -> PHP generates SVG -> JS renders preview.
2.  **Customization**: Changing a color or pattern triggers a debounced AJAX call to update the preview instantly.
3.  **Download**: The application generates a unique file in `qrcodes/` and serves it for download. Old files are automatically cleaned up based on `config.php` settings (`file_lifetime`).

## 🤝 Contribution

Contributions are welcome! Please ensure any modifications to the core generation logic (`lib/class-qrcdr.php`) are tested against various QR error correction levels to maintain code scannability.

---
*Developed by pure dedication to clean, functional code.*
