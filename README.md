![logo](./assets/files/fuge-logo.png)
> An execution environment for micro service development with Node.js

# fuge.io
This repo contains the documentation website for [fuge][]. This documentation is available at
[fuge.io][] or can be run locally by cloning this repo and following the steps below.

## Run Locally
After cloning, you will need to get dependencies via npm:

```
npm i
```

Next simply build and serve to port `8000` using:

```
npm run start
```

## Contributing
Fuge and its docs are __open projects__ and encourage participation. If you feel you can help in
any way, be it with examples, extra testing, tutorials, or new features please be our guest.

Please make all content changes in the [/src/pages][] folder. All changes are built just before we
redeploy the site so you only need to include changes in your PR. Upon your PR being accepted your
changes will be deployed.

Please see our [contribute][] page for more information.

## License
Copyright Peter Elger and other contributors, Licensed under [MIT][].

[MIT]: ./LICENSE
[/src/pages]: ./src/pages
[contribute]: ./src/pages/contribute/index.md
[fuge]: https://www.npmjs.com/package/fuge
[fuge.io]: http://fuge.io
[Metalsmith]: http://metalsmith.io
