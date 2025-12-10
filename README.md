# PayRent - Page de Redirection et Téléchargement

Cette page web sert de :
1. **Page de redirection** pour les liens d'invitation par email
2. **Page de téléchargement** pour l'application PayRent

## 🚀 Déploiement sur GitHub Pages

### Étape 1 : Créer le repository

1. Allez sur GitHub et créez un nouveau repository nommé `payrent-releases`
2. Clonez ce dossier `web_redirect` dans le repository

### Étape 2 : Activer GitHub Pages

1. Allez dans **Settings** > **Pages**
2. Source : **Deploy from a branch**
3. Branch : **main** (ou master)
4. Folder : **/ (root)**
5. Cliquez **Save**

### Étape 3 : Votre URL sera

```
https://espoir-oussa.github.io/payrent-releases/
```

## 📱 Publier une nouvelle version de l'APK

### 1. Compiler l'APK

```bash
cd D:\Flutter\payrent
flutter build apk --release
```

L'APK sera dans : `build/app/outputs/flutter-apk/app-release.apk`

### 2. Créer une Release sur GitHub

1. Allez sur votre repo `payrent-releases`
2. Cliquez **Releases** > **Create a new release**
3. Tag : `v1.0.1` (ou la version)
4. Title : `PayRent v1.0.1`
5. Glissez-déposez l'APK (renommez-le en `payrent-v1.0.1.apk`)
6. Cliquez **Publish release**

### 3. Mettre à jour version.json

Modifiez le fichier `version.json` :

```json
{
    "version": "1.0.1",
    "versionCode": 2,
    "releaseDate": "2024-12-15",
    "apkUrl": "https://github.com/Espoir-oussa/payrent-releases/releases/download/v1.0.1/payrent-v1.0.1.apk",
    "size": "25 MB",
    "changelog": [
        "🐛 Corrections de bugs",
        "✨ Nouvelles fonctionnalités"
    ]
}
```

### 4. Commit et Push

```bash
git add version.json
git commit -m "Mise à jour vers v1.0.1"
git push
```

La page affichera automatiquement la nouvelle version !

## 🔗 Configuration dans l'app Flutter

Dans `lib/core/services/email_service.dart`, mettez l'URL :

```dart
static const String webBaseUrl = 'https://espoir-oussa.github.io/payrent-releases';
```

## 📁 Structure des fichiers

```
payrent-releases/
├── index.html      # Page principale
├── version.json    # Informations de version (à mettre à jour)
└── README.md       # Ce fichier
```

## 🎨 Personnalisation

- **Logo** : Modifiez l'emoji 🏠 dans le HTML ou ajoutez une vraie image
- **Couleurs** : Modifiez les variables CSS dans `:root`
- **Textes** : Modifiez directement dans le HTML

## ✅ Test local

Pour tester localement avant de déployer :

```bash
cd web_redirect
python -m http.server 8080
```

Puis ouvrez : `http://localhost:8080?token=test123&action=accept`
