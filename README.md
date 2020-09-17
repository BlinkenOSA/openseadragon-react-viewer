# OpenSeadragonViewer

![Image of OpenSeadragon React Viewer](https://i.imgur.com/6PbYcbE.jpg)

A React wrapper component around the OpenSeadragon viewer. Feed `OpenSeadragonViewer` a IIIF manifest URL, and it will render an OpenSeadragon viewer with:

- FontAwesome toolbar icons
- A tile source dropdown navigation menu
- Thumbnails navigation
- Download options
- Support for deep linking, and saving URL parameters

## Installation and usage

```
yarn add openseadragon-react-viewer

// And peer dependencies
yarn add @emotion/core openseadragon
```

Then use it in your app:

```
import React from 'react';
import { OpenSeadragonViewer } from "openseadragon-react-viewer"

const App = () => {
  // Get your manifest from somewhere
  const manifestUrl = "https://some-manifest-url-here.json";

  // Options to show/hide extra UI features in the viewer
  // height(in pixels) option is default to 800 for wide-screens and 500 for narrow-screens
  // All other options default to 'true'
  const options = {
    showDropdown: true,
    showThumbnails: false,
    showToolbar: true,
    deepLinking: true,
    height: 800,
  };

  return (
    <OpenSeadragonViewer manifestUrl={manifestUrl} options={options} />
  );
}

export default App;
```

### Options / Props

Props the component accepts:

- `manifestUrl` - {string} IIIF manifest url (required)
- `options` - {object} An options config object whether to use custom features or OpenSeadragon features

See the [Styleguidist docs](https://samvera-labs.github.io/openseadragon-react-viewer/) for full configuration options.

### Custom styling

CSS class names are provided for elements which allow for custom styling overrides.

For example, to change the style of the title in the viewer, in your CSS define something like:

```
.osrv-work-title {
  color: green;
  font-family: "Verdana";
  font-size: 2rem;
}
```

### Getting help

If you need help with `openseadragon-react-viewer`, [submit an issue](https://github.com/samvera-labs/openseadragon-react-viewer/issues).

### Cross-site Requests

** This info pulled from the [Diva.js](https://github.com/ddmal/diva.js) package**

You may receive an error that looks something like this:

```bash
XMLHttpRequest cannot load http://example.com/demo/imagefiles.json. No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'http://localhost:8000' is therefore not allowed access.
```

This is a security precaution that all browsers use to prevent cross-site request forgeries. If you receive this message it is because your `manifestUrl` prop and the server used to serve the OpenSeadragon React Viewer are not at the same server address.

To fix this you must ensure that the OpenSeadragon React Viewer host's React application, and the location pointed to by the `manifestUrl` prop are being served by the same server, or you must create an exception using the Access-Control-Allow-Origin header on your server to explicitly white-list the `manifestUrl` location.

## Development

### Prerequisites

You'll need to have `node` installed on your local machine. Also, preferably `yarn` installed as well. You can check either with:

```
node --version
yarn --version
```

### Installing

1. Clone or fork this repository

2. Install project dependencies

```
yarn install
```

### Start development environment

To spin up the development environment run:

```
yarn dev
```

Visit http://localhost:10001/ in your browser.

See `rollup.config.js` for development and packaging configuration details. Development environment runs from a `UMD` bundled file, which is saved to the `/public` folder for local development.

### Running the tests

To run unit tests, with a full coverage report:

```
yarn test
```

To run tests in `watch` mode:

```
yarn test:watch
```

### Styleguidist development

Styleguidist, in addition to providing documentation, also offers an isolated development environment. To run the environment and test it out:

```
yarn dev
// or
yarn styleguide
```

To build a static html version of the docs (which Github pages uses), run:

```
yarn styleguide:build
```

## Deployment

To deploy your forked version of this repo, run:

```
yarn build
```

This will create CommoneJS, ES Module, and UMD distribution files located in the `/dist/` directory.

## Documentation

See the [Styleguidist docs](https://samvera-labs.github.io/openseadragon-react-viewer/) for documentation on the components.

## Contributing

If you're working on PR for this project, branch off `master` and create a feature branch. Submit your PR to https://github.com/samvera-labs/openseadragon-react-viewer. You're awesome. Thanks!

## Code style

Use [Prettier](https://prettier.io/).

`.prettierrc` file contains current project coding style settings.

## Built With

- [OpenSeadragon](https://openseadragon.github.io/) - OpenSeadragon
- [IIIF](https://iiif.io/) - IIIF International Image Interoperability Framework
- [React](https://reactjs.org/) - JavaScript component library
- [Rollup](https://rollupjs.org/) - JavaScript Bundler
- [Jest](https://jestjs.io/) - Testing framework
- [Emotion](https://emotion.sh/) - CSS in JS

## Authors

- **Adam J. Arling** - UI Developer - [Northwestern University](https://github.com/adamjarling)
- **Divya R. Katpally** - Front-end Developer - [Northwestern University](https://github.com/katdivyareddy10)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
