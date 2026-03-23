---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/dashboard-configurations/kibana-dashboard-integration/kibana-auth-proxy-setup-and-configuration
---

# Kibana - Auth Proxy Setup & Configuration

## Overview

The **Kibana Auth Proxy** is like a security gateway for Kibana.

* It is a layer between users and Kibana to make sure only authorised people can get in.
* It checks each request using DIGIT’s login system before allowing access.

You can easily customise how it works by setting environment variables (for example, which port it uses, which login service it talks to, and which websites are allowed).

It’s ready to install using Helm charts, which makes deployment fast.\
Technically, it’s built using **Node.js** and works as a “reverse proxy” — meaning all traffic goes through it before reaching Kibana.

## Setup & Configuration

The service relies on environment variables defined in envVariables for key configuration. These variables include:

The variables enable users to customise the proxy’s behaviour and handlers:

| Variable                                 | Purpose                                                 |
| ---------------------------------------- | ------------------------------------------------------- |
| **SERVER\_PORT**                         | Port on which the proxy runs                            |
| **EGOV\_USER\_HOST** / **\_SEARCH**      | Defines the host and endpoint for the external auth API |
| **KIBANA\_HOST** / **\_BASE\_PATH**      | URL and base path of the Kibana server                  |
| **KIBANA\_ACCEPTED\_CONTEXT\_UI\_PATHS** | Valid referer paths for access control                  |
| **KIBANA\_ACCEPTED\_DOMAIN\_NAME**       | Domain(s) allowed to access Kibana                      |
| **KIBANA\_EXCLUDE\_URL\_PATTERNS**       | URL patterns that bypass authentication                 |

These settings can be overridden with environment variables during deployment.

## Deployment Configuration

The deployment details given in the [Helm Charts repo here](https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/health-services/auth-proxy) ensure the auth-proxy is easily deployed into your infrastructure.

### Build Details

Auth-Proxy: auth-proxy-urlencoded-fix-aad9a5959c-23

