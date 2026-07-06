# 🌐  Développement d’une Plateforme E-commerce de Prêt-à-Porter


> Application web complète développée avec **Laravel** — projet académique de développement web full-stack.

[![Laravel](https://img.shields.io/badge/Laravel-10.x-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)](https://laravel.com)
[![PHP](https://img.shields.io/badge/PHP-8.1+-777BB4?style=for-the-badge&logo=php&logoColor=white)](https://php.net)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://mysql.com)
[![Vite](https://img.shields.io/badge/Vite-4.x-646CFF?style=for-the-badge&logo=vite&logoColor=white)](https://vitejs.dev)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

---

## 📋 Table des matières

1. [À propos du projet](#-à-propos-du-projet)
2. [Technologies utilisées](#-technologies-utilisées)
3. [Architecture du projet](#-architecture-du-projet)
4. [Structure des dossiers](#-structure-des-dossiers)
5. [Prérequis](#-prérequis)
6. [Installation](#-installation)
7. [Configuration](#-configuration)
8. [Lancement](#-lancement)
9. [Base de données](#-base-de-données)
10. [Tests](#-tests)
11. [Déploiement](#-déploiement)
12. [Bonnes pratiques](#-bonnes-pratiques)
13. [Auteur](#-auteur)
14. [Licence](#-licence)

---

## 🎯 À propos du projet

**Développement d’une Plateforme E-commerce de Prêt-à-Porter** est une application web développée dans le cadre d'un projet académique de développement web. Elle repose sur le framework **Laravel** selon le patron de conception **MVC (Modèle - Vue - Contrôleur)**, garantissant une séparation claire des responsabilités et une codebase maintenable.

L'application est construite avec une approche **full-stack** :
- Le **back-end** est entièrement géré par Laravel (PHP), avec Eloquent ORM pour la base de données.
- Le **front-end** utilise les templates **Blade** natifs de Laravel avec du CSS personnalisé compilé via Vite.

> ⚠️ Ce dépôt est archivé en lecture seule depuis juin 2025.

---

## 🛠️ Technologies utilisées

### Back-end

| Technologie | Version | Rôle |
|---|---|---|
| **PHP** | >= 8.1 | Langage principal (88.1% du code) |
| **Laravel** | 10.x | Framework MVC principal |
| **Eloquent ORM** | — | Gestion de la base de données |
| **Laravel Artisan** | — | CLI de gestion du projet |
| **PHPUnit** | — | Framework de tests |
| **barryvdh/laravel-ide-helper** | — | Aide à l'auto-complétion IDE |

### Front-end

| Technologie | Version | Rôle |
|---|---|---|
| **Blade** | — | Moteur de templates (7.2% du code) |
| **CSS** | — | Styles personnalisés (4.6% du code) |
| **JavaScript** | — | Interactions légères (0.1% du code) |
| **Vite** | 4.x | Bundler et compilateur d'assets |

### Base de données & Outils

| Technologie | Rôle |
|---|---|
| **MySQL** | Système de gestion de base de données |
| **Composer** | Gestionnaire de dépendances PHP |
| **npm** | Gestionnaire de paquets Node.js |

---

## 🏗️ Architecture du projet

Le projet suit l'architecture **MVC** de Laravel :

```
Requête HTTP
     │
     ▼
┌─────────────┐
│   Routes    │  → routes/web.php
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ Middleware  │  → app/Http/Middleware/
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ Controller  │  → app/Http/Controllers/
└──────┬──────┘
       │
       ├─────────────────────┐
       ▼                     ▼
┌─────────────┐       ┌─────────────┐
│    Model    │       │    View     │
│  (Eloquent) │       │   (Blade)   │
│ app/Models/ │       │ resources/  │
└──────┬──────┘       └─────────────┘
       │
       ▼
┌─────────────┐
│  Database   │
│   (MySQL)   │
└─────────────┘
```

---

## 📁 Structure des dossiers

```
Projet-Dev-Web/
│
├── 📂 app/                          # Cœur de l'application
│   ├── 📂 Http/
│   │   ├── 📂 Controllers/          # Contrôleurs (logique métier)
│   │   ├── 📂 Middleware/           # Filtres de requêtes HTTP
│   │   └── 📂 Requests/            # Validation des formulaires
│   ├── 📂 Models/                   # Modèles Eloquent (entités BDD)
│   └── 📂 Providers/               # Fournisseurs de services
│
├── 📂 bootstrap/                    # Initialisation du framework Laravel
│   ├── app.php                      # Point d'entrée bootstrap
│   └── 📂 cache/                    # Cache de configuration
│
├── 📂 config/                       # Fichiers de configuration
│   ├── app.php                      # Config générale de l'app
│   ├── auth.php                     # Config authentification
│   ├── database.php                 # Config base de données
│   ├── mail.php                     # Config email
│   └── ...                          # Autres configs Laravel
│
├── 📂 database/                     # Tout ce qui concerne la BDD
│   ├── 📂 factories/               # Usines de données de test
│   ├── 📂 migrations/              # Historique de la structure BDD
│   └── 📂 seeders/                 # Données initiales (fixtures)
│
├── 📂 public/                       # Dossier public accessible via le web
│   ├── index.php                    # Point d'entrée de l'application
│   ├── 📂 css/                      # CSS compilés
│   ├── 📂 js/                       # JS compilés
│   └── 📂 images/                  # Images statiques
│
├── 📂 resources/                    # Ressources front-end sources
│   ├── 📂 views/                   # Templates Blade (.blade.php)
│   │   ├── 📂 layouts/             # Layouts partagés (header, footer…)
│   │   ├── 📂 components/          # Composants réutilisables
│   │   └── ...                      # Vues par fonctionnalité
│   ├── 📂 css/                     # Fichiers CSS sources
│   └── 📂 js/                      # Fichiers JavaScript sources
│
├── 📂 routes/                       # Définition des routes
│   ├── web.php                      # Routes web (interfaces utilisateur)
│   ├── api.php                      # Routes API REST
│   └── console.php                  # Commandes Artisan personnalisées
│
├── 📂 storage/                      # Fichiers générés par l'application
│   ├── 📂 app/                     # Fichiers uploadés
│   ├── 📂 framework/               # Cache, sessions, vues compilées
│   └── 📂 logs/                    # Fichiers de log (laravel.log)
│
├── 📂 tests/                        # Tests automatisés
│   ├── 📂 Feature/                 # Tests fonctionnels (end-to-end)
│   └── 📂 Unit/                    # Tests unitaires
│
├── .editorconfig                    # Configuration éditeur de code
├── .env.example                     # Modèle de variables d'environnement
├── .gitignore                       # Fichiers ignorés par Git
├── _ide_helper.php                  # Aide auto-complétion IDE
├── artisan                          # CLI Laravel
├── composer.json                    # Dépendances PHP
├── package.json                     # Dépendances Node.js
├── phpunit.xml                      # Configuration des tests
└── vite.config.js                   # Configuration Vite (assets)
```

---

## ✅ Prérequis

Avant de commencer, vérifiez que les outils suivants sont installés sur votre machine :

| Outil | Version minimale | Vérification |
|---|---|---|
| **PHP** | 8.1 | `php -v` |
| **Composer** | 2.x | `composer -V` |
| **Node.js** | 18.x | `node -v` |
| **npm** | 8.x | `npm -v` |
| **MySQL** | 8.0 | `mysql --version` |
| **Git** | — | `git --version` |

---

## 🚀 Installation

### Étape 1 — Cloner le dépôt

```bash
git clone https://github.com/ibrahimrh555/Projet-Dev-Web.git
cd Projet-Dev-Web
```

### Étape 2 — Installer les dépendances PHP

```bash
composer install
```

> Cela installe toutes les bibliothèques définies dans `composer.json` (Laravel, IDE helper, etc.)

### Étape 3 — Installer les dépendances front-end

```bash
npm install
```

> Cela installe Vite et les outils de compilation des assets CSS/JS.

---

## ⚙️ Configuration

### Étape 4 — Créer le fichier d'environnement

```bash
cp .env.example .env
```

### Étape 5 — Générer la clé de l'application

```bash
php artisan key:generate
```

> Cette commande génère une clé de chiffrement unique pour votre instance.

### Étape 6 — Configurer la base de données

Ouvrez le fichier `.env` et renseignez vos paramètres de connexion MySQL :

```env
# ─── Application ──────────────────────────────────
APP_NAME="Projet Dev Web"
APP_ENV=local
APP_DEBUG=true
APP_URL=http://localhost:8000

# ─── Base de données ──────────────────────────────
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=projet_dev_web      # Nom de votre base de données
DB_USERNAME=root                 # Votre utilisateur MySQL
DB_PASSWORD=                     # Votre mot de passe MySQL

# ─── Cache & Sessions ─────────────────────────────
CACHE_DRIVER=file
SESSION_DRIVER=file
QUEUE_CONNECTION=sync

# ─── Email (optionnel) ────────────────────────────
MAIL_MAILER=smtp
MAIL_HOST=mailpit
MAIL_PORT=1025
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS="hello@example.com"
MAIL_FROM_NAME="${APP_NAME}"
```

---

## ▶️ Lancement

### Étape 7 — Préparer la base de données

Créez d'abord votre base de données MySQL :

```sql
CREATE DATABASE projet_dev_web CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

Puis lancez les migrations :

```bash
# Créer toutes les tables
php artisan migrate

# (Optionnel) Peupler avec des données de démonstration
php artisan db:seed

# (Optionnel) Réinitialiser et repeupler complètement
php artisan migrate:fresh --seed
```

### Étape 8 — Compiler les assets front-end

```bash
# Mode développement avec hot-reload (rechargement automatique)
npm run dev

# Mode production (fichiers optimisés et minifiés)
npm run build
```

### Étape 9 — Démarrer le serveur

```bash
php artisan serve
```

L'application est accessible à l'adresse : **http://localhost:8000**

---

## 🗄️ Base de données

### Commandes utiles

```bash
# Lancer les migrations (créer/mettre à jour les tables)
php artisan migrate

# Voir le statut des migrations
php artisan migrate:status

# Annuler la dernière migration
php artisan migrate:rollback

# Recréer toute la base de données
php artisan migrate:fresh

# Lancer les seeders uniquement
php artisan db:seed

# Recréer + seeder en une commande
php artisan migrate:fresh --seed
```

### Créer de nouvelles ressources

```bash
# Créer un modèle + migration + contrôleur + seeder en une seule commande
php artisan make:model NomDuModele -mcrs

# Créer un contrôleur resourceful
php artisan make:controller NomController --resource

# Créer une migration seule
php artisan make:migration create_nom_table --create=nom_table

# Créer un seeder
php artisan make:seeder NomSeeder
```

---

## 🧪 Tests

Le projet utilise **PHPUnit** configuré via `phpunit.xml`.

```bash
# Lancer tous les tests
php artisan test

# Avec affichage détaillé
php artisan test --verbose

# Lancer uniquement les tests unitaires
php artisan test --testsuite=Unit

# Lancer uniquement les tests fonctionnels
php artisan test --testsuite=Feature

# Lancer un fichier de test spécifique
php artisan test tests/Feature/ExempleTest.php

# Voir la couverture de code (nécessite Xdebug)
php artisan test --coverage
```

### Créer de nouveaux tests

```bash
# Test unitaire
php artisan make:test NomTest --unit

# Test fonctionnel
php artisan make:test NomTest
```

---

## 🚢 Déploiement

Pour déployer l'application en production, exécutez les commandes suivantes :

```bash
# 1. Passer en mode production dans .env
#    APP_ENV=production
#    APP_DEBUG=false

# 2. Installer les dépendances PHP sans dev
composer install --no-dev --optimize-autoloader

# 3. Compiler les assets front-end pour la production
npm run build

# 4. Optimiser le chargement de Laravel
php artisan config:cache
php artisan route:cache
php artisan view:cache

# 5. Lancer les migrations en production
php artisan migrate --force

# 6. Lier le dossier de stockage
php artisan storage:link
```

### Configuration Nginx recommandée

```nginx
server {
    listen 80;
    server_name votre-domaine.com;
    root /var/www/Projet-Dev-Web/public;

    add_header X-Frame-Options "SAMEORIGIN";
    add_header X-Content-Type-Options "nosniff";

    index index.php;
    charset utf-8;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        include fastcgi_params;
    }

    location ~ /\.(?!well-known).* {
        deny all;
    }
}
```

---

## 💡 Bonnes pratiques

### Commandes Artisan fréquentes

```bash
# Vider tous les caches
php artisan cache:clear
php artisan config:clear
php artisan route:clear
php artisan view:clear

# Voir toutes les routes définies
php artisan route:list

# Voir toutes les commandes disponibles
php artisan list

# Ouvrir le shell interactif Tinker (REPL)
php artisan tinker
```

### Variables d'environnement importantes

| Variable | Description | Valeur recommandée (prod) |
|---|---|---|
| `APP_ENV` | Environnement de l'app | `production` |
| `APP_DEBUG` | Mode debug | `false` |
| `APP_KEY` | Clé de chiffrement | Générée automatiquement |
| `DB_CONNECTION` | Type de base de données | `mysql` |
| `CACHE_DRIVER` | Driver de cache | `redis` ou `file` |
| `SESSION_DRIVER` | Driver de session | `database` ou `redis` |
| `QUEUE_CONNECTION` | Driver de file d'attente | `database` ou `redis` |

---

## 👤 Auteur

**Boutklmount Hamza**
**Mohamed Bentimzal**
**Ibrahim Rahmani**



---

## 📄 Licence

Ce projet est distribué sous la licence **MIT**. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

---

## 🔗 Ressources utiles

- 📚 [Documentation Laravel](https://laravel.com/docs)
- 🎓 [Laravel Bootcamp](https://bootcamp.laravel.com)
- 🎬 [Laracasts](https://laracasts.com)
- 🧩 [Packagist — packages PHP](https://packagist.org)
- ⚡ [Documentation Vite](https://vitejs.dev)
- 🧪 [PHPUnit](https://phpunit.de)

---

<p align="center">Fait avec Laravel</p>
