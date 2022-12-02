# Fix for "flicker issues" on first load for projects based on the octopus capstone template

When deploying your capstone project to Vercel you might experience, that the page loads without styles first and the styling is applied in a second step after a second.
To prevent this annoying flickering effect, we recommend the following fix:

- If you didn't change your `_document.js` yet, simply replace it with the following code:

  ```
  import Document, {Html, Head, Main, NextScript} from "next/document";
  import {ServerStyleSheet} from "styled-components";

  class MyDocument extends Document {
      static async getInitialProps(ctx) {
          const sheet = new ServerStyleSheet();
          const originalRenderPage = ctx.renderPage;
          try {
              ctx.renderPage = () =>
              originalRenderPage({
                  enhanceApp: App => props => sheet.collectStyles(<App {...props} />),
                  enhanceComponent: Component => Component,
              });

              const initialProps = await Document.getInitialProps(ctx);

              return {
              ...initialProps,
              styles: [initialProps.styles, sheet.getStyleElement()],
              };
          } finally {
              sheet.seal();
          }
      }
      render() {
          return (
              <Html>
              <Head>
              <link
                  rel="icon"
                  href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>🐙</text></svg>"
              />
              </Head>
              <body>
              <Main />
              <NextScript />
              </body>
              </Html>
          );
      }
  }

  export default MyDocument;

  ```

- If you changed your `_document.js` already (e.g. to replace the app icon), please copy your changed JSX code into the `return` section of the code above.
- Additionally, we found two unneccessary npm-imports in the template. We did not find any issues with them yet, but to keep everything clean you could try to remove them by running the following command:

```
npm uninstall @babel/core babel-loader
```
