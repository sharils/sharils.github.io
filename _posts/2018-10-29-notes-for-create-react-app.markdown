---
layout: post
title:  "Notes for Create React App"
date:   2018-10-29 23:59:37
categories: jekyll update
---

# Notes for [Create React App][1]

- [Displaying Lint Output in the Editor][2]
- [Getting Started with Storybook][3]
- [Analyzing the Bundle Size][4]
- [Using HTTPS in Development][5]
- [Adding a CSS Modules Stylesheet][6]
- [CSS Grid Layout prefixing is disabled by default, but it will not strip manual prefixing. If you'd like to opt-in to CSS Grid prefixing, first familiarize yourself about its limitations.][7]
- [`<link rel="shortcut icon" href="%PUBLIC_URL%/favicon.ico">`][8]
- [`import('./moduleA') .then(({ moduleA }) => { // Use moduleA })`][9]
- [Adding Bootstrap][10]
- [Adding Relay][11]
- [Note: You must create custom environment variables beginning with REACT_APP][12]
- [Referencing Environment Variables in the HTML][13]
- [Adding Custom Environment Variables][14]
- [As the comment states, switching serviceWorker.unregister() to serviceWorker.register() will opt you in to using the service worker.][15]
- [We recommend to put the test files (or __tests__ folders) next to the code they are testing so that relative imports appear shorter.][16]
- [If your app uses a browser API that you need to mock in your tests or if you just need a global setup before running your tests, add a src/setupTests.js to your project.][17]
- [Debugging Tests][18]
- [Proxying API Requests in Development][19]
- [Generating Dynamic <meta> Tags on the Server][20]
- [Injecting Data from the Server into the Page][21]
- [.env.staging][22], REACT_APP_API_URL, env-cmd
- [Firebase][23], [GitHub Pages][24], [Heroku][25], [Netlify][26], Now, S3, Surge
- If you're ready to extract a component from your project so other people can use it, we recommend moving it to a separate directory outside of your project and then using a tool like nwb to prepare it for publishing.
- [Pre-Rendering into Static HTML Files][27]
- [Advanced Configuration][28]: BROWSER, HOST, PORT, HTTPS, PUBLIC_URL, CI, REACT_EDITOR, CHOKIDAR_USEPOLLING, GENERATE_SOURCEMAP, NODE_PATH, INLINE_RUNTIME_CHUNK
- [instead of ejecting we recommend to fork react-scripts][29]

[1]: https://facebook.github.io/create-react-app/docs/getting-started
[2]: https://facebook.github.io/create-react-app/docs/setting-up-your-editor#displaying-lint-output-in-the-editor
[3]: https://facebook.github.io/create-react-app/docs/developing-components-in-isolation#getting-started-with-storybook
[4]: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size
[5]: https://facebook.github.io/create-react-app/docs/using-https-in-development
[6]: https://facebook.github.io/create-react-app/docs/adding-a-css-modules-stylesheet
[7]: https://facebook.github.io/create-react-app/docs/post-processing-css
[8]: https://facebook.github.io/create-react-app/docs/using-the-public-folder
[9]: https://facebook.github.io/create-react-app/docs/code-splitting
[10]: https://facebook.github.io/create-react-app/docs/adding-bootstrap
[11]: https://facebook.github.io/create-react-app/docs/adding-relay
[12]: https://facebook.github.io/create-react-app/docs/adding-custom-environment-variables
[13]: https://facebook.github.io/create-react-app/docs/adding-custom-environment-variables#referencing-environment-variables-in-the-html
[14]: https://facebook.github.io/create-react-app/docs/adding-custom-environment-variables#adding-development-environment-variables-in-env
[15]: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app
[16]: https://facebook.github.io/create-react-app/docs/running-tests#filename-conventions
[17]: https://facebook.github.io/create-react-app/docs/running-tests#initializing-test-environment
[18]: https://facebook.github.io/create-react-app/docs/debugging-tests
[19]: https://facebook.github.io/create-react-app/docs/proxying-api-requests-in-development
[20]: https://facebook.github.io/create-react-app/docs/title-and-meta-tags#generating-dynamic-meta-tags-on-the-server
[21]: https://facebook.github.io/create-react-app/docs/title-and-meta-tags#injecting-data-from-the-server-into-the-page
[22]: https://facebook.github.io/create-react-app/docs/deployment#customizing-environment-variables-for-arbitrary-build-environments
[23]: https://facebook.github.io/create-react-app/docs/deployment#firebase-https-firebasegooglecom
[24]: https://facebook.github.io/create-react-app/docs/deployment#github-pages-https-pagesgithubcom
[25]: https://facebook.github.io/create-react-app/docs/deployment#heroku-https-wwwherokucom
[26]: https://facebook.github.io/create-react-app/docs/deployment#netlify-https-wwwnetlifycom
[27]: https://facebook.github.io/create-react-app/docs/pre-rendering-into-static-html-files
[28]: https://facebook.github.io/create-react-app/docs/advanced-configuration
[29]: https://facebook.github.io/create-react-app/docs/alternatives-to-ejecting
