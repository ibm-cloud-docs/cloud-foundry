---

copyright:
  years: 2015, 2018
lastupdated: "2017-10-26"
subcollection: "Nodejs"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

# Enforce HTTPS on all pages in your application
{: #enforce_https}

When you run your application in {{site.data.keyword.Bluemix}} with the express framework, the following changes need to be made to enforce HTTPS instead of HTTP on all pages in your application.

```
var express = require("express");
var app = express();

app.enable('trust proxy');

app.use (function (req, res, next) {
  if (req.secure || process.env.BLUEMIX_REGION === undefined) {
    next();
  } else {
    console.log('redirecting to https');
    res.redirect('https://' + req.headers.host + req.url);
  }
});
```
