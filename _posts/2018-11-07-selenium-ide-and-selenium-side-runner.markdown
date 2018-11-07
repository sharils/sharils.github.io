---
layout: post
title:  "Selenium IDE and Selenium SIDE Runner"
date:   2018-10-11 10:27:03
categories: jekyll update
---

## Selenium IDE

See [this][1] video for a tutorial to create a test. Remember to save the test as a `.side` file.

You can also install the Chrome version in Opera.

## Selenium SIDE Runner

### Install

Follow [the official installation guide][2] to install it.

In the same folder where `*.side` tests is saved to, `yarn add selenium-webdriver`.

If you want to run `*.side` tests in Mozilla Firefox, `brew cask info chromedriver`.

### Run `*.side` tests in Google Chrome

`brew cask info chromedriver` since we want to run `*.side` tests in Google Chrome.

In the same folder where `*.side` tests is saved to:

```sh
selenium-side-runner *.side
```

Headless mode:

```sh
selenium-side-runner --capabilities chromeOptions.args=[headless] *.side
```

Headless mode then visual mode if failed

```sh
if ! selenium-side-runner --capabilities chromeOptions.args=[headless] *.side; then
  selenium-side-runner *.side
fi
```

Configure via `.side.yml` file

```yml
capabilities:
  browserName: "chrome"
  chromeOptions:
    args:
      - headless
```

### Run `*.side` tests in Mozilla Firefox

`brew install geckodriver` since we want to run `*.side` tests in Mozilla Firefox.

In the same folder where `*.side` tests is saved to:

```sh
selenium-side-runner --capabilities 'browserName=firefox platform=MAC' *.side
```

Headless mode:

```sh
selenium-side-runner --capabilities 'browserName=firefox platform=MAC moz:firefoxOptions.args=[-headless]' *.side
```

Headless mode then visual mode if failed

```sh
if ! selenium-side-runner --capabilities 'browserName=firefox platform=MAC moz:firefoxOptions.args=[-headless]' *.side; then
  selenium-side-runner --capabilities 'browserName=firefox platform=MAC' *.side
fi
```

### Run `*.side` tests in Opera

`brew cask install operadriver` since we want to run `*.side` tests in Opera.

In the same folder where `*.side` tests is saved to:

```sh
selenium-side-runner --capabilities 'browserName=opera platform=MAC' *.side
```

[1]: https://www.youtube.com/watch?v=ZG3VFDMaAlk "Selenium IDE Demo A tutorial for beginners - YouTube"
[2]: https://www.npmjs.com/package/selenium-side-runner#installation "selenium-side-runner - npm"
