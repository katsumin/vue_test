## vue 開発環境の作成

- コンテナ起動
  ```sh
  $ docker compose up -d
  ```
- vue 環境作成

  ```sh
  $ docker compose exec -it web bash
  root@9159fc6fa509:/usr/src/app# yarn create vuetify
  yarn create v1.22.22
  (node:24) [DEP0169] DeprecationWarning: `url.parse()` behavior is not standardized and prone to errors that have security implications. Use the WHATWG URL API instead. CVEs are not issued for `url.parse()` vulnerabilities.
  (Use `node --trace-deprecation ...` to show where the warning was created)
  [1/4] Resolving packages...
  [2/4] Fetching packages...
  [3/4] Linking dependencies...
  [4/4] Building fresh packages...
  success Installed "create-vuetify@2.5.2" with binaries:
      - create-vuetify
  [################] 16/16
  Vuetify.js - Material Component Framework for Vue

  ✔ Project name: … vuetify-project
  ✔ Which preset would you like to install? › Default (Adds routing, ESLint & SASS variables)
  ✔ Use TypeScript? … No / Yes
  ✔ Would you like to install dependencies with yarn, npm, pnpm, or bun? › yarn
  ✔ Install Dependencies? … No / Yes

  ◌ Generating scaffold...
  ◌ Installing dependencies with yarn...

  vuetify-project has been generated at /usr/src/app/vuetify-project

  Discord community: https://community.vuetifyjs.com
  Github: https://github.com/vuetifyjs/vuetify
  Support Vuetify: https://github.com/sponsors/johnleider
  Done in 61.98s.
  root@9159fc6fa509:/usr/src/app#
  ```

- vue 環境の起動
  ```sh
  root@9159fc6fa509:/usr/src/app# cd vuetify-project
  root@9159fc6fa509:/usr/src/app# yarn dev --host 0.0.0.0
  ```
