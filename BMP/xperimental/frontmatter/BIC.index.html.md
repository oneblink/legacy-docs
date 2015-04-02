# Template for Initial HTML

BIC v3, like other web apps, requires an initial HTML document in order to be initialised.
This HTML document was formerly provided entirely by the Mobility Platform, but this is an example of tight-coupling that makes it difficult to update BIC v3 without also updating the Mobility Platform.

## Template Format

It is now expected that new versions of BIC v3 supply their own initial HTML template. This template should have a filename extension that indicates the format.

Currently, the only supported format is [Mustache](http://mustache.github.io/), so we expect all templates to be named `index.mustache` or similar.

## Template Data

In order to transform the template into HTML, data needs to be provided by the Mobility Platform. In order for templates to be interchangeable, this data needs to be in a standardised structure.

Here is a JSON-formatted illustration of the data structure:

```json
{
  "_SERVER": {
    /* see the _SERVER section below  */
  },
  "answerSpace": {
    /* see the answerSpace section below */
  },
  "BIC": {
    /* see the BIC section below */
  }
}
```

### _SERVER

This is based on PHP's [$_SERVER](http://php.net/manual/en/reserved.variables.server.php) super global. Besides key names, however, there is nothing PHP-specific about this.

We explicitly do not make all $_SERVER values available, just the ones that are difficult to derive in JavaScript through other means. Further, the values are strictly sanitised, in order to avoid [Cross Site Scripting (XSS)](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)) vulnerabilities.

The complete list of available $_SERVER values is:

 - **HTTP_ACCEPT**
 - **HTTP_ACCEPT_CHARSET**
 - **HTTP_ACCEPT_ENCODING**
 - **HTTP_ACCEPT_LANGUAGE**
 - **HTTP_CONNECTION**
 - **HTTP_USER_AGENT**
 - **SERVER_PROTOCOL**
 - **HTTP_REFERER**
 - **REQUEST_URI**

If our sanitisation process is blocking legitimate values, or if these are insufficient for a legitimate purpose, then please let us know and we will discuss making necessary adjustments.

### answerSpace

This is based on the configuration of the current answerSpace, with the most useful being:

- **id**: a unique identifier for the answerSpace, currently numeric but we make no promises
- **name**: the unique name of the answerSpace, which is more reliable than "id"
- **displayName**: friendly-name of the answerSpace, defaults to "name" if empty
- **env**: list of client-accessible Environment Variable values
- **env_json**: as above, but formatted as a single JSON string
- **styleSheets_html**: single string containing CDN-corrected HTML for CSS to include, with BIC stylesheets first, followed by external CSS from the answerSpace Manager
- **scripts_html**: as above but for JavaScript, with BIC scripts first, followed by external JavaScript from the answerSpace Manager
- **styleSheet**: single string containing the CSS rules from the answerSpace Manager
- **appCache**: URL string for the AppCache manifest, but only when offlineMode is enabled
- **appCachePermalink**: as above, but available regardless of offlineMode

### BIC

This is based on the metadata for the current version of the BIC, as configured in the answerSpace.
