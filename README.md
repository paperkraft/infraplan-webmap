# InfraPlan WebMap

An interactive web-based map displaying infrastructure projects across India, built with **Leaflet.js** and hosted with **GitHub Pages**.

## ✨ Features
- 🗺️ Interactive map with multiple project layers
- 🎨 Custom markers with clustering support
- 🔍 Search and filter functionality
- 📸 Gallery view with project photos
- 📱 Responsive sidebar with layer controls
- 🌍 Multiple basemap styles (Mapbox)
- 📊 Statistics dashboard

## 🚀 Live Demo
[View the map online](https://YOUR_USERNAME.github.io/infraplan-webmap/)

## 📥 Quick Start

### Option 1: Run Locally
1. Clone this repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/infraplan-webmap.git
   cd infraplan-webmap
   ```

2. Open `index.html` in your browser or use a local server:
   ```bash
   python -m http.server 8000
   # Then visit http://localhost:8000
   ```

### Option 2: Deploy to GitHub Pages
1. Create a new GitHub repository named `infraplan-webmap`
2. Push this code to the `main` branch:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/infraplan-webmap.git
   git push -u origin main
   ```

3. Go to **Settings** → **Pages** → Select `main` branch as source
4. Your map will be live at: `https://YOUR_USERNAME.github.io/infraplan-webmap/`

## ⚙️ Configuration

### Adding/Editing Project Layers
Edit the `LAYERS` array in `index.html` (lines 410-445):

```javascript
{
  id:'layer_id',
  name:'Display Name',
  file:'data/your_file.geojson',
  color:'#FF5733',
  shape:'circle',  // circle, square, triangle, star, cross, hexagon
  type:'icon',
  cluster: true,   // true = clustered | false = individual markers
  iconSize: 24
}
```

### Basemap Styles
Supported Mapbox styles (edit line 516):
- `mapbox/streets-v12` (default)
- `mapbox/light-v11`
- `mapbox/dark-v11`
- `mapbox/outdoors-v12`
- `mapbox/satellite-v9`
- `mapbox/satellite-streets-v12`

### Zoom-based Icon Scaling
Modify `ZOOM_SCALE` (lines 475-483) to adjust how icons grow as users zoom:
```javascript
const ZOOM_SCALE = [
  { minZoom:  0, maxZoom:  4, multiplier: 1.0 },
  { minZoom:  5, maxZoom:  6, multiplier: 1.1 },
  // ... more zoom levels
];
```

## 📂 Project Structure
```
infraplan-webmap/
├── index.html              # Main application
├── data/                   # GeoJSON data files
│   ├── Architectural_3D_Mapping.geojson
│   ├── Solar_Energy_Projects.geojson
│   ├── Underground_Drainage_Scheme.geojson
│   ├── City_Development_Plan_and_City_Sanitation_Plan.geojson
│   ├── Hydraulic_Model_Study.geojson
│   ├── Drinking_Water_Supply_Works.geojson
│   └── India_border.geojson
├── icons/                  # Project type icons
│   ├── arch.png
│   ├── solar.png
│   ├── drain.jpg
│   ├── city.jpg
│   ├── hydraulic.png
│   └── water.png
├── images/                 # Project photos
│   ├── Annaram/
│   ├── Boras/
│   ├── Phata/
│   ├── Xekong/
│   └── default.PNG
├── README.md               # This file
└── .gitignore              # Git ignore rules
```

## 🔗 Data Format

GeoJSON files should include the following properties:
```json
{
  "type": "Feature",
  "properties": {
    "Name": "Project Name",
    "Project_Na": "Alternative name",
    "Country": "India",
    "State": "State Name",
    "Description": "Project description",
    "Photos": "path/to/image1.jpg|path/to/image2.jpg",
    "Photo1": "path/to/photo1.jpg",
    "Photo2": "path/to/photo2.jpg"
  },
  "geometry": {
    "type": "Point",
    "coordinates": [longitude, latitude]
  }
}
```

## 🎨 Customization

### Change App Title
Find `#topbar-title` in index.html and update text.

### Change Default Map Center/Zoom
Line 518: `const map = L.map('map').setView([25,78],4);`
- First number: Latitude (25° North)
- Second number: Longitude (78° East)
- Third number: Zoom level (4)

### Custom Colors
Edit CSS variables at the top of `<style>` (lines 19-32):
```css
:root {
  --acc: #2563EB;        /* Accent color */
  --text: #111827;       /* Text color */
  --bg: #FFFFFF;         /* Background */
  /* ... more colors ... */
}
```

## 🛠️ Troubleshooting

### Map Not Loading
1. Check browser console for errors (F12)
2. Ensure all data files are in the correct paths
3. Verify GeoJSON files are valid: [geojsonlint.com](https://geojsonlint.com/)

### Images Not Showing
1. Verify image file paths in GeoJSON properties
2. Check that image files exist in the `images/` folder
3. Ensure paths use forward slashes `/` not backslashes `\`

### GitHub Pages Deployment Issues
1. Ensure repository is **public**
2. Check that Pages is enabled in repository settings
3. Verify branch is set to `main` and folder is `root`
4. Wait 1-2 minutes for deployment to complete

## 🔐 Security Note
The Mapbox access token is visible in the code. For production:
- Create a restricted token with specific URL constraints
- Consider using a backend proxy for token management
- Visit [Mapbox account settings](https://account.mapbox.com/tokens/) to manage tokens

## 📝 License
This project is open source. Modify as needed for your infrastructure projects.

## 👤 Author
Created for InfraPlan - Infrastructure Project Visualization

---

**Last Updated:** June 2, 2026  
**Built with:** Leaflet.js, Mapbox GL, Font Awesome
