# 🌞 Sun Movement & Shadow Formation Simulation

An interactive HTML5 simulation for **Cambridge Primary Science Stage 2** (Grade 2) exploring how the sun's position in the sky affects shadow direction and length. Cross-curricular with **Cambridge Primary Maths** (3D Figures).

---

## 🎯 Learning Objectives

- Observe that the sun appears to move across the sky from east to west throughout the day
- Describe how shadow length changes based on the sun's position (longer in morning/evening, shorter at midday)
- Identify that shadows are cast in the opposite direction from the light source
- Recognize 3D shapes (rectangular prisms, cones, cylinders, spheres) in real-world objects

---

## ✨ Features

- **Draggable sun** — move it across a semicircular arc from sunrise (6 AM) to sunset (6 PM)
- **Real-time time display** — shows the time of day as the sun moves
- **Dynamic shadows** — shadow length and direction update instantly based on sun position
- **3D perspective landscape** — buildings and trees rendered as 3D solids on a slanted ground plane
- **Ray-traced lighting** — diffuse shading and specular highlights on all objects
- **Dynamic sky gradient** — sky color shifts from warm sunrise tones to deep blue midday to golden sunset
- **Observation prompts** — on-screen text guides student inquiry as the sun moves
- **Touch-optimized** — works on tablets and mobile devices with large drag targets

---

## 🗂️ Project Structure

```
sun-shadow-sim/
└── index.html       # Complete single-file simulation (no dependencies)
```

---

## 🚀 Deployment

### Run Locally
Open `index.html` directly in any modern browser — no server required.

### Deploy to Vercel
1. Push `index.html` to a GitHub repository
2. Go to [vercel.com](https://vercel.com) and import the repository
3. Vercel auto-detects a static HTML project — click **Deploy**
4. No build configuration needed

---

## 📱 Device Compatibility

| Device | Support |
|---|---|
| Desktop (Chrome, Firefox, Edge) | ✅ Full support |
| iPad / Android tablet | ✅ Touch drag enabled |
| Mobile phone | ✅ Responsive layout |

---

## 🔗 Curriculum Alignment

| Subject | Framework | Topic |
|---|---|---|
| Science | Cambridge Primary Science Stage 2 | Light and Shadows |
| Maths | Cambridge Primary Maths Stage 2 | 3D Shapes / Solid Figures |

---

## 🏫 About

Built for **IPH Schools (SD Intan Permata Hati)**, Surabaya, Indonesia.  
Designed by **Brian Franco Estidola, LPT.** — Primary Science Subject Coordinator  
Part of the **Antigravity** EdTech development project series.

---

## 🛠️ Tech Stack

- Vanilla JavaScript
- HTML5 Canvas
- CSS3 (no external dependencies)
