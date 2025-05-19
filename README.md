# Blog UI Library

> **Note:** This project is for personal use only and is not intended for production environments.

## Introduction

Blog UI Library is a collection of reusable, customizable components designed specifically for [Svelte](https://svelte.dev/) projects using [Tailwind CSS](https://tailwindcss.com/).

## Installation

To install the library in your Svelte project, run the following command:

```sh
npm install https://github.com/filip-melka/blog-ui-library/releases/download/v0.0.2/blog-ui-library-0.0.2.tgz
```

## Releases

You can check current releases [here](https://github.com/filip-melka/blog-ui-library/releases).

## 🚀 Local Development

### Prerequisites

Ensure you have Node.js and npm installed on your system.

### Installation

Clone the repository and install dependencies:

```sh
git clone https://github.com/filip-melka/blog-ui-library.git
cd blog-ui-library
npm install
```

## 📖 Previewing Components

To explore and test the components using Storybook, run:

```sh
npm run storybook
```

## 📦 Building and Packaging

To manually build and package the library, use the following commands:

```sh
npm run build
npm pack
```

This will generate a build of the library and create a tarball package for distribution.

## 🚀 Automated Publishing

The `publish-release.yml` GitHub Action handles automated building, packaging, and publishing of new releases.

### Releasing a New Version

To publish a new release, follow these steps:

1. Ensure your code is committed and pushed to the `master` branch:

```sh
git push origin master
```

2. Create and push a version tag:

```sh
git tag v1.0.0
git push origin v1.0.0
```

This triggers the GitHub Action to automatically build, package, and publish the new release.
