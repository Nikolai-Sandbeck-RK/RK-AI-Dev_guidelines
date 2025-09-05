# 🚀 Guide: Sådan deployer du Docusaurus til GitHub Pages med TypeScript

Denne guide dokumenterer alle trin, som blev fulgt for at sætte et Docusaurus-projekt op med TypeScript og hoste det gratis på GitHub Pages.  
Projekt: **RK-AI-Dev_guidelines**  
Bruger: **Nikolai Sandbeck**

---

## 🧱 1. Opret nyt Docusaurus-projekt

```bash
npx create-docusaurus@latest my-docs classic
# Vælg: TypeScript når du bliver spurgt
cd my-docs
npm install
```

---

## 🧪 2. Test det lokalt

```bash
npm start
```

Åbner: [http://localhost:3000](http://localhost:3000)

---

## ⚙️ 3. Tilpas konfiguration (`docusaurus.config.ts`)

```ts
url: 'https://Nikolai-Sandbeck-RK.github.io',
baseUrl: '/RK-AI-Dev_guidelines/',
organizationName: 'Nikolai-Sandbeck-RK',
projectName: 'RK-AI-Dev_guidelines',
deploymentBranch: 'gh-pages',
trailingSlash: false,
```

---

## 📂 4. Oprydning og opbygning af ny struktur

1. Slet mapperne:
    ```bash
    rm -rf docs/tutorial-basics docs/tutorial-extras
    ```

2. Opret dine egne `.md` filer:
    - `intro.md`
    - `getting-started.md`
    - `structure.md`
    - `prompt-design.md`
    - `evaluation-testing.md`

---

## 🔑 5. Git og GitHub setup

```bash
git init
git remote add origin https://github.com/Nikolai-Sandbeck-RK/RK-AI-Dev_guidelines.git
git add .
git commit -m "Første commit"
git branch -M main
git push -u origin main
```

---

## 🔐 6. Personal Access Token (PAT)

1. Gå til: https://github.com/settings/tokens  
2. Opret en klassisk token med scope: `repo`  
3. Brug den som adgangskode ved push/deploy

---

## 🚀 7. Deploy til GitHub Pages

```bash
npm run build
GIT_USER=Nikolai-Sandbeck-RK npm run deploy
```

Når prompten til at indtaste password viser sig i toppen af vindue i VScode, brug **PAT som adgangskode**.

---

## 🌐 8. GitHub Pages aktivering

1. Gå til: `Settings → Pages`
2. Vælg:
    - Branch: `gh-pages`
    - Folder: `/ (root)`
3. Klik **Save**

URL: https://Nikolai-Sandbeck-RK.github.io/RK-AI-Dev_guidelines/

---

## 🧼 9. Almindelige fejl og løsninger

- **Fejl: "not a git repo"** → `git init` mangler
- **Fejl: "gh-pages does not exist"** → Opret branch eller deploy først
- **Fejl: "Authentication failed"** → Brug PAT, ikke adgangskode

---

✅ Done! Dit site er nu online med din egen struktur, skrevet i TypeScript og hostet gratis 🎉