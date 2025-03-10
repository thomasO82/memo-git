# 🚀 Workflow Git Collaboratif (2 Développeurs - 1 Chef de Projet & 1 Dev)

## 📌 **Rôles et responsabilités**

### 🎯 **Chef de Projet (CP)**
- Responsable de la branche `main` (production).
- Participe au développement et a sa propre branche (`prenom-cp`).
- Valide et fusionne les Pull Requests (PR) vers `develop` et `main`.
- Vérifie la qualité du code et organise les tâches.

### 🔥 **Développeur (DEV)**
- Développe les nouvelles fonctionnalités sur des branches spécifiques.
- A sa propre branche (`prenom-dev`).
- Fait des Pull Requests (PR) pour soumettre son travail.
- Corrige les retours du CP et fusionne ses features dans sa branche personnelle avant d’intégrer `develop`.

---

## 📂 **Organisation des Branches**

1. **`main`** : Branche stable, validée et prête pour la production (seul le CP y fusionne).
2. **`develop`** : Branche d'intégration, où les nouvelles features sont testées avant d’aller en `main`.
3. **`prenom-cp`** : Branche personnelle du chef de projet.
4. **`prenom-dev`** : Branche personnelle du développeur.
5. **`feature/nom-de-la-feature`** : Branche temporaire pour chaque nouvelle fonctionnalité.

---

## 🛠 **Étapes du Workflow**

### 1️⃣ **Initialisation du projet**
```bash
git init
git remote add origin https://github.com/organisation/projet.git
git checkout -b main
git push -u origin main
git checkout -b develop
git push -u origin develop
```

---

### 2️⃣ **Les DEV récupèrent le projet et créent leurs branches personnelles**
```bash
git clone https://github.com/organisation/projet.git
cd projet
git checkout -b develop origin/develop
git checkout -b prenom-cp  # Pour le CP
git push -u origin prenom-cp
git checkout -b prenom-dev  # Pour le DEV
git push -u origin prenom-dev
```

---

### 3️⃣ **Démarrer une nouvelle fonctionnalité**
```bash
git checkout prenom-cp  # Ou prenom-dev selon qui travaille
git pull origin develop  # Récupérer les dernières mises à jour
git checkout -b feature/nom-de-la-feature
```

---

### 4️⃣ **Développement et commits réguliers**
```bash
git add .
git commit -m "✨ Ajout de la feature X"
git push origin feature/nom-de-la-feature
```

---

### 5️⃣ **Fusionner la feature dans la branche personnelle**
```bash
git checkout prenom-cp  # Ou prenom-dev
git pull origin prenom-cp  # Ou prenom-dev
git merge feature/nom-de-la-feature
```

---

### 6️⃣ **Mise à jour avec `develop` pour éviter les conflits**
```bash
git checkout develop
git pull origin develop
git checkout prenom-cp  # Ou prenom-dev
git merge develop
```

---

### 7️⃣ **Création d'une Pull Request (PR) vers `develop`**
- Aller sur **GitHub / GitLab / Bitbucket**.
- Créer une **PR de `prenom-cp` ou `prenom-dev` vers `develop`**.
- Demander une **review à l’autre membre de l’équipe**.

---

### 8️⃣ **Validation et fusion dans `develop`**
```bash
git checkout develop
git pull origin develop
git merge prenom-cp  # Ou prenom-dev
git push origin develop
```

---

### 9️⃣ **Déploiement en production (fusion `develop` → `main`)**
```bash
git checkout main
git merge develop
git push origin main
```

---

## 📌 **Mémo des commandes Git utilisées**

### 📁 **Initialisation du projet**
- `git init` → Initialise un dépôt Git.
- `git remote add origin URL` → Associe le dépôt local à un dépôt distant.
- `git checkout -b NOM-BRANCHE` → Crée et bascule sur une nouvelle branche.
- `git push -u origin NOM-BRANCHE` → Pousse la branche vers le dépôt distant.

### 📥 **Récupération du projet et création des branches personnelles**
- `git clone URL` → Clone le projet.
- `git checkout -b develop origin/develop` → Crée et bascule sur `develop`.
- `git checkout -b NOM-BRANCHE` → Crée une nouvelle branche locale.
- `git push -u origin NOM-BRANCHE` → Envoie la branche vers le dépôt distant.

### 🛠 **Gestion des fonctionnalités**
- `git checkout NOM-BRANCHE` → Bascule sur une branche.
- `git pull origin NOM-BRANCHE` → Récupère les dernières mises à jour de la branche.
- `git checkout -b feature/NOM-FEATURE` → Crée une nouvelle branche pour la feature.
- `git add .` → Ajoute tous les fichiers modifiés.
- `git commit -m "Message"` → Crée un commit avec un message.
- `git push origin NOM-BRANCHE` → Pousse la branche vers le dépôt distant.

### 🔄 **Fusion et mise à jour des branches**
- `git merge NOM-BRANCHE` → Fusionne la branche spécifiée dans la branche actuelle.
- `git pull origin develop` → Met à jour `develop` avec les derniers changements.
- `git push origin develop` → Pousse `develop` mis à jour.

### 🚀 **Déploiement en production**
- `git checkout main` → Passe sur `main`.
- `git merge develop` → Fusionne `develop` dans `main`.
- `git push origin main` → Pousse `main` vers le dépôt distant.

---

## 🎯 **Résumé du Workflow**  

1. **Le CP initialise le projet** et gère `main` et `develop`.
2. **Chaque membre de l’équipe crée sa branche personnelle (`prenom-cp` et `prenom-dev`).**  
3. **Pour chaque nouvelle fonctionnalité**, une branche `feature/nom-de-la-feature` est créée.
4. **Les développeurs fusionnent d’abord leurs features dans leur propre branche.**
5. **Ils mettent à jour leur branche avec `develop` avant d’envoyer une PR.**
6. **Le CP et le DEV se review mutuellement et fusionnent dans `develop`.**
7. **Le CP fusionne `develop` dans `main` pour le déploiement.**

---

## 🚀 **Pourquoi ce workflow est efficace ?**  
✅ **Organisation claire** entre CP et DEV.  
✅ **Moins de conflits** grâce aux branches bien séparées.  
✅ **Tests et validation sur les branches personnelles avant `develop`**.  
✅ **Facilité de suivi** avec les Pull Requests.  
✅ **Déploiement structuré** et contrôle qualité assuré par l’équipe.  

Avec cette méthode, votre équipe travaille efficacement tout en maintenant un code propre et stable ! 🔥
