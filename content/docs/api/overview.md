<h3 id="overview">Overview</h3>

Welcome to the Fider API documentation.

The Fider API allows you to manage Posts and other data within your Fider instance in a simple, programmatic way using conventional HTTP requests. The endpoints are intuitive and powerful, allowing you to easily make calls to retrieve information or to execute actions.

<strong>Version</strong>

The <strong>API v1</strong> was introduced on Fider `v0.16.0`. Make sure you're running the latest version of Fider to leverage the API. All Cloud users on `fider.io` are already on the latest so you can start using it right now.

<strong>Request</strong>

Allowed HTTP Verbs are GET, POST, PUT and DELETE. All data must be sent as JSON. 

Requests are sent to your Fider URL using the HTTP/HTTPS protocol.

<table>
  <tr>
    <th width="90">Hosting</th>
    <th>URL</th>
    <th width="110">Protocol</th>
  </tr>
  <tr>
    <td>Cloud</td>
    <td><code>https://&lt;subdomain&gt;.fider.io</code> or, if configured, your custom domain name (e.g: <code>https://feedback.yourcompany.com</code>)</td>
    <td>HTTPS only</td>
  </tr>
  <tr>
    <td>Self-Hosted</td>
    <td>The URL you have configured</td>
    <td>HTTP or HTTPS</td>
  </tr>
</table>

<strong>Response</strong>

Every response will be encoded with `application/json` and one of the following status code.

<table>
  <tr>
    <th width="150">Status Code</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>200 OK</td>
    <td>Fider has accepted and processed your request, no error was encountered.</td>
  </tr>
  <tr>
    <td>400 Bad Request</td>
    <td>Something is incorrect with your request, it might be missing a parameter or have an invalid value. See <strong>Error Messages</strong> below.</td>
  </tr>
  <tr>
    <td>403 Forbidden</td>
    <td>API Key is not present or not allowed to perform the operation</td>
  </tr>
  <tr>
    <td>404 Not Found</td>
    <td>The resource you're looking for doesn't exist.</td>
  </tr>
  <tr>
    <td>500 Internal Error</td>
    <td>This generally indicates a server-side problem on Fider and it cannot fulfill your request currently.</td>
  </tr>
</table>

<strong>Error Messages</strong>

Every `400 Bad Request` response contains a JSON payload with details of what went wrong. Each `error (object)` contains a `message (string)` describing what is incorrect and may also contain a `field (string)` property. If the error object doesn't contain the field, that's a general error message.

```
{
  "errors": [
    {
      "field": "color",
      "message": "'dark' is an invalid color."
    },
    {
      "message": "A tag named 'suggestion' already exists."
    }
  ]
}
```