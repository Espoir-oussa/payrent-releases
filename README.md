# Landing page - tmp-payrent-releases

Cette page sert de landing page simple pour télécharger l'APK de test de PayRent.

## Processus manuel (option A)
1. Construis l'APK localement :
   ```bash
   flutter build apk --release
   ```
2. Crée une **Release** sur le repository que tu utilises pour héberger les APKs (ou sur `Espoir-oussa/payrent-releases`), puis téléverse l'APK en tant qu'asset.
3. Recopie l'URL de l'asset APK (ou de la release) et met à jour `tmp-payrent-releases/version.json` :
   - `version`: numéro (ex. "1.0.2")
   - `apkUrl`: URL complète de l'asset APK
   - `releasePage`: URL de la page Release (optionnel)
   - `size`: taille (ex. "25 MB")
   - `releaseDate`: date de release
   - `changelog`: tableau de chaînes

### Script d'aide (optionnel)
Un script PowerShell `scripts/publish_apk.ps1` est fourni pour mettre à jour rapidement `tmp-payrent-releases/version.json` et committer/pusher la modification.

## Exemple `version.json`
```json
{
  "version": "1.0.2",
  "apkUrl": "https://github.com/<owner>/payrent-releases/releases/download/v1.0.2/payrent-v1.0.2.apk",
  "releasePage": "https://github.com/<owner>/payrent-releases/releases/tag/v1.0.2",
  "size": "25 MB",
  "releaseDate": "2025-12-16",
  "changelog": ["Corrections de bugs"]
}
```

---

Si tu veux, je peux :
- t'ajouter un petit bouton d'upload pour faciliter la maintenance locale (mais nécessite config),
- ou automatiser la création de Release avec `gh` (option B) plus tard.

