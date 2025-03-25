---
layout: default
title: getting started
---

# Getting Started

This guide will help you get started building a progressive web app in no time. If you have any issues, take a look at the troubleshooting guide for potentail solutions. 

### 1. Environment Setup
Install Node.js for a development environment.

- If you don’t have Homebrew installed, install it first:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

- Once Homebrew is installed, use it to install Node.js:
```
brew install node
```

- Verify the installation:
```
node -v
npm -v
```

### 2. Install a code editor like VS Code.
An ide provides great tools and support when building and running the apps.

### 3. Create the app!
Use `create-react-app` or Vite for a faster, lightweight setup:

- substitute `your-app-name` with a name for your app i.e. financial-app

```
npx create-react-app your-app-name
cd your-app-name
npm start
```

#### Potential Problems
When running `npx create-react-app app-name` you may see dependency incompatibility issues like below and there are a few ways to resolve this:
```
npm error Found: react@19.0.0
npm error node_modules/react
npm error   react@"^19.0.0" from the root project
npm error
npm error Could not resolve dependency:
npm error peer react@"^18.0.0" from @testing-library/react@13.4.0
```
In the case above the dependency @testing-library/react@13.4.0 version expects a version of React that is compatible with ^18.0.0, but you are using React 19.0.0, which is not compatible with this peer dependency.

#### Potential Resolutions

1. **Solution 1:** Downgrade React to a Compatible Version. In the example above you can downgrade to v 18 as follows:
```
npm uninstall react react-dom
npm install react@18 react-dom@18
```
2. **Solution 2:** Update Testing Library:
```
npm info @testing-library/react versions

npm install @testing-library/react@<compatible-version>
```

### Pushing to Vercel Repository 

If you had an existing repository before creating a repository for vercel and want to continue to make changes to this one, you will need a way to merge those changes to the repository that deploys using vercel. You can do so as follows: 
 
 - Clone the repository that you configured through vercel locally:
`git clone git@github.com:frutas4caro/cathy-learning-vercel.git`

Navigate to root of this repository locally:
`cd cathy-learning-vercel`

Set the original repository as an upstream to the vercel repo:
`git remote add upstream https://github.com/frutas4caro/cathy-learning-platform.git`

Run a rebase - will take all upstream changes and place them on your local branch
`git rebase upstream/main`

Push your change to origin:
`git push origin main --force`