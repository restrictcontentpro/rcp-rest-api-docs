# REST API - Introduction #

The [REST API add-on](https://restrictcontentpro.com/downloads/rest-api/) provides a complete RESTful JSON API for retrieving, updating, creating, and deleting membership data in Restrict Content Pro.

## Requirements ##

The Restrict Content Pro REST API depends on the WordPress REST API and will not function without it. It also has minimum version requirements for WordPress, PHP, and Restrict Content Pro.

* WordPress: 4.4 or later
* Restrict Content Pro: 2.5 or later
* PHP: 5.3 or later

## Endpoint ##

The RCP REST API is available at `/wp-json/rcp/`.

If the default `wp-json` endpoint has been changed, the `rcp` endpoint will respect that change, so adjust accordingly.

## Versioning ##

Each distinct version of the REST API is accessible via the `rcp` endpoint. Versions may be deprecated at anytime but at no time will breaking changes be implementing without incrementing the version number. Past versions are expected to be kept available for at least six months beyond the release of the proceeding version.

`
/wp-json/rcp/{version}/{route}
`

Example: `/wp-json/rcp/v1/{route}`

<aside class="notice">
	Current version: v1
</aside>

## Errors ##

The Restrict Content Pro REST API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The kitten requested is hidden for administrators only.
404 | Not Found -- The specified kitten could not be found.
405 | Method Not Allowed -- You tried to access a kitten with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
410 | Gone -- The kitten requested has been removed from our servers.
418 | I'm a teapot.
429 | Too Many Requests -- You're requesting too many kittens! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

## Authentication ##

The RCP REST API requires authenticating with a WordPress user account that has the necessary capabilities in order to view, modify, and delete information via the REST API.

Please see the [WordPress REST API Authentication documentation](https://developer.wordpress.org/rest-api/using-the-rest-api/authentication/) to instructions on how to authenticate with the API.
