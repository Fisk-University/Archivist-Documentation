# 📃 Rosenwald Project: Archivist Documentation

This repository helps **archivists, librarians, and digital humanities professionals** at HBCUs and similar institutions replicate the digital archive built at Fisk University for the **Julius Rosenwald Fund** collection. It contains clear, non-technical guidance on how to set up, configure, and launch your own Omeka S-based site with minimal overhead and long-term sustainability.

> ✨ This is the public-friendly version of our internal developer documentation. If you're a developer, please request access to the private repo for system architecture and credentials.

---

## 📆 About the Rosenwald Project

The Rosenwald Project is a Mellon Foundation-funded initiative that digitizes the history of **Julius Rosenwald**, a philanthropist who helped fund thousands of schools for African Americans in the early 20th century. 

Fisk University launched this digital archive to preserve and share Rosenwald-related documents with the world. Just as importantly, we documented every step to help **other HBCUs and cultural memory institutions** replicate this effort with low cost and little technical burden.

This guide is part of our mission to make digital preservation more accessible and sustainable across the archival community.

---

## 📁 Why We Chose Omeka S

[Omeka S](https://omeka.org/s/) is a free and open-source content management system built for digital collections. It's widely used by universities, archives, and museums.

We chose it because:
- It's **designed for metadata-rich archives**
- Supports **modular themes and plugins**
- Has a large user community and solid documentation
- Requires **no licensing fees**

With the right modules and infrastructure, Omeka S offers enterprise power with a low learning curve.

---

## 🚀 What Our Site Uses

### 🎨 Theme
**Rosenwald-Fund-Collection** (custom)
- Matches Fisk University branding
- Prioritizes clarity and accessibility
- Displays collection images, metadata, and search controls in a clean layout
- GitHub: [Rosenwald-Fund-Collection Theme](https://github.com/Fisk-University/Rosenwald-Fund-Collection)

### ⚖️ Modules Used

#### Custom Modules:
- **ZipImport** – Bulk-import images and metadata from a zip file and CSV. ([GitHub](https://github.com/Fisk-University/ZipImport))
- **UnitedSearch** – Lets users filter collections by dual properties (like State and County). ([GitHub](https://github.com/Fisk-University/UnitedSearch))


#### Third-Party Modules:
- **AnyCloud** – Store media files in cloud storage (e.g., Amazon S3)
- **CSV Import** – Import content from spreadsheets (used alongside ZipImport)
- **Common**, **Easy Admin**, **Log**, **Mapping** – Backend helpers and admin utilities
- **CSSEditor** – Add site-specific CSS overrides
- **Item Carousel Block** – Add image carousels to pages

All modules are free and available through Omeka's official plugin directories or GitHub.

---

## 📅 Installation Steps

### 1. Install Omeka S
Follow Omeka's installation guide: https://omeka.org/s/docs/user-manual/install/.
- This repo also includes `Installing-Omeka-S-on-AWS.md` for additional installation support on AWS.

You will need:
- PHP 8.1+
- MySQL 5.7+
- Apache or Nginx

You can install Omeka S on:
- Your local machine (for testing)
- An EC2 instance on AWS or other cloud computing service like Azure (for production/live website)
- A university-managed server (for production/live website)

### 2. Upload the Theme
1. Download the Rosenwald-Fund-Collection theme from GitHub
2. Place it in your `themes/` folder
3. Enable it in your Omeka admin under **Appearance** > **Theme**

### 3. Install and Enable Modules
1. Download modules (ZIP format) from GitHub or Omeka Plugin Directory
2. Place each module folder into the `/modules/` directory
3. Go to **Modules** in the Omeka admin dashboard and click **Install**

Recommended order:
- Install `Common` first (dependency)
- Then `CSV Import`, `AnyCloud`, and `ZipImport`, etc.

### 4. Configure Your Site
- Create a new site under **Sites** tab
- Add your item sets (collections)
- Use the **Site Pages** builder to add pages like "About," "Collections," or "Map"
- Use **Block Layouts** to insert search boxes, carousels, and dropdown filters
- Utilize **ZipImport** to batch import hundreds of digital assets related metadata ([Details](https://github.com/Fisk-University/ZipImport))

### 5. Metadata Suggestions
We use:
- A custom vocabulary for any unique and highly requested metadata (`GlobalVocabulary.ttl` included in this repo for reference) 
- Custom vocabulary `State` and `County` properties (for our custom `Dual Property Search` page block)
- A custom Excel macro and geoloaction data from the US govt to assign lat/long to counties.

---

## 🚧 Reducing Technical and Cost Overhead

We avoided vendor lock-in and kept costs low using:

- **Amazon Web Services (AWS)** infrastructure (In our case, was more cost effective than Azure):
  - EC2: open-source hosting
  - RDS: managed MySQL database
  - S3: cloud media storage
  - IAM: secure access roles
  - Route 53: subdomain management
- **Omeka S**: free and modular, no proprietary CMS required
- **Open-source plugins**: no license fees

For universities with limited IT support, AWS provides scalable hosting that can be documented and replicated with minimal hands-on maintenance.

---

## 🫱🏾 Support & Next Steps

Need help setting up?
- Use the [Omeka S forums](https://forum.omeka.org/)
- Reach out to the Rosenwald Project team at Fisk University

Want to contribute?
- Fork this repository and submit improvements via pull request
- Submit issues if you notice outdated or unclear documentation

This documentation is maintained with replication in mind. If your institution builds on this guide, let us know! We hope this toolkit empowers more archives to preserve history in the digital age.

---

## License

This documentation is published under the [Server Side Public License (SSPL-1.0)](https://www.mongodb.com/legal/licensing/server-side-public-license).

---

Built with ❤️ by LaTaevia Berry for Fisk University and HBCUs nationwide