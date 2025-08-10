# 🚀 My Portfolio Website

A modern, responsive portfolio website built with Vue.js and Vite, showcasing my skills, projects, and professional journey as a Full Stack Developer.

## 🌟 Live Demo

🔗 **[View Live Portfolio](https://jrk-portfolio.netlify.app/)**

## 📋 Table of Contents

- [Features](#features)
- [Technologies Used](#technologies-used)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Components](#components)
- [Deployment](#deployment)
- [Contact](#contact)
- [License](#license)

## ✨ Features

- **Responsive Design**: Works seamlessly on desktop, tablet, and mobile devices
- **Interactive UI**: Smooth animations and transitions using AOS (Animate On Scroll)
- **Skills Showcase**: Comprehensive display of technical skills with icons
- **Project Gallery**: Detailed project presentations with live links and source code
- **Professional Journey**: Timeline of career milestones and achievements
- **Contact Form**: Direct communication capability
- **CV Download**: Downloadable resume functionality
- **Modern Styling**: Clean, professional design with Sass/SCSS

## 🛠️ Technologies Used

### Frontend
- **Vue.js 2.7** - Progressive JavaScript framework
- **Vite** - Next generation frontend tooling
- **Sass/SCSS** - CSS preprocessor for enhanced styling
- **HTML5 & CSS3** - Semantic markup and modern styling

### Libraries & Plugins
- **AOS (Animate On Scroll)** - Scroll animations
- **FontAwesome** - Icon library
- **Vue Typer** - Typing animation effect
- **Vue Slick Carousel** - Image carousel component
- **html2pdf.js** - PDF generation for CV download

### Development Tools
- **Vite** - Build tool and development server
- **GitHub Actions** - CI/CD for automated deployment
- **GitHub Pages** - Hosting platform

## 🚀 Getting Started

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/jagarapuRadhaKrishna/My-Portfolio-Website.git
   cd My-Portfolio-Website
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start development server**
   ```bash
   npm run dev
   ```

4. **Open your browser**
   Navigate to `http://localhost:5173` to view the portfolio

### Build for Production

```bash
npm run build
```

The build artifacts will be stored in the `dist/` directory.

### Preview Production Build

```bash
npm run preview
```

## 📁 Project Structure

```
portfolio/
├── public/                 # Static assets
│   ├── icons/             # Technology and skill icons
│   ├── projects/          # Project screenshots
│   ├── certificates/      # Professional certificates
│   └── journey/           # Career journey images
├── src/
│   ├── components/        # Vue components
│   │   ├── about.vue      # About section
│   │   ├── contact.vue    # Contact form
│   │   ├── journey.vue    # Professional journey
│   │   ├── nav.vue        # Navigation component
│   │   ├── project.vue    # Projects showcase
│   │   ├── skills.vue     # Skills display
│   │   └── summary.vue    # Hero/summary section
│   ├── assets/            # Compiled assets
│   ├── App.vue            # Root component
│   └── main.js            # Application entry point
├── .github/workflows/     # GitHub Actions
├── package.json           # Dependencies and scripts
├── vite.config.js         # Vite configuration
└── README.md              # Project documentation
```

## 🧩 Components

### Core Components

- **Navigation (`nav.vue`)**: Responsive navigation bar with smooth scrolling
- **Summary (`summary.vue`)**: Hero section with introduction and key highlights
- **About (`about.vue`)**: Detailed personal and professional information
- **Skills (`skills.vue`)**: Technical skills with progress indicators and icons
- **Projects (`project.vue`)**: Portfolio of developed applications and websites
- **Journey (`journey.vue`)**: Professional timeline and career milestones
- **Contact (`contact.vue`)**: Contact form and social media links

### Features Components
- **Write Me (`writeMe.vue`)**: Additional contact information
- **Project Details**: Detailed view for specific projects

## 🚀 Deployment

This portfolio is configured for deployment on **Netlify** with automatic builds from GitHub.

### Netlify Deployment (Recommended)

1. **Connect GitHub Repository**:
   - Go to [Netlify](https://www.netlify.com/)
   - Click "New site from Git"
   - Connect your GitHub account
   - Select your repository: `jagarapuRadhaKrishna/My-Portfolio-Website`

2. **Build Settings** (Auto-configured via netlify.toml):
   - **Build command**: `npm run build`
   - **Publish directory**: `dist`
   - **Node version**: 18

3. **Deploy**:
   - Click "Deploy site"
   - Your site will be available at: `https://your-site-name.netlify.app`

### Manual Deployment
If you prefer manual deployment:

```bash
npm run netlify:build
```

### GitHub Pages Alternative
For GitHub Pages deployment:

```bash
npm run deploy
```

### Build Configuration

The project includes optimized configurations:
- **netlify.toml**: Netlify-specific build settings and redirects
- **_redirects**: SPA routing fallback
- **Vite config**: Optimized for production builds

## 📱 Responsive Design

The portfolio is fully responsive and optimized for:
- **Desktop** (1200px+)
- **Laptop** (992px - 1199px)
- **Tablet** (768px - 991px)
- **Mobile** (320px - 767px)

## 🎨 Customization

### Colors and Themes
- Modify the color scheme in `src/assets/styles/` (if using separate style files)
- Update theme variables in component styles

### Content Updates
- Update personal information in respective Vue components
- Add new projects by modifying the projects data structure
- Update skills by adding new entries to the skills array

### Adding New Sections
1. Create a new Vue component in `src/components/`
2. Import and register it in `App.vue`
3. Add navigation link in `nav.vue`

## 🔗 Connect With Me

- **GitHub**: [jagarapuRadhaKrishna](https://github.com/jagarapuRadhaKrishna)
- **LinkedIn**: [Your LinkedIn Profile]
- **Email**: [Your Email Address]
- **Portfolio**: [https://jrk-portfolio.netlify.app/](https://jrk-portfolio.netlify.app/)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Vue.js community for the excellent framework
- FontAwesome for the comprehensive icon library
- GitHub for hosting and CI/CD capabilities
- All open-source contributors who made the libraries used in this project

---

⭐ **If you found this portfolio helpful, please consider giving it a star!**

---

**Note**: This portfolio is continuously updated with new projects and improvements. Feel free to explore the code and use it as inspiration for your own portfolio!
