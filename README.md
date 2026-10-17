# UNAMDD Mining — Projet APK (prêt à importer)

**UNAMDD Mining Sarl**  
Application Android de cartographie minière hors-ligne du cadastre CAMI (RDC).  
Chef du bureau technique : **Ir MANSOUR MAB**

---

## Contenu du projet (tout est à la RACINE)

```
.github/workflows/build-apk.yml   → compilation automatique de l'APK sur GitHub
config.xml                        → configuration Cordova de l'app
package.json                      → dépendances du projet
www/index.html                    → la maquette de l'application
.gitignore
```

> ⚠ IMPORTANT : ces fichiers doivent rester à la **racine** du dépôt GitHub,
> PAS dans un sous-dossier. Sinon la compilation échoue avec
> « Current working directory is not a Cordova-based project ».

---

## Comment compiler l'APK (sans rien installer sur votre PC)

### Étape 1 — Mettre les fichiers dans un dépôt GitHub

1. Créez (ou ouvrez) un dépôt sur GitHub.
2. Cliquez **Add file › Upload files**.
3. Déposez : `config.xml`, `package.json`, `.gitignore` et le dossier `www`.
4. Cliquez **Commit changes**.

### Étape 2 — Ajouter le workflow (le fichier caché .github)

Le dossier `.github` commence par un point et s'envoie mal en glisser-déposer.
Le plus sûr est de le CRÉER directement sur GitHub :

1. **Add file › Create new file**.
2. Nom du fichier (copier-coller exactement) :
   `.github/workflows/build-apk.yml`
3. Collez le contenu du fichier `build-apk.yml` fourni dans ce projet.
4. **Commit changes**.

### Étape 3 — Lancer la compilation

1. Onglet **Actions**.
2. Le workflow se lance tout seul (ou cliquez **Run workflow**).
3. Attendez le rond **vert** (3 à 6 minutes).

### Étape 4 — Récupérer l'APK

- Cliquez sur le run vert.
- Tout en bas, section **Artifacts** → **UNAMDD-Mining-APK**.
- Téléchargez le `.zip`, décompressez-le : vous obtenez `UNAMDD-Mining-debug.apk`.
- Copiez ce fichier sur un téléphone Android et installez-le
  (autorisez « sources inconnues »).

---

## Publier une version officielle (optionnel)

Pour générer en plus une **Release** téléchargeable, créez un tag `v1.0.0` :
le workflow attachera automatiquement l'APK à la Release.

---

## Notes techniques

- Il s'agit d'un **APK de débogage** (debug), parfait pour tester et installer
  en interne. Pour une publication Play Store, il faudra un APK/AAB signé
  (keystore) — étape à prévoir plus tard.
- La maquette (`www/index.html`) utilise des cartes en ligne (Leaflet/OSM/Esri)
  et des données IPIS/CAMI de **démonstration**. Pour le mode 100 % hors-ligne en
  production : fond de carte local (MBTiles/PMTiles), base locale (SQLite) et
  synchro via le backend.
