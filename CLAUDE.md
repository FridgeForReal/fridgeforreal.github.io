# Marketing Website - Hugo Static Site

The Marketing Website serves as the primary web presence for FridgeForReal, built with Hugo static site generator to provide a fast, professional landing page that showcases the app's features and builds user awareness ahead of the 2026 launch.

## 🎯 Website Purpose

This website handles:
- **Brand Awareness**: Primary web presence for FridgeForReal brand
- **User Acquisition**: Conversion-optimized landing page for marketing campaigns
- **Feature Showcase**: Detailed presentation of app capabilities and benefits  
- **Launch Preparation**: Email collection and interest building for 2026 app launch
- **Social Proof**: User testimonials and community building
- **Content Marketing**: Educational content about food waste reduction

## 🏗️ Architecture

### Hugo Static Site Architecture
```
Hugo Content → Theme Processing → Static Generation → GitHub Pages
     ↓              ↓                   ↓               ↓
  Markdown    →  Hugo Fresh Theme  →  HTML/CSS/JS  →  Web Hosting
```

### Deployment Pipeline
```
Git Push → GitHub Actions → Hugo Build → GitHub Pages Deploy
    ↓           ↓              ↓             ↓
  Source   →  CI/CD Build  →  Static Files → Live Website
```

## 🗂️ Project Structure

```
fridgeforreal.github.io/
├── hugo.yaml                    # Hugo site configuration
├── go.mod                       # Hugo modules (themes)
├── go.sum                       # Module checksums
├── content/                     # Site content (Markdown)
│   ├── about.md                 # About Us page content
│   ├── comingsoon.md            # Coming Soon page
│   ├── emailconfirmed.md        # Email confirmation page
│   ├── features.md              # Features page content
│   └── mission.md               # Mission and values page
├── archetypes/                  # Content templates
│   └── default.md               # Default page archetype
├── public/                      # Generated static site (build output)
│   ├── index.html               # Homepage
│   ├── css/, js/, images/       # Static assets
│   ├── about/, features/        # Generated pages
│   └── sitemap.xml              # SEO sitemap
├── resources/                   # Hugo build resources
│   └── _gen/                    # Generated assets cache  
└── themes/                      # Hugo themes (git modules)
    ├── hugo-fresh/              # Primary landing page theme
    │   ├── layouts/             # Template files
    │   ├── assets/              # SASS/SCSS source
    │   └── static/              # Theme static assets
    └── bulma/                   # CSS framework theme
        └── sass/                # Bulma CSS framework source
```

## 🎨 Theme & Design

### Hugo Fresh Theme
- **Primary Theme**: Modern SaaS/app landing page theme
- **Repository**: `github.com/StefMa/hugo-fresh v1.2.0`
- **Features**: Hero sections, feature highlights, testimonials, call-to-action
- **Responsive Design**: Mobile-first approach with Bulma CSS framework
- **Components**: Navbar, hero, sections, footer, preloader

### Bulma CSS Framework
- **CSS Framework**: `github.com/jgthms/bulma`
- **Version**: Latest (2025-02-05 snapshot)
- **Features**: Flexbox-based responsive grid, components, utilities
- **Customization**: SASS/SCSS source for theme customization

### Visual Elements
- **Color Scheme**: Modern, clean design with green/blue accent colors
- **Typography**: Sans-serif fonts with clear hierarchy
- **Illustrations**: Custom fridge illustrations and app mockups
- **Icons**: FontAwesome and custom SVG icon sets
- **Loading States**: Animated preloader for smooth UX

## 📄 Site Content & Pages

### Homepage (`/`)
**Hero Section**:
- **Tagline**: "Your Fridge. For real."
- **Subtitle**: "Reducing food waste, one fridge at a time."
- **CTA**: Download button (currently → "Coming Soon")

**Feature Highlights**:
1. **Smart Food Management**: Track inventory with expiration dates
2. **Recipe Suggestions**: AI-powered recipes based on available ingredients
3. **Waste Reduction**: Intelligent notifications and usage tracking

**Social Proof**: User testimonials (3 fictional testimonials)

### Features Page (`/features`)
**Detailed Feature Descriptions**:
- **Inventory Tracking**: Comprehensive food management system
- **Expiration Alerts**: Smart notifications for food freshness
- **Recipe Generation**: AI-powered recipe suggestions
- **Barcode Scanning**: Quick food item identification
- **Usage Analytics**: Track food waste reduction progress

### Mission Page (`/mission`)
**Content Focus**:
- **Problem Statement**: Food waste statistics and environmental impact
- **Solution Approach**: How FridgeForReal addresses the problem
- **Company Values**: Sustainability, technology, user experience
- **Environmental Impact**: Measurable waste reduction goals

### About Us Page (`/about`)
**Team Information**:
- Company story and founding vision
- Team values and approach
- Contact information: `fridgeforreal.contact@gmail.com`
- FAQ section addressing common questions
- Social media links: Instagram (@fridge.for.real)

### Supporting Pages
- **Coming Soon** (`/comingsoon`): Placeholder for app downloads with launch timeline
- **Email Confirmed** (`/emailconfirmed`): Confirmation page for newsletter signups

## 🚀 Build & Deployment

### GitHub Actions Workflow (`.github/workflows/hugo.yml`)
```yaml
name: Deploy Hugo site to Pages
on:
  push:
    branches: ["main"]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          submodules: recursive
      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v3
        with:
          hugo-version: '0.145.0'
          extended: true
      - name: Setup Dart Sass
        run: sudo snap install dart-sass
      - name: Build with Hugo
        run: hugo --minify --baseURL ${{ steps.pages.outputs.base_url }}
      - name: Upload to GitHub Pages
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./public
```

### Build Process
1. **Content Processing**: Markdown files converted to HTML
2. **Asset Compilation**: SASS/SCSS compiled to minified CSS
3. **Template Rendering**: Go templates processed with content data
4. **Static Generation**: Complete static site generated to `/public/`
5. **Optimization**: Minification, image optimization, asset bundling
6. **SEO Generation**: Sitemap, robots.txt, OpenGraph meta tags

### Performance Optimization
- **Minified Assets**: CSS and JavaScript minification
- **Image Optimization**: Compressed images with proper formats
- **SEO Optimization**: Meta tags, structured data, sitemap
- **Fast Loading**: Static site ensures minimal load times

## ⚙️ Configuration

### Hugo Site Configuration (`hugo.yaml`)
```yaml
baseURL: 'https://fridgeforreal.github.io/'
languageCode: 'en-us'
title: 'FridgeForReal'
theme: ['hugo-fresh', 'bulma']

params:
  description: 'Your smart fridge companion that helps reduce food waste'
  social:
    instagram: 'fridge.for.real'
  contact:
    email: 'fridgeforreal.contact@gmail.com'
  launch:
    year: 2026
```

### Hugo Modules (`go.mod`)
```go
module github.com/fridgeforreal/fridgeforreal.github.io

go 1.21

require (
    github.com/StefMa/hugo-fresh v1.2.0
    github.com/jgthms/bulma v0.0.0-20250205140526-7f4c17bb550e
)
```

### Theme Configuration
- **Primary Theme**: hugo-fresh for layout and structure
- **CSS Framework**: bulma for styling and responsive design
- **Module Management**: Hugo modules instead of git submodules
- **Asset Processing**: SASS compilation with Dart Sass

## 📊 SEO & Analytics

### SEO Optimization
- **Meta Tags**: Comprehensive OpenGraph and Twitter Card tags
- **Structured Data**: Schema.org markup for better search indexing
- **Sitemap**: Auto-generated XML sitemap for search engines
- **Clean URLs**: SEO-friendly URL structure
- **Page Titles**: Descriptive, keyword-optimized page titles

### Performance Metrics
- **Static Site Benefits**: Fast loading, CDN-friendly, secure
- **Lighthouse Scores**: Optimized for performance, accessibility, SEO
- **Mobile Optimization**: Responsive design for all device sizes

## 🌐 Integration Points

### FridgeForReal Ecosystem Integration
- **Mobile App Links**: Ready for app store integration (currently placeholder)
- **Email Collection**: Newsletter signup integration for launch notifications
- **Social Media**: Instagram integration for community building
- **Contact Forms**: Direct communication channel via email

### External Services
- **GitHub Pages**: Static site hosting and deployment
- **GitHub Actions**: CI/CD pipeline for automated deployments
- **Social Media**: Instagram account integration
- **Email**: Contact form integration (currently email link)

## 🔧 Development Workflow

### Local Development
```bash
# Prerequisites: Hugo extended, Go, Git
# Install Hugo (macOS)
brew install hugo

# Clone repository with themes
git clone --recursive https://github.com/FridgeForReal/fridgeforreal.github.io
cd fridgeforreal.github.io

# Initialize Hugo modules
hugo mod init github.com/fridgeforreal/fridgeforreal.github.io
hugo mod get

# Start development server
hugo server -D --disableFastRender

# Visit: http://localhost:1313
```

### Content Updates
```bash
# Add new page
hugo new content/new-page.md

# Edit existing content
vi content/features.md

# Build site
hugo --minify

# Deploy (automatic on git push to main)
git add . && git commit -m "Update content" && git push
```

### Theme Customization
- **SASS Variables**: Customize Bulma variables in theme assets
- **Template Overrides**: Override theme layouts in local `layouts/` directory
- **Asset Pipeline**: Add custom CSS/JS through Hugo asset processing

## 📱 Launch Preparation

### 2026 Launch Timeline
- **Current State**: "Coming Soon" placeholder with email collection
- **Pre-Launch**: Build email list, social media presence, content marketing
- **Launch Phase**: Replace "Coming Soon" with actual app store links
- **Post-Launch**: Add user testimonials, press coverage, download metrics

### Conversion Optimization
- **Clear CTAs**: Prominent download buttons and email signup
- **Social Proof**: User testimonials and social media integration
- **Feature Benefits**: Clear value proposition and feature explanations
- **Mobile Experience**: Optimized for mobile visitors (primary audience)

## 🚨 Maintenance

### Regular Updates
- **Content Updates**: Feature descriptions, launch timeline, testimonials
- **Theme Updates**: Hugo Fresh and Bulma version updates
- **Security**: Hugo version updates and dependency management
- **Performance**: Asset optimization and loading speed monitoring

### Monitoring
- **GitHub Pages**: Deployment status and site availability
- **Analytics**: Traffic patterns and conversion rates (when implemented)
- **SEO**: Search rankings and organic traffic growth
- **Social Media**: Instagram engagement and follower growth

---

## 🚀 Quick Start

1. **Prerequisites**: Hugo extended, Go, Git
2. **Clone Repository**: `git clone --recursive [repository]`
3. **Install Dependencies**: `hugo mod get`
4. **Start Development**: `hugo server -D`
5. **Deploy**: Push to main branch for automatic deployment

For comprehensive setup, see the main [FridgeForReal documentation](../CLAUDE.md) and Hugo documentation.