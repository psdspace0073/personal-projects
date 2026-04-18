# Voxlit

**PRODUCT PRIORITISATION · REAL-TIME FEATURE VOTING**

> Real-time feature voting and product prioritisation.  
> Transforms raw user feedback into a ranked, weighted, actionable roadmap signal — with zero backend infrastructure.

---

## 🚀 Overview

Voxlit is a single-page application that gives product teams a live feature-voting board.

Users can:
- Submit feature requests  
- Vote on what matters  
- Watch rankings update in real time  

Product managers get a **clean, weighted signal** instead of noisy feedback.

**Key constraint:**  
- No server  
- No build step  
- No database  
- Ships as **3 static files**

---

## ✨ Core Features

### 🔹 Real-time ranked voting
- Instant re-sorting on every vote  
- Smooth animations and UI feedback  

### 🔹 Fuzzy duplicate detection
- Levenshtein distance matching  
- Prevents duplicate feature submissions  

### 🔹 Weighted voting
- Assign vote multipliers (1.5×, 2×, 3×)  
- Prioritise power users / customers  

### 🔹 Status lifecycle
- Under Review → Planned → In Progress → Shipped  
- Updates public roadmap dynamically  

### 🔹 Effort / Impact matrix
- Drag-and-drop prioritisation  
- Persistent state across refresh  

### 🔹 Magnifying lens UI
- Canvas-powered zoom effect  
- Dynamic background particle system  

---

## ⚡ Getting Started

### 1. Clone the repo
```bash
git clone https://github.com/your-org/voxlit.git
cd voxlit
```

### 2. Serve locally
```bash
# Python
python -m http.server 8080

# Node
npx serve .
```

### 3. Open in browser
```
http://localhost:8080
```

### 4. Deploy
- Vercel  
- Netlify  
- GitHub Pages  

---

## 🏗️ Architecture

### File Structure

| File        | Size  | Responsibility |
|------------|------|----------------|
| index.html | ~140KB | Layout + structure |
| style.css  | ~42KB  | Styling + animations |
| script.js  | ~65KB  | Logic + canvas + state |

---

## 🧩 Rendering Layers

- `#bg-canvas` → Particle system  
- `#fg-layer` → UI content with mask  
- `#lens-ring` → Cursor glow  
- `#lens-cross` → Crosshair  

Lens zoom uses:
- `canvas.clip()`  
- `canvas.scale(2.0)`  

---

## 💾 State Management

All data stored in `localStorage`.

| Key           | Description |
|--------------|------------|
| fv_votes     | Vote counts + user votes |
| fv_features  | Feature objects |
| fv_comments  | Comments per feature |
| fv_matrix    | Effort/impact placement |
| fv_power     | Weighted features |

---

## 🎨 Customisation

### Seed Features
Edit in `script.js`:
```js
const DEFAULT_FEATURES = [...]
const DEFAULT_VOTES = {...}
```

### Theme
Modify CSS variables:
```css
:root {
  --violet: #7B5CF0;
  --black: #080808;
  --white: #F2F2F0;
}
```

### Performance Tuning
```js
const PARTICLE_COUNT = 55;
const ZOOM = 2.0;
const LENS_R = 120;
```

---

## ⌨️ Keyboard Shortcuts

| Key   | Action |
|------|--------|
| N    | Open submit form |
| Esc  | Close panel |
| Enter| Submit comment |

---

## ⚙️ Performance Optimisations

- Single canvas rendering  
- CSS variable masking  
- rAF throttling (60 FPS cap)  
- Precomputed styles  
- Idle frame skipping  

---

## 🗺️ Roadmap

### ✅ MVP
- Voting system  
- Duplicate detection  
- Status lifecycle  
- Admin weighting  
- Matrix + Kanban  
- Comments  
- Lens UI  
- localStorage  

### 🔜 Phase 2 (Backend)
- Auth  
- Cloud sync  
- Notifications  
- Export  
- Webhooks  

### 🏢 Phase 3 (Enterprise)
- SSO  
- RBAC  
- White-label  
- Analytics  
- Integrations  

---

## 🌐 Browser Support

- Canvas API → All modern browsers  
- CSS mask-image → Modern browsers (Safari needs prefix)  
- localStorage → All modern browsers  

---

## 🤝 Contributing

Guidelines:
- Keep it **vanilla JS**  
- No backend dependencies  
- Optimise before modifying render loop  
- Sanitize all user input  
- Use `fv_` namespace for storage  

---

## 🧪 Local Testing

```bash
python -m http.server 8080
```

- Same tab → shared state  
- Incognito → fresh state  

---

## 📄 License

MIT License  
© 2026 Voxlit  
