# CMS Rate Monitoring UI

A simple web application powered by [JSROOT](https://root.cern.ch/js/) and VueJS to browse CERN CMS HLT and L1 Trigger Rates.

Data source is the RateMon experimental API, exposing trigger rates plots made by the RateMon tools.

Interactive plots rendering

![](.meta/screen0.png)

Trigger Path selection

![](.meta/screen1.png)


## Public instances

A few development instances are currently running. Most stable one should be on [brandeis.cern.ch:8082](http://brandeis.cern.ch:8082) (you must be on CERN network or proxied through LXPLUS to access this host).

## Running

```bash
# Project setup
npm install
# Compiles and hot-reloads for development
npm run serve
# Compiles and minifies for production
npm run build
### Lints and fixes files
npm run lint
```

### Further references

[VueJS configuration reference](https://cli.vuejs.org/config/).
