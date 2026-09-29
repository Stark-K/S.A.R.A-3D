# 🖐️ S.A.R.A 3D Studio

> **Spatial Augmented Reality Assistant** — A bare-hand gesture and voice-controlled 3D spatial CAD engine built with OpenCV, ModernGL, MediaPipe, and Trimesh.

![S.A.R.A 3D Studio Demo](assets/demo.gif)

---

## 🌟 Key Features

- **Bare-Hand Spatial Control:** Real-time 3D rotation, scaling, and translation using dual-hand tracking without external controllers or hardware.
- **Auto-Merge & Precision Snap Engine:** Proximity-based face and vertex snapping that eliminates natural hand jitter and floating-point alignment errors during gesture-driven mesh operations.
- **Real-Time Boolean Mesh Unioning:** Seamlessly combines separate meshes into clean, single-manifold 3D models using `Trimesh`.
- **Multimodal AI Engine:** Voice and natural language command processing for high-level spatial instructions (*"Sara, create a red cube and snap it above the box"*).
- **Asynchronous Pipeline:** Dedicated worker thread for MediaPipe hand tracking to keep GL rendering locked at 60+ FPS.
- **High-Performance Shading:** Custom ModernGL render pipeline featuring PBR lighting options, high-resolution bloom, and dynamic SSAO.
- **Production Asset Export:** Full support for exporting scene assemblies and merged models directly into `.gltf` / `.glb` formats.

---

## 🏗️ Architecture Overview

```text
[ Camera Stream ] ---> [ MediaPipe Thread (Async) ] ---> [ Gesture Queue ]
                                                                 │
                                                                 ▼
[ Voice / NLP Input ] ---------------------------------> [ Spatial Engine ]
                                                                 │
                                                                 ▼
[ ModernGL Renderer (60+ FPS) ] <--- [ Mesh Snap & Union ] <-----┘
