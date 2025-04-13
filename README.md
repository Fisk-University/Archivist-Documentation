# Archivist-Documentation

# Rosenwald Digital Archive: Omeka S Implementation Guide

## Project Introduction

The **Rosenwald Project** at Fisk University is a **Mellon-funded digital preservation initiative** that documents the philanthropic impact of **Julius Rosenwald**, who supported the construction of thousands of schools for African-American children in the segregated South.

Our mission is to **digitize and share Rosenwald-related archival materials** so that this critical history becomes more accessible to scholars, educators, and the public.

This repository is designed to support **archivists, librarians, and digital project managers**—especially those at **HBCUs**—in **replicating or adapting** our digital collection model using **Omeka S**, a widely-used open-source platform.

The documentation includes step-by-step guidance for:

- Setting up an Omeka S website
- Installing our custom theme and modules
- Configuring your site to match the look and function of the Rosenwald Collection

## Omeka S Overview: What It Is and Why We Chose It

**Omeka S** is a web-based publication system built for universities, galleries, libraries, archives, and museums. It allows institutions to create a local network of independently curated exhibits that share a collaboratively built pool of items and their metadata.

We chose Omeka S because it is:

- **Open-source**, reducing licensing costs and ensuring transparency
- **Modular**, making it easy to extend with custom themes and plugins
- **Widely used in the archival and digital humanities community**, providing strong alignment with best practices and long-term support

## Modules Used

Modules extend the functionality of your Omeka S installation and sites. Below are the core and custom modules developed and used in the Rosenwald Project:

### [ZipImport](https://github.com/Fisk-University/ZipImport)

ZipImport allows for bulk uploading of items and media from a ZIP file containing a CSV and associated files. It supports nested folders for items with multiple media files and automatically creates digital objects in Omeka S. After upload, it returns the original CSV with updated file locations. Works with both local and cloud storage.

### [UnitedSearch](https://github.com/Fisk-University/UnitedSearch)

UnitedSearch adds advanced, hierarchical search functionality. It includes two block types: one for searching within item sets by a specific property, and a dual-property search for linked fields like State and County. It’s ideal for structured data and improves usability across large collections.

### [PropertySearch](https://github.com/Fisk-University/PropertySearch)
PropertySearch adds a simple, targeted search block for users to filter records by school name, state, or county. It’s optimized for discovering Rosenwald school data and integrates seamlessly into Omeka S site pages.


### [ItemSetSearch](https://github.com/Fisk-University/ItemSetSearch)
ItemSetSearch allows administrators to place custom search blocks on any site page. It supports dropdowns, dual-field combos, and flexible search options like "Contains", "Exact match", and "Starts with". All settings can be managed from the admin dashboard.

### [SearchFilterPlus](https://github.com/Fisk-University/SearchFilterPlus)
#TODO: add summary

## Theme Info
**Theme Name**: [`rosenwald-fund-collection`](https://github.com/Fisk-University/Rosenwald-Fund-Collection.git)
- **Design Goals**: This custom Omeka S theme designed for digital collections, providing a clean and modern layout tailored for historical archives and cultural heritage projects. This theme includes customizable navigation, responsive design, and enhanced search functionality to improve user experience. It offers a clean, responsive layout with features tailored for accessibility and usability.

The theme supports:
- Grid and list views for browsing items
- Custom branding with logo, banner, and color options
- Flexible navigation (horizontal or sidebar with child pages)
- Expandable search bar and mobile-friendly design
- Metadata and media display options for clarity and context

Advanced users can customize styles using Sass, but quick visual changes can be made using the CSS Editor module. This theme is built to balance simplicity for archivists with flexibility for developers.

## Installation

### Installing Omeka S
Folow the [Omeka S Installation Guide](https://github.com/omeka/omeka-s/blob/develop/README.md)

### Uploading the theme
To use the `rosenwald-fund-collection` theme:
1. **Download or clone** the theme from the [repository](https://github.com/Fisk-University/Rosenwald-Fund-Collection.git).

2. **Upload the theme folder** to the `/themes/` directory of your Omeka S installation.  
   Example:
   `/path-to-your-omeka-s/themes/rosenwald-fund-collection/`
3. In the Omeka S **admin dashboard**, go to **Sites > [Your Site] > Theme**, and select `rosenwald-fund-collection` from the dropdown menu.
4. **Click "Save"** to apply the theme to your site.

You can now customize the theme’s logo, banner image, colors, and layout options through the admin interface.

See the [theme documentation](https://omeka.org/s/docs/user-manual/sites/site_theme/#install-themes) for more information. 

### Installing & enabling the modules

To install and activate the custom modules used in this project:

1. **Download or clone** each module repository from GitHub.  
   Examples:
   - [ZipImport](https://github.com/Fisk-University/ZipImport)
   - [UnitedSearch](https://github.com/Fisk-University/UnitedSearch)
   - [PropertySearch](https://github.com/Fisk-University/PropertySearch)
   - [ItemSetSearch](https://github.com/Fisk-University/ItemSetSearch)

2. **Upload each module folder** to the `/modules/` directory in your Omeka S installation.  
   Example path: `/path-to-your-omeka-s/modules/ZipImport/`
   
4. In the **Omeka S admin dashboard**, go to **Modules**. You should see each uploaded module listed.

5. Click **“Install”** next to each module. After installation, click **“Activate”** if it’s not already enabled.

Once activated, each module will be available for configuration or use within your sites.

See Omeka S [module documentation](https://omeka.org/s/docs/user-manual/modules/) for more information.

### Configuration notes

After installing the theme and modules, follow these steps to configure your site for optimal functionality:

- **Search Configuration**  
  - In **UnitedSearch**, set up the **Dual Property Search** block to filter counties based on the selected state.
  - Use **PropertySearch** for simpler filtering by school name, state, or county.
  - Add search blocks to your site by navigating to **Sites > Pages > Add Block** and selecting the appropriate module block.

- **Theme Settings**  
  - Go to **Sites > Theme** to upload a logo, set a banner image, and customize accent colors to match your institution’s branding.
  - Choose between **grid or list view** for browsing items, and select how metadata and media should be displayed on item pages.

- **Navigation Structure**  
  - Create top-level and child pages under **Sites > Pages** to build a clear and accessible navigation menu.
  - Use the vertical or horizontal navigation layout based on your content needs.

- **Metadata Templates**  
  - Under **Resource Templates**, you can define standardized metadata fields for items. This ensures consistent data entry across your collection.
  - Suggested fields include: Title, Description, School Name, State, County, and Media Type.

These configurations help ensure your site is easy to navigate, visually consistent, and optimized for search and discovery.

## Tips for Low Overhead

To keep infrastructure affordable and easy to maintain, we built our site using **Amazon Web Services (AWS)** and free, open-source tools. This approach avoids vendor lock-in and gives institutions full control over their digital collections.

- **EC2 (Elastic Compute Cloud)**: Hosts the Omeka S website on a virtual server, allowing flexible scaling without relying on campus IT infrastructure.
- **S3 (Simple Storage Service)**: Stores media files like images and PDFs separately from the website, reducing load on the server and enabling low-cost, reliable storage.
- **IAM (Identity and Access Management)**: Manages admin roles securely, allowing permissions to be customized for different team members.
- **Route 53**: Handles domain routing to ensure the site is accessible at a custom URL.

This setup is cost-effective, scalable, and well-documented—ideal for HBCUs and small institutions looking to build sustainable digital archives.

## Support & Next Steps

This project is maintained by the Rosenwald Project team at Fisk University. If you're an archivist, librarian, or project manager looking to replicate this setup:

- Start by following the steps in this documentation
- Explore the [Omeka S User Manual](https://omeka.org/s/docs/)
- For help or feedback, open a GitHub Issue in this repository

We welcome contributions and collaboration from the community. Whether you're adapting the theme, improving documentation, or building new modules, your work helps expand access to African-American historical records through open-source tools.
