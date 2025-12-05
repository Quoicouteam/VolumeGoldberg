# 🎧 Volume Goldberg — Machine de Rube Goldberg audio

> Une machine de Rube Goldberg, c’est-à-dire une façon bien trop compliquée d’arriver à un résultat.  
> Ici : contrôler le volume audio du système via une interface artistique composée de leviers, engrenages et animations inspirées d’un vieux phonographe.

---


---

## 👀 Aperçu

Ce projet représente un contrôleur audio entièrement animé :
- une platine avec disque rotatif,
- un bras/toneram articulé,
- un levier mécanique servant de contrôle de volume,
- un châssis façon phonographe vintage avec texture métallisée et gaufre géométrique.

Le tout fonctionne comme une **machine de Rube Goldberg**, c’est-à-dire une suite d’actions visuelles et absurdes pour accomplir une tâche triviale : modifier le volume.

---

## ✨ Fonctionnalités

- 📀 *Animation du disque (Spinner)* en fonction du volume
- 🎚️ *Levier interactif* (Lever) utilisant `v-model`
- 🎛️ Composants stylisés (métal, parallélépipède 3D, interrupteurs)
- 🔊 Intégration avec un système audio externe
- 🎥 Animations CSS et transitions synchronisées
- 🧩 Compatible Vue 3 & Composition API

---

## 🛠️ Technologies utilisées

- **Vue 3** (Composition API + Single File Components)
- **Vite**
- **JavaScript**
- **CSS moderne (gradients, ombres, textures)**

---

## 📥 Installation

```sh
npm install
npm run dev
```

## 🧩 Usage 
Passez par l'adresse http://localhost:5173/


## 📁 Structure du projet
```sh
src/
├── components/
│    ├── goldberg_audio/
│    │     ├── Patiphon.vue        # composant principal de la machine
│    │     ├── Lever.vue           # levier (volume)
│    │     ├── Spinner.vue         # disque rotatif
│    │     └── Toneram.vue         # bras/toneram
│    └── ...
├── App.vue
└── main.js
```
