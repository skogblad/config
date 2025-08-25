# config
*Använd vid varje (nytt) projekt:*

### Vite:
**1. Lägg till:**
```bash
npm create vite@latest .
```
*alternativt installera en exakt version (som vets är stabil: 5/5/2025):*
```bash
npm install vite@4.0.0 --save-dev
```
*- Välj Vue som ramverk om så önskas (nedan för skolprojekt):*
<br>*- Välj "Customize with create-vue" (Official Vue Starter) för att lägga till routing och state management i app:*
<br>*- Välj YES på: Vue Router*
<br>*- Välj NO på: JSX Support, Vitest, End-to-end T. S., Pinia*
<br>*- Välj om önskas Eslint + Prettier. **OBS!** - lägg in reglerna nu direkt så de kommer med i formateringen nedan*

```bash
npm install
npm format
npm run dev
```
**2. vite.config.ts** -filen: <br>
import { defineConfig } from 'vite';

export default defineConfig({
  'base': '/adressen-till-ert-repo-här/'
});

-----

### Vue / React
**1. Lägg till:** 
*Vue:*
```bash
npm create vue@latest
```

*React:*
```bash
npm create vite@latest
```

***--> Välj önskat ramverk***

```bash
npm install
```
```bash
npm run dev
```

*React Router:*
```bash
npm i react-router
```
-----

### Node.js
[Läs mer här](https://nodejs.org/en/download)

#### Express
```bash
npm install express --save
```
#### Express & TypeScript:
[Läs mer här](https://kinsta.com/blog/express-typescript/?utm_source=chatgpt.com)

-----

### API

#### mongoose:
```bash
npm install mongoose
```
[Läs mer här](https://www.npmjs.com/package/mongoose)

#### jsonwebtoken:
```bash
npm install jsonwebtoken
```
```bash
npm install --save @types/jsonwebtoken
```
[Läs mer här](https://www.npmjs.com/package/jsonwebtoken)

#### cookie-parser:
```bash
npm install cookie-parser
```
```bash
npm install --save @types/cookie-parser
```
[Läs mer här](https://www.npmjs.com/package/cookie-parser)

### Guide

<details>
<summary><strong>Guide</strong> <i>(1 image)</i></summary>

##### Från API-utvecklig kurs:
![Skärmavbild 2025-03-18 kl  08 52 38](https://github.com/user-attachments/assets/53734d58-5de6-4aaf-b91b-689aab7cf312)

</details>

-----

### .gitignore -fil
**Lägg till följande:** <br>
dist <br>
node_modules <br>
.DS_Store <br>
package-lock.json <br>
.env

-----

### ESLint
**Installera:** 
```bash
npm init @eslint/config@latest
```
**Exempel rules:** <br>
import globals from "globals";
import pluginJs from "@eslint/js";
import tseslint from "typescript-eslint";

/** @type {import('eslint').Linter.Config[]} */
export default [
  {files: ["**/*.{js,mjs,cjs,ts}"]},
  {
    languageOptions: { globals: globals.browser },
    rules: {
      camelcase: "error",
      'comma-dangle': ['error', 'always-multiline'], // Enforce trailing commas in multiline
      'curly': ['error', 'all'], // Require curly braces for all control statements
      'no-console': 'warn', // Warn about console.log usage
    },
  },
  pluginJs.configs.recommended,
  ...tseslint.configs.recommended,
];

**ESLint-kontroll**
```bash
npm run lint
```
-----

### Prettier
**1. Installera:** 
```bash
npm install --save-dev --save-exact prettier
```
**2. Skapa en tom config-fil som heter .prettierrc:** 
```bash
node --eval "fs.writeFileSync('.prettierrc','{}\n')"
```
**3. Skapa en prettierignore-fil för att ignorera vissa filer:** 
```bash
node --eval "fs.writeFileSync('.prettierignore','# Ignore artifacts:\nbuild\ncoverage\n')"
```
**4. Formatera med npm:** 
```bash
npx prettier . --write
```
**5. Installera eslint-config-prettier för att Prettier och ESLint ska lira ihop:** 
```bash
npm install --save-dev eslint-config-prettier
```
**6. Öppna eslint.config.mjs-filen och lägg till dessa 2 rader:** <br>
import globals from "globals";
import pluginJs from "@eslint/js";
import tseslint from "typescript-eslint";
*import eslintConfigPrettier from "eslint-config-prettier";*

/** @type {import('eslint').Linter.Config[]} */
export default [
  {files: ["**/*.{js,mjs,cjs,ts}"]},
  {
    languageOptions: { globals: globals.browser },
    rules: {
      camelcase: "error",
      'comma-dangle': ['error', 'always-multiline'], // Enforce trailing commas in multiline
      'curly': ['error', 'all'], // Require curly braces for all control statements
      'no-console': 'warn', // Warn about console.log usage
    },
  },
  pluginJs.configs.recommended,
  ...tseslint.configs.recommended,
  *eslintConfigPrettier*
];

**7. Övrigt:** <br>
Installera Prettier-tillägget i VSC.
Öppna sedan filen .prettierrc och lägg in era regler i den, se exempel här [exempel här](https://prettier.io/docs/en/configuration#basic-configuration) (Basic Configuration, JSON).

Starta om Visual Studio Code.

Alla regler som finns tillgängliga hittar ni [här](https://prettier.io/docs/en/options).

**Exempel: Jennis [.prettierrc](https://github.com/postmodernistx/configs/blob/main/.prettierrc.json)**

**Exempel: Jennis [.prettierignore](https://github.com/postmodernistx/configs/blob/main/.prettierignore)**

-----

### Sass
**Installera:** 
```bash
npm install --save-dev sass
```
Skapa en style.scss-fil och länka in den högst upp i main.ts-filen.

-----

### Aktivera publicering av sidan på Github
- På GitHub för valt repo, gå till fliken Settings
- Välj Pages och aktivera Pages, välj GitHub Actions i dropdown-menyn.
- Lägg in publicerings-skript för Vite härifrån i mappen **.github/workflows**
  - Döp filen till **deploy.yml**.

Gå till startsidan på ert repo, klicka på kugghjulet till höger under repo-namnet och klicka sedan i kryssrutan (checkbox:en) Use your GitHub Pages website.

-----

### Testa att allt fungerar
**I terminalen, skriv:**
```bash
npm run dev
```
Gå in på adressen som visas, förmodligen **http://localhost:5173** och kolla att sidan syns.

<br>

#### För grupparbete
Nu klonar varje enskild gruppmedlem ner repot till sin dator, och (1) installerar nödvändiga "dependencies" och (2) säkerställ att det ser likadant ut på varje persons dator.
```bash
npm install
npm run dev
```
-----

### Klona repo till privat Github sida
Länk till Jenni's [Youtube video](https://www.youtube.com/watch?v=AAP2b3fKYQ4)
```bash
git remote remove origin
git remote add origin *new_repository*
git branch -M main
git push -u origin main
```

Vid publicering av projektet, dvs. göra om TS -> JS och Sass -> CSS, kör script:
```bash
npm run build
```
