# UMIDSHOTS - Portfolio Website

A modern, responsive portfolio website for a mobilographer and content creator. Built with Vue.js and Vite.

## Features

- 🎨 Modern, clean design with gradient animations
- 📱 Fully responsive (mobile, tablet, desktop)
- ⚡ Fast performance with Vite
- 🎬 Portfolio gallery with category filtering
- 📧 Contact form
- 🎭 Smooth animations and transitions
- 🌐 SEO-friendly structure

## Project Setup

### Prerequisites
- Node.js (version 16 or higher)
- npm or yarn

### Installation

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Customization Guide

### 1. Personal Information

Edit the following sections in the components:

#### Hero Section (`src/components/Hero.vue`)
- Change the subtitle, title, and description
- Update statistics (projects, followers, years)

#### About Section (`src/components/About.vue`)
- Add your photo (replace the placeholder)
- Update the bio text
- Customize skills and expertise areas

#### Contact Section (`src/components/Contact.vue`)
- Update email, phone, and location
- Add your social media links
- Configure form submission endpoint

### 2. Portfolio Projects

Edit `src/components/Portfolio.vue`:
- Update the `projects` array with your actual work
- Add real images (place them in `src/assets/`)
- Customize categories

### 3. Color Scheme

Edit `src/style.css` to change colors:
```css
:root {
  --primary-color: #0a0a0a;
  --accent-color: #ff6b6b;
  --gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}
```

### 4. Adding Images

1. Place images in the `public/` folder or `src/assets/`
2. For About section photo:
   - Replace the placeholder in `About.vue` with:
   ```html
   <img src="/your-photo.jpg" alt="Your Name" />
   ```
3. For portfolio items, update the projects array with image paths

### 5. Social Media Links

Update links in:
- `src/components/Contact.vue` (contact section)
- `src/components/Footer.vue` (footer section)

Replace `#` with your actual social media URLs.

## Project Structure

```
umidshots-vue/
├── public/
├── src/
│   ├── assets/
│   ├── components/
│   │   ├── Navigation.vue
│   │   ├── Hero.vue
│   │   ├── About.vue
│   │   ├── Portfolio.vue
│   │   ├── Contact.vue
│   │   └── Footer.vue
│   ├── App.vue
│   ├── main.js
│   └── style.css
├── index.html
├── package.json
└── vite.config.js
```

## Deployment

### Netlify
1. Connect your GitHub repository
2. Build command: `npm run build`
3. Publish directory: `dist`

### Vercel
1. Import your repository
2. Framework preset: Vite
3. Build command: `npm run build`
4. Output directory: `dist`

### GitHub Pages
```bash
npm run build
# Upload the dist folder to your gh-pages branch
```

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## License

MIT License - feel free to use this template for your personal portfolio!

## Credits

Built with:
- Vue.js 3
- Vite
- Pure CSS (no frameworks)
- Google Fonts (Inter & Playfair Display)
