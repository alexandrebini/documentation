---
title: Code migration - Dependencies - Strapi Developer Docs
description: Migrate your dependencies from Strapi v3.6.x to v4.1.x with step-by-step instructions
canonicalUrl:  http://docs.strapi.io/developer-docs/latest/update-migration-guides/migration-guides/v4/code/backend/dependencies.html
---

# v4 code migration: Updating dependencies

!!!include(developer-docs/latest/update-migration-guides/migration-guides/v4/snippets/code-migration-intro.md)!!!

:::strapi v3/v4 comparison
In Strapi v3, Strapi package names were prefixed with `strapi-`.

Strapi v4 uses scoped packages, prefixed with `@strapi/`.
:::

<!-- To migrate dependencies to Strapi v4, update all references to Strapi packages using the new names found in the following table, and make sure the version number in `package.json` is up-to-date. -->
To migrate depdencies to Strapi v4, many packages no longer need to be defined manually in the `package.json`, below you will see a comparison of a v3 `package.json` vs a v4 `package.json`. All Strapi package versions from the `@strapi/` prefix scope should be the same version.

::: details v3 package.json example

```json
{
  "name": "strapi-v3-project",
  "private": true,
  "version": "0.1.0",
  "description": "A Strapi application",
  "scripts": {
    "develop": "strapi develop",
    "start": "strapi start",
    "build": "strapi build",
    "strapi": "strapi"
  },
  "devDependencies": {},
  "dependencies": {
    "strapi": "3.6.9",
    "strapi-admin": "3.6.9",
    "strapi-utils": "3.6.9",
    "strapi-plugin-content-type-builder": "3.6.9",
    "strapi-plugin-content-manager": "3.6.9",
    "strapi-plugin-users-permissions": "3.6.9",
    "strapi-plugin-email": "3.6.9",
    "strapi-plugin-upload": "3.6.9",
    "strapi-plugin-i18n": "3.6.9",
    "strapi-connector-bookshelf": "3.6.9",
    "knex": "0.21.18",
    "sqlite3": "5.0.0"
  },
  "author": {
    "name": "A Strapi developer"
  },
  "strapi": {
    "uuid": "64f95072-c082-4da8-be68-6d483781cf54"
  },
  "engines": {
    "node": ">=10.16.0 <=14.x.x",
    "npm": "^6.0.0"
  },
  "license": "MIT"
}
```

:::

::: details v4 package.json example

```json
{
  "name": "strapi-v4-project",
  "private": true,
  "version": "0.1.0",
  "description": "A Strapi application",
  "scripts": {
    "develop": "strapi develop",
    "start": "strapi start",
    "build": "strapi build",
    "strapi": "strapi"
  },
  "devDependencies": {},
  "dependencies": {
    "@strapi/strapi": "4.1.2",
    "@strapi/plugin-users-permissions": "4.1.2", // Optional Package
    "@strapi/plugin-i18n": "4.1.2", // Optional Package
    "sqlite3": "5.0.2"
  },
  "author": {
    "name": "A Strapi developer"
  },
  "strapi": {
    "uuid": "b8aa7baf-d6dc-4c50-93d4-7739bc88c3fd"
  },
  "engines": {
    "node": ">=14.x.x <=16.x.x",
    "npm": ">=6.0.0"
  },
  "license": "MIT"
}
```

:::

- Packages with a ❗ emoji before their name are required and need to be defined in your `package.json`
- Packages with a 🔌 emoji before their name are optional plugins/providers that can be installed or removed as needed
- Packages with a ✨ emoji before their name have a new name in v4 but do not need to be defined in your `package.json`
- Packages identified with the ❌  emoji have been removed from v4 and all references to these packages should be removed from the code.

| Package name in Strapi v3          | Package name in Strapi v4             |
| ---------------------------------- | ------------------------------------- |
| strapi                             | ❗ @strapi/strapi                      |
| strapi-database                    | ✨ @strapi/database                    |
| strapi-admin                       | ✨ @strapi/admin                       |
| strapi-utils                       | ✨ @strapi/utils                       |
| strapi-helper-plugin               | ✨ @strapi/helper-plugin               |
| strapi-plugin-users-permissions    | 🔌 @strapi/plugin-users-permissions    |
| strapi-plugin-i18n                 | 🔌 @strapi/plugin-i18n                 |
| strapi-plugin-upload               | ✨ @strapi/plugin-upload               |
| strapi-plugin-documentation        | 🔌 @strapi/plugin-documentation        |
| strapi-plugin-graphql              | 🔌 @strapi/plugin-graphql              |
| strapi-plugin-email                | ✨ @strapi/plugin-email                |
| strapi-plugin-sentry               | 🔌 @strapi/plugin-sentry               |
| strapi-plugin-content-type-builder | ✨ @strapi/plugin-content-type-builder |
| strapi-plugin-content-manager      | ✨ @strapi/plugin-content-manager      |
| strapi-provider-upload-local       | ✨ @strapi/provider-upload-local       |
| strapi-provider-upload-aws-s3      | 🔌 @strapi/provider-upload-aws-s3      |
| strapi-provider-upload-cloudinary  | 🔌 @strapi/provider-upload-cloudinary  |
| strapi-provider-upload-rackspace   | 🔌 @strapi/provider-upload-rackspace   |
| strapi-provider-email-sendmail     | ✨ @strapi/provider-email-sendmail     |
| strapi-provider-email-amazon-ses   | 🔌 @strapi/provider-email-amazon-ses   |
| strapi-provider-email-mailgun      | 🔌 @strapi/provider-email-mailgun      |
| strapi-provider-email-nodemailer   | 🔌 @strapi/provider-email-nodemailer   |
| strapi-provider-email-sendgrid     | 🔌 @strapi/provider-email-sendgrid     |
| create-strapi-starter              | create-strapi-starter                 |
| create-strapi-app                  | create-strapi-app                     |
| strapi-generate-policy             | strapi-generate-policy                |
| strapi-generate-controller         | strapi-generate-model                 |
| strapi-generate-model              | strapi-generate-controller            |
| strapi-generate-new                | strapi-generate-new                   |
| strapi-generate                    | strapi-generate                       |
| strapi-generate-api                | strapi-generate-api                   |
| strapi-generate-plugin             | strapi-generate-plugin                |
| strapi-generate-service            | strapi-generate-service               |
| strapi-connector-mongoose          | ❌ (removed from v4)                   |
| strapi-connector-bookshelf         | ❌ (removed from v4)                   |
| strapi-hook-redis                  | ❌ (removed from v4)                   |
| strapi-hook-ejs                    | ❌ (removed from v4)                   |
| strapi-middleware-views            | ❌ (removed from v4)                   |

Example:

If the `package.json` file of a Strapi v3 application has the `“strapi-plugin-users-permissions”: “3.6.x”` dependency declaration, and the migration targets Strapi v4.1.2, the dependency declaration should be replaced with `“@strapi/plugin-users-permissions”: “4.1.2”`.

<!-- TODO: add a conclusion or links for other steps -->
