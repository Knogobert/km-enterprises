# 🏗️ Boilerplate for Nuxt, Tailwind & NetlifyCMS

[![Netlify Status](https://api.netlify.com/api/v1/badges/cb2d4cc5-8a65-4940-81ce-4456ff96e6db/deploy-status)](https://app.netlify.com/sites/ntn-boilerplate/deploys)

**[Live Demo](https://ntn-boilerplate.netlify.app/)**

An opinionated starter template for a quick start with the following technologies up on a site after only 5 minutes!

![NTN Boilerplate Screenshot](https://user-images.githubusercontent.com/770560/92640923-4a36fa80-f2de-11ea-8f96-a7bca7b1e0cc.png)

## 🔋 Batteries included

- Vue 2
- Vuex
- Nuxt.js (in "universal mode", where both SEO and speed is great)
- PostCSS (no SCSS)
- Tailwind
- PurgeCSS (removes unused CSS-selectors)
- Dark mode & custom ColorModePicker (Set to "dark mode first")
- PWA (install website as standalone app)
- Netlify CMS (no need for a separate server)
- Git LFS (store uploaded images outside the main repo)
- Netlify LM (Netlify’s Git LFS support)
- Prettier

## 🎉 Getting Started

1. [![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/knogobert/ntn-boilerplate)

2. **Git clone the repo** (`cd` to projects' outer folder and run your `git clone https://github.com/Knogobert/ntn-boilerplate.git`)

3. **[Install git-lfs](https://git-lfs.github.com/)** on your computer and in your Netlify build settings, set the environment variable `GIT_LFS_ENABLED` : `true`

4. **Setup Netlify CMS** by [enabling Identity](https://app.netlify.com/sites/ntn-boilerplate/settings/identity) and [enabling Git Gateway](https://app.netlify.com/sites/ntn-boilerplate/settings/identity#services). Register a regular email-account (not OAuth yet!) on your site by going to your `/admin` (https://ntn-boilerplate.netlify.app/admin) and then after that [set the registration to invite only](https://app.netlify.com/sites/ntn-boilerplate/settings/identity#registration-preferences)

---

## Project commands

1. 📦 Install dependencies.

```bash
npm install
```

2. 🏗 Run the project for local dev. This will start a hot-reloading server at `localhost:3000`.

```bash
npm run dev
```

3. 🌌 Build the app for server-side rendered deployment. See more about **Universal SSR** in the [Nuxt.js docs](https://nuxtjs.org/guide#server-rendered-universal-ssr-).

```bash
npm run build

# And to serve that deployment...
npm run start
```

4. ⚡️ Generate a fully pre-rendered static site. See more [in the docs](https://nuxtjs.org/guide#static-generated-pre-rendering-).

```bash
npm run generate
```

### Personalize setup

1. Copy and change the .env-file

   - `cp .env-example .env`
   - Then change the values

2. Change the value on these lines

   - `static/admin/config.yml:1` — `site_url`
   - `static/admin/config.yml:2` — `logo_url`
   - `content/site/info.json` — `sitename`, `sitedescription` & `sitelang`
   - `package.json:1` — `name`, `description`, `author` & `repository.url`

3. Change colors, content & content collections

   - Colors are managed in `assets/scss/_vars.scss` & `tailwind.config.js`
   - Content is managed mainly in [local Netlify CMS](http://localhost:3000/admin) or by hand in `assets/content`
   - Content collections are managed in `static/admin/config.yml`, then added to vuex store in `store/index.js`

## More info

> This project was bootstrapped with `create-nuxt-app`. There are more detailed explanations of how everything works in the [Nuxt.js docs](https://nuxtjs.org).

### Netlify Identity

Make sure to set to "registration invite only" [here](https://app.netlify.com/sites/ntn-boilerplate/settings/identity#registration-preferences) if you don't want spam.

When you create your first account, _don’t_ sign up using OAuth, generate a new password and sign in that way locally, otherwise a successful login will send you to the URL you typed in instead of keeping you on localhost.

---

Originally based on [Henry Desroches' nuxt-netlify-cms-starter](https://github.com/xdesro/nuxt-netlify-cms-starter).

Deployed easily with their boilerplate via:
[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/xdesro/nuxt-netlify-cms-starter)

(Don’t forget to set the env var `GIT_LFS_ENABLED` to `true` on your netlify site for LFS to work)

---

## Troubleshooting

1. > I added a CSS class, but it doesn't show

   - It is most likely purged by PurgeCSS, make sure it is whitelisted in `purgeCSS` in `nuxt.config.js`

2. > This repository is configured for Git LFS but 'git-lfs' was not found on your path. If you no longer wish to use Git LFS, remove this hook by deleting .git/hooks/pre-push.

   - Install git-lfs, run `git lfs install` in project root
