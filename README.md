🎧 SOUNDHUB — Plateforme Full-Stack pour Artistes & Producteurs

Django (Architecture Hexagonale) • Django REST • React • PostgreSQL • Docker

<div align="center">

✨ SoundHub est une plateforme moderne pensée pour les artistes, beatmakers, DJ et producteurs.
🎛 Gestion musicale • 📆 Événements • 📰 Mini réseau social • 🎓 Formations • 🌐 API REST scalable

Développé avec une architecture propre (hexagonale), performante et entièrement testable.

</div>
📚 Sommaire

# Présentation

# Fonctionnalités principales

# Stack technique

# Architecture (Hexagonale)

# Structure du projet

# Installation & Lancement

# Variables d’environnement

# Scripts & Commandes

# Tests

# Documentation API

# Roadmap

Contribuer

Licence

# 🎵 Présentation

SoundHub est un hub complet pour les créateurs de musique.
L’objectif est de centraliser plusieurs outils essentiels :

Gestion des morceaux

Organisation de concerts et sessions studio

Mini réseau social dédié aux artistes

Suivi de formations

Création d’une communauté active

Le projet est pensé pour évoluer vers une application mobile (React Native), une API modulaire et un panel administrateur complet.

# ⭐ Fonctionnalités principales
🎧 Module Musical

Upload de morceaux (WAV / MP3)

Métadonnées : BPM, tonalité, tags, genre

Versions multiples d’un même track

Lecteur audio intégré

# 📆 Agenda / Événements

Création d’événements (DJ set, concert, studio)

Rappels automatiques (emails)

Vue calendrier

# 📰 Mini Réseau Social

Publication de posts (texte, image, audio)

Like / Commentaire

Fil d’actualité

# 🎓 Formations

Suivi de cours

Progression utilisateur

Modules organisés

# 🔍 Recherche

Résultats mixtes : tracks / users / events / posts

# 🛡 Authentification

Inscription / Connexion JWT

Profil complet

Upload avatar

🛠 Stack technique
Backend (API)

Django 5

Django REST Framework

PostgreSQL

Celery + Redis

JWT (SimpleJWT)

Architecture Hexagonale ( Ports & Adapters )

Pytest

Frontend (Web)

React + Vite

TailwindCSS

React Query

React Router

Jest

Outils DevOps

Docker & Docker Compose

Makefile (optionnel)

Linters & Formatters

Swagger & ReDoc pour la documentation API

# 🧱 Architecture (Hexagonale)

L’API Django suit une architecture hexagonale parfaitement modulaire :

              Présentation (API)
                    │ views
                    ▼
          ┌───────────────────────┐
          │     Application        │
          │  (use cases / services)│
          └───────────▲───────────┘
                      │ ports
                      ▼
           ┌─────────────────────┐
           │       Domaine       │
           │(entities, business) │
           └───────────▲────────┘
                       │ adapters
                       ▼
      ┌──────────────────────────────────┐
      │      Infrastructure              │
      │ (ORM, DB, external services…)    │
      └──────────────────────────────────┘

Avantages

Séparation totale du métier et de la technologie

Tests beaucoup plus simples

Modularité parfaite pour une future version mobile

Adapters interchangeables (ex : changer S3 → Cloudflare R2 sans toucher au domain)

#📁 Structure du projet
Backend (Django)
backend/
│
├── apps/
│   ├── users/
│   │   ├── domain/
│   │   │   ├── entities.py
│   │   │   └── value_objects.py
│   │   ├── application/
│   │   │   └── services.py
│   │   ├── infrastructure/
│   │   │   ├── models.py
│   │   │   └── repositories.py
│   │   └── presentation/
│   │       ├── serializers.py
│   │       └── views.py
│   │
│   ├── tracks/
│   ├── events/
│   ├── social/
│   └── training/
│
├── config/
│   ├── settings/
│   ├── urls.py
│   └── wsgi.py
│
└── tests/

Frontend (React)
frontend/
│
├── src/
│   ├── components/
│   ├── pages/
│   ├── hooks/
│   ├── services/ (API)
│   ├── store/
│   └── styles/
└── public/

# 🚀 Installation & Lancement
1️⃣ Cloner le repo
git clone https://github.com/<username>/soundhub.git
cd soundhub

2️⃣ Backend : installation locale
cd backend
pip install -r requirements.txt

3️⃣ Frontend : installation
cd frontend
npm install

4️⃣ Lancer en mode Docker
docker-compose up --build


API → http://localhost:8000

Frontend → http://localhost:5173

# 🔧 Variables d’environnement
Backend — .env
SECRET_KEY=your_secret_key_here
DEBUG=True
DATABASE_URL=postgres://user:password@db:5432/soundhub
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_BUCKET_NAME=

Frontend — .env
VITE_API_URL=http://localhost:8000/api

# 🧪 Tests
Backend
pytest
coverage run -m pytest
coverage report

Frontend
npm test

# 📘 Documentation API

Swagger UI :
➡️ /api/docs/swagger/

ReDoc :
➡️ /api/docs/redoc/

# 🗺 Roadmap
v1 — MVP

Auth + profil ✔

Upload musique ✔

Agenda ✔

Social (posts / likes / commentaires)

Formations (module de base)

Recherche globale

v2 — Features avancées

Messages privés

Notifications temps réel

Collaborations entre artistes

Analyse audio BPM / clé (IA)

v3 — Mobile

App React Native

Mode hors-ligne

Sync automatique

# 🤝 Contribuer

Les contributions sont les bienvenues !
Merci de respecter :

L’architecture hexagonale

Les conventions de code

La couverture de tests

Pull requests ouvertes à tous.

📄 Licence

Projet distribué sous licence MIT.
