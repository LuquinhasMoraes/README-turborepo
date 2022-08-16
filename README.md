# Looplex Turborepo

The official Looplex Monorepo. **DO NOT forget your daily `git pull`**, otherwise it may get complicated for you to keep your local copy up-to-date.

[![Monorepo](https://img.shields.io/badge/powered_by-pnpm-F69220.svg?style=for-the-badge&logo=pnpm)](https://pnpm.io/workspaces)
[![Turborepo](https://img.shields.io/badge/builds_with-turborepo-4682B4.svg?style=for-the-badge&logo=turborepo)](https://turborepo.org/)
[![Plop](https://img.shields.io/badge/automation-plop-792ee5.svg?style=for-the-badge&logo=pytorch-lightning)](https://plopjs.com/)
[![Next.JS](https://img.shields.io/badge/apps_with-next.js-black.svg?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![Microbundle](https://img.shields.io/badge/modules_by-microbundle-8dd6f9.svg?style=for-the-badge&logo=webpack)](https://github.com/developit/microbundle#readme)
[![Ant Design System](https://img.shields.io/badge/ant-design_system-0170fe.svg?style=for-the-badge&logo=ant%20design)](https://ant.design/)
[![MobX State Tree](https://img.shields.io/badge/state_management-mst-ff7102.svg?style=for-the-badge&logo=mobx-state-tree)](https://mobx-state-tree.js.org)
[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-f7df1e.svg?style=for-the-badge&logo=eslint)](https://standardjs.com)
[![Jest Testing Framework](https://img.shields.io/badge/tested_with-jest-c21325.svg?style=for-the-badge&logo=jest)](https://jestjs.io/)
[![Playwright](https://img.shields.io/badge/e2e_testing-playwright-40b5a4.svg?style=for-the-badge&logo=puppeteer)](https://playwright.dev/)
[![Commitizen Friendly](https://img.shields.io/badge/commitizen-friendly-f05032.svg?style=for-the-badge&logo=git)](http://commitizen.github.io/cz-cli/)
[![Semantic Release](https://img.shields.io/badge/semantic-release-cb3837.svg?style=for-the-badge&logo=npm)](https://semantic-release.gitbook.io/semantic-release/)

## Usage

- **create** `plop`
- **add dependency** `pnpm add {{package}} --filter={{workspace.name}}`
- **add development dependency** `pnpm add -D {{package}} --filter={{workspace.name}}`
- **remove dependency** `pnpm rm -D {{package}} --filter={{workspace.name}}`

## Conventional Commits Scopes

```
<type>(<scope>): <short summary>
  │       │             │
  │       │             └ Summary in present tense. Not capitalized. No period at the end.
  │       │
  │       └ Commit Scope: see below
  │
  └ Commit Type: build|ci|docs|feat|fix|perf|refactor|test
```

- `api` (actions)
- `code`
- `assembler`
- `cases`
- `dashboards`
- `explorer`
- `finances`
- `monorepo`
- `people`
- `sectioning`
- `vault`
- `workflows`

## Why?

### PNPM Workspaces ❤ Turborepo

Monorepos are **AWESOME** for sharing and collaborating modules. Keeping the code organized is easier when compared to [git submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules) and [template repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-template-repository).

Though [npm workspaces](https://docs.npmjs.com/cli/v7/using-npm/workspaces) provides support to managing multiple packages, it doesn't scale well neither for complex application builds nor for multiple projects. That's why we leverage **PNPM for managing `node_modules`** and **Turborepo to reduce the building time**. Turborepo features:

* **Faster, incremental builds**: Building once is painful enough, Turborepo will remember what you've built and skip the stuff that's already been computed.
* **Content-aware hashing**: Turborepo looks at the contents of your files, not timestamps to figure out what needs to be built.
Cloud caching: Share a cloud build cache with your teammates and CI/CD for even faster builds.
* **Parallel execution**: Execute builds using every core at maximum parallelism without wasting idle CPUs.
Zero runtime overhead: Turborepo doesn't interfere with your runtime code or touch your sourcemaps. It does what it does and then gets out of your way.
* **Task pipelines**: Define the relationships between your tasks and then let Turborepo optimize what to build and when.
* **Pruned subsets**: Speed up PaaS deploys by generating a subset of your monorepo with only what's needed to build a specific target.
* **Convention-based config**: Reduce complexity through convention. Fan out configuration with just a few lines of JSON.
* **Profile in your browser**: Generate build profiles and import them in Chrome or Edge to understand which tasks are taking the longest.

which works very well with [PNPM](https://pnpm.io/) intelligent management of `node_modules` using hard and symbolic links:

![PNPM Idea](https://pnpm.io/assets/images/cafs-illustration-7be6bd97e43ba11a031b099869321deb.jpg)

### MobX-State-Tree
* The complete application flow can be tested without ever needing to instantiate a component.
* Decoupling models and views ensures our models will keep working great in the future.
* More components can be dumb; they don’t have to fetch data or process routing.
* Our stores become more like a state machine, making it easy to follow the transitions of our application.
* Via runtime type checking, you can't accidentally assign the wrong data type to a property.
* TypeScript can infer static types from your runtime types automatically.
* Using snapshots and patches, you can do time-travel debugging or logging of state changes over time.

### Conventional Commits
* Automatically generating CHANGELOGs.
* Automatically determining a semantic version bump (based on the types of commits landed).
* Communicating the nature of changes to teammates, the public, and other stakeholders.
* Triggering build and publish processes.
* Making it easier for people to contribute to your projects, by allowing them to explore a more structured commit history.

## Our Standards and Rules

| Context                                |                            Specification                             |
|:---------------------------------------|:--------------------------------------------------------------------:|
| Storing and Sharing **Date and Time**  | [ISO 8601 Z](https://www.iso.org/iso-8601-date-and-time-format.html) |
| Storing and Sharing **Country Codes**  |     [ISO 3166](https://www.iso.org/iso-3166-country-codes.html)      |
| Storing and Sharing **Language Codes** |     [ISO 639-1](https://www.iso.org/iso-639-language-codes.html)     |
| Storing and Sharing **Currency Codes** |     [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html)     |
| Runtime **Charset**                    |                            UTF-8 (65001)                             |
| Runtime **Language Code**              |                             en-US (1033)                             |

When dealing with resource repositories, we follow the structure below:

```
<domain.com>/<user|shared>/<module>/<resource_path>
  │            │             │        │
  │            │             │        └ module author `resource_path` template. Not capitalized. No period at the end.
  │            │             │
  │            │             └ module id
  │            │
  │            └ usually shared
  │
  └ organization domain
```

## Features

- [x] Customize Turborepo for Javascript
- [x] Configure Standard + Snazzy
- [x] Configure Commitizen + Conventional Commit Messages + Standard Version
- [x] Configure Playwright for applications
- [x] Configure Jest for both applications and packages
- [x] Configure Ant Design + Icons + Charts
- [x] Configure Less 3.x.x compiler scripts
- [ ] Configure Mobx State Tree + Hot Module Reloading
- [ ] Configure Full Calendar
- [ ] Configure Kodiak to automate feature-* reconciliation into `testing`
- [ ] Configure CI/CD
- [ ] Implement [Sectioning](https://html.spec.whatwg.org/multipage/sections.html) (global layout)
- [ ] Implement Drawer
- [ ] Implement Modal
- [ ] Implement Notifications
- [ ] Implement Global Search
- [ ] Implement Authentication (OIDC). [Validating](https://datatracker.ietf.org/doc/html/rfc7519#section-7.2)
- [ ] Create Authorization (OAuth2) middleware
- [ ] Integrate with Dynatrace
- [ ] Integrate with GTM
- [ ] Integrate with Zen Desk
- [ ] Implement SCIM
- [ ] Create modules manifest
- [ ] Create api scaffolding
- [ ] Create api plugins architecture

### Installing

```
npm install --global commitizen cz-conventional-changelog standard snazzy standard-version plop pnpm
git clone https://github.com/looplex/turborepo
cd turborepo
npm install
```

### Plop recipes

For consistency and agility, we provide the following boilerplates for you to get your hands dirt as soon as possible:

- `application`: a [Next.js](https://nextjs.org) application
- `module`: a [Microbundle](https://github.com/developit/microbundle#readme) package
- _`api`_: a skeleton for creating APIs based on the railroad pattern with identification, authorization and global errors handles etc
- _`widget`_: a homepage widget

### Utilities

This turborepo has some additional tools already setup for you:

- [Commitizen](http://commitizen.github.io/cz-cli/) with conventional changelog to sanitize commit messages
- [Plop JS](https://plopjs.com/) to save time and keep consistency around the projects
- [Standard JS](https://standardjs.com/) for code linting and code formatting
- [Standard Version](https://github.com/conventional-changelog/standard-version#readme) to keep the CHANGELOG up-to-date

### Build

To build all apps and packages, run the following command:

```
npm run build
```

### Develop

To develop all apps and packages, run the following command:

```
npm run dev
```

### Test

To develop all apps and packages, run the following command:

```
npm run test
```

### Remote Caching

Turborepo can use a technique known as [Remote Caching (Beta)](https://turborepo.org/docs/core-concepts/remote-caching) to share cache artifacts across machines, enabling you to share build caches with your team and CI/CD pipelines.

By default, Turborepo will cache locally. To enable Remote Caching (Beta) you will need an account with Vercel. If you don't have an account you can [create one](https://vercel.com/signup), then enter the following commands:

```
cd turborepo
npx turbo login
```

This will authenticate the Turborepo CLI with your [Vercel account](https://vercel.com/docs/concepts/personal-accounts/overview).

Next, you can link your Turborepo to your Remote Cache by running the following command from the root of your turborepo:

```
npx turbo link
```

## Useful Links

### MobX-State-Tree
- [Welcome to MobX-State-Tree!](https://mobx-state-tree.js.org/intro/welcome)

### Jest
- [Next.js Configuration with SWC](https://nextjs.org/docs/testing#jest-and-react-testing-library)
- [Module Configuration](https://jestjs.io/docs/getting-started#using-babel)

### Playwright
- [Next.js end-to-end testing with Playwright](https://nextjs.org/docs/testing#playwright)

### Turborepo

- [Pipelines](https://turborepo.org/docs/core-concepts/pipelines)
- [Caching](https://turborepo.org/docs/core-concepts/caching)
- [Remote Caching (Beta)](https://turborepo.org/docs/core-concepts/remote-caching)
- [Scoped Tasks](https://turborepo.org/docs/core-concepts/scopes)
- [Configuration Options](https://turborepo.org/docs/reference/configuration)
- [CLI Usage](https://turborepo.org/docs/reference/command-line-reference)
