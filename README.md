# config
*Use for every (new) project:*

### Vite:
**1. Installera:** npm create vite@latest .

**2. Updatera vid redan installerat(?):** npm install

**3. Kör vite:** npm run dev

**4. vite.config.ts** -filen: <br>
import { defineConfig } from 'vite';

export default defineConfig({
  'base': '/adressen-till-ert-repo-här/'
});

<br>

### .gitignore -fil
**Lägg till följande:** .DS_Store, *.css.map, style.css, node_modules/

<br>

### ESLint
**Installera:** npm init @eslint/config@latest

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
**1. Installera:** npm install --save-dev --save-exact prettier

**2. Skapa en tom config-fil som heter .prettierrc:** node --eval "fs.writeFileSync('.prettierrc','{}\n')"

**3. kapa en prettierignore-fil för att ignorera vissa filer:** node --eval "fs.writeFileSync('.prettierignore','# Ignore artifacts:\nbuild\ncoverage\n')"

**4. Formatera med npm:** npx prettier . --write

**5. Installera eslint-config-prettier för att Prettier och ESLint ska lira ihop:** npm install --save-dev eslint-config-prettier

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
**Installera:** npm install --save-dev sass

Skapa en style.scss-fil och länka in den högst upp i main.ts-filen.

<br>

### Aktivera publicering av sidan på Github
Gå in på GitHub i ert repo, gå till fliken Settings --> Pages och aktivera Pages, välj GitHub Actions i dropdown-menyn. Lägg in publicerings-skript för Vite härifrån i mappen **.github/workflows** - döp filen till **deploy.yml**.

Gå till startsidan på ert repo, klicka på kugghjulet till höger under repo-namnet och klicka sedan i kryssrutan (checkbox:en) Use your GitHub Pages website.

<br>

### Testa att allt fungerar
**I terminalen, skriv:** npm run dev

Gå in på adressen som visas i terminalen, förmodligen **http://localhost:5173** och kolla att sidan syns.

<br>

#### För grupparbete
Nu klonar varje enskild gruppmedlem ner repot till sin dator, och installerar nödvändiga "dependencies" genom att i terminalen skriva **npm install**.

Skriv sedan **npm run dev** och säkerställ att det ser likadant ut på varje persons dator.

