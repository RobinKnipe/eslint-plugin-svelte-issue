# eslint-plugin-svelte-issue

Project to show bun install issue in `eslint-plugin-svelte` because of dependency version problem.

## Skeleton Svelte library

Project created with the standard `svelte@latest` CLI:

```shell
$ bun create svelte@latest

create-svelte version 6.0.9

┌  Welcome to SvelteKit!
│
◇  Where should we create your project?
│    (hit Enter to use current directory)
│
◇  Directory not empty. Continue?
│  Yes
│
◇  Which Svelte app template?
│  Library project
│
◇  Add type checking with TypeScript?
│  Yes, using TypeScript syntax
│
◇  Select additional options (use arrow keys/space bar)
│  Add ESLint for code linting, Add Prettier for code formatting, Try the Svelte 5 preview (unstable!)
│
└  Your project is ready!

✔ Typescript
  Inside Svelte components, use <script lang="ts">

✔ ESLint
  https://github.com/sveltejs/eslint-plugin-svelte

✔ Prettier
  https://prettier.io/docs/en/options.html
  https://github.com/sveltejs/prettier-plugin-svelte#options

Install community-maintained integrations:
  https://github.com/svelte-add/svelte-add

Next steps:
  1: bun install
```

## Bun install failure

Following the next steps (installation) fails with the following error:

```shell
$ bun install
bun install v1.0.26 (c75e768a)
warn: incorrect peer dependency "svelte@5.0.0-next.80"

error: No version matching ">=0.34.0-next.12 <1.0.0" found for specifier "svelte-eslint-parser" (but package exists)
```

## Suggested fix

Switch to the `fix` branch and see the suggested resolution (PR pending) which successfully installs with `bun`:

```shell
$ git checkout fix
$ bun install
bun install v1.0.26 (c75e768a)
warn: incorrect peer dependency "svelte@5.0.0-next.80"

 + @sveltejs/adapter-auto@3.1.1
 + @sveltejs/kit@2.5.4
 + @sveltejs/package@2.3.0
 + @sveltejs/vite-plugin-svelte@3.0.2
 + @types/eslint@8.56.6
 + @typescript-eslint/eslint-plugin@7.3.1
 + @typescript-eslint/parser@7.3.1
 + eslint@8.57.0
 + eslint-config-prettier@9.1.0
 + eslint-plugin-svelte@git+ssh://github.com/RobinKnipe/eslint-plugin-svelte#5d72c27ad81b12c471c8f84ea1bb685f1677c636
 + prettier@3.2.5
 + prettier-plugin-svelte@3.2.2
 + publint@0.1.16 (v0.2.7 available)
 + svelte@5.0.0-next.80
 + svelte-check@3.6.8
 + tslib@2.6.2
 + typescript@5.4.2
 + vite@5.1.6

warn: @sveltejs/kit's postinstall script took 727.4ms

 230 packages installed [4.16s]
```