A shell for testing [Eager](https://eager.io) apps.

How to use this:

1. Clone this repo.
1. Sign into [eager.io/developer](https://eager.io/developer) and create an app, pasting the repo URL you just cloned (e.g. [github.com/adamschwartz/EagerAppTestingShell](https://github.com/adamschwartz/EagerAppTestingShell)).
1. Import version `v1.0.0` using the following manually-specified JSON:

  ```JSON
  {"resources":{"head":[{"type":"script","contents":

  "window.EAGER_APP_TEST_URL = 'https://localhost/path/to/app-javascript-file.js';"

  },{"type":"script","contents":"setTimeout(function(){window.EAGER_APP_TEST_OPTIONS=INSTALL_OPTIONS;Eager.loadAsync.script=[window.EAGER_APP_TEST_URL];Eager.reloadBody()});"}]}}
  ```

  Make sure to change `https://localhost/path/to/app-javascript-file.js` to the local JS file you want to test. Note, the file must be served with SSL or you’ll need to disable the insecure content browser warning. [Vee](https://github.com/HubSpot/vee) can help with this.

1. Use `window.EAGER_APP_TEST_OPTIONS` inside your JS file to access the install page options JSON the user will fill out.
1. Finally, visit the install page in an unauthed browser session and set the preview URL to the site you want to test. You can also open the preview in a separate window.
