# SemaphoreCI Notifier

Browser extension to send browser notifications when the build finishes on Semaphore CI. This extension supports both Semaphore classic and 2.0.

- [Chrome webstore](https://chrome.google.com/webstore/detail/semaphore-ci-notifier/fidjidielhnphocjcnbccipbjikemnpl)
- [Firefox Addon](https://addons.mozilla.org/firefox/addon/semaphore-ci-notifier/)

![Logo](media/semaphore-ci-small-tile.png)

## Features

- Use modern Promise-based `browser.*` APIs [webextension-polyfill][link-webext-polyfill].
- [Auto-syncing options](#auto-syncing-options).
- [Auto-publishing](#publishing) with auto-versioning and support for manual releases.
- [Extensive configuration documentation](#configuration).

This extension has been generated with [otlmn/browser-extension-template](https://github.com/notlmn/browser-extension-template).

### Publishing

It's possible to publish to both the Chrome Web Store and Mozilla Addons at once by creating these ENV variables:

1. `CLIENT_ID`, `CLIENT_SECRET`, and `REFRESH_TOKEN` from [Google APIs][link-cws-keys].
1. `WEB_EXT_API_KEY`, and `WEB_EXT_API_SECRET` from [AMO][link-amo-keys].

And then running:

```sh
npm run release
```

This will:

1. Build the extension
1. Create a version number based on the current UTC time, like [`19.6.16.428`](https://github.com/fregante/daily-version) and sets it in the manifest.json
1. Deploy it to both stores

#### Auto-publishing

Thanks to the included [GitHub Action Workflows](.github/workflows), if you set up those ENVs in the repo's Settings, the deployment will automatically happen:

- on a schedule, by default [every week](.github/workflows/deploy-automatic.yml) (but only if there are any new commits in the last tag)
- manually, by clicking ["Run workflow"](https://github.blog/changelog/2020-07-06-github-actions-manual-triggers-with-workflow_dispatch/) in the Actions tab.

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

[link-webext-polyfill]: https://github.com/mozilla/webextension-polyfill
[link-cws-keys]: https://github.com/DrewML/chrome-webstore-upload/blob/master/How%20to%20generate%20Google%20API%20keys.md
[link-amo-keys]: https://addons.mozilla.org/en-US/developers/addon/api/key
