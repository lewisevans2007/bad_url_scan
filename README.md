# Bad url scan

A simple bad URL scanner for JavaScript

This firewall has over 50 bad URLs that are commonly used in attacks.

## Installation

```bash
npm install bad_url_scan
```

## Usage

````javascript
const scan = require("bad_url_scan");

scan("https://example.com/admin"); // Returns true

scan("https://example.com/blogs/my_trip.html"); // Returns false
````

## Example usage

Here is an example of a web server that uses this package to scan URLs:

```javascript
app.get('/', (req, res) => {
    const url = req.query.url;
    const bad = scan(url); // Returns true if the URL is bad
    if (bad) {
        res.send("Forbidden");
    } else {
        res.send("Hello World")
    }
});
```

If you want to allow a URL that is classed as bad, you can make a ignore list to ignore certain URLs:

```javascript
scan("https://example.com/results/database", ["results/database"]); // Returns false

scan("https://example.com/admin", ["results/database"]); // Returns true
```

## Licence

This project is licenced under GNU General Public Licence Version 3.0. See [LICENCE](LICENCE) for more information.