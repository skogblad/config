# config
*Använd vid varje (nytt) projekt:*

### Vite:
**1. Lägg till:**
```bash
$ npm create vite@latest .
$ npm install
$ npm run dev
```
*- Välj Vue som ramverk om så önskas:*
<br>*- Välj "Customize with create-vue" för att lägga till routing och state management i app:*
<br>*- Välj YES på: Vue Router, Pinia*
<br>*- Välj NO på: JSX Support, Vitest, End-to-end T. S.*

**2. vite.config.ts** -filen: <br>
import { defineConfig } from 'vite';

export default defineConfig({
  'base': '/adressen-till-ert-repo-här/'
});

<br>

### Vue
**1. Lägg till:** 
```bash
$ npm create vue@latest
$ npm install
$ npm run dev
```

<br>

### .gitignore -fil
**Lägg till följande:** .DS_Store, *.css.map, style.css, node_modules/

<br>

### ESLint
**Installera:** 
```bash
$ npm init @eslint/config@latest
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

<br>

### Prettier
**1. Installera:** 
```bash
$ npm install --save-dev --save-exact prettier
```
**2. Skapa en tom config-fil som heter .prettierrc:** 
```bash
$ node --eval "fs.writeFileSync('.prettierrc','{}\n')"
```
**3. Skapa en prettierignore-fil för att ignorera vissa filer:** 
```bash
$ node --eval "fs.writeFileSync('.prettierignore','# Ignore artifacts:\nbuild\ncoverage\n')"
```
**4. Formatera med npm:** 
```bash
$ npx prettier . --write
```
**5. Installera eslint-config-prettier för att Prettier och ESLint ska lira ihop:** 
```bash
$ npm install --save-dev eslint-config-prettier
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

Exempel: Jennis [.prettierrc](https://github.com/postmodernistx/configs/blob/main/.prettierrc.json)

Exempel: Jennis [.prettierignore](https://github.com/postmodernistx/configs/blob/main/.prettierignore)

<br>

### Sass
**Installera:** 
```bash
$ npm install --save-dev sass
```
Skapa en style.scss-fil och länka in den högst upp i main.ts-filen.

<br>

### Aktivera publicering av sidan på Github
- På GitHub för valt repo, gå till fliken Settings
- Välj Pages och aktivera Pages, välj GitHub Actions i dropdown-menyn.
- Lägg in publicerings-skript för Vite härifrån i mappen **.github/workflows**
  - Döp filen till **deploy.yml**.

Gå till startsidan på ert repo, klicka på kugghjulet till höger under repo-namnet och klicka sedan i kryssrutan (checkbox:en) Use your GitHub Pages website.

<br>

#### Testa att allt fungerar
**I terminalen, skriv:**
```bash
$ npm run dev
```
Gå in på adressen som visas, förmodligen **http://localhost:5173** och kolla att sidan syns.

<br>

#### För grupparbete
Nu klonar varje enskild gruppmedlem ner repot till sin dator, och (1) installerar nödvändiga "dependencies" och (2) säkerställ att det ser likadant ut på varje persons dator.
```bash
$ npm install
$ npm run dev
```
<br>

#### Klona repo till privat Github sida
Länk till Jenni's [Youtube video](https://www.youtube.com/watch?v=AAP2b3fKYQ4)
