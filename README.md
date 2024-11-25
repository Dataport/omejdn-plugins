# MERLOT specific plugins for the [Omejdn server](https://github.com/Fraunhofer-AISEC/omejdn-server)
This repository contains plugins that are used within the MERLOT project to achieve the usage of Omejdn as a DAPS authentication server for use with EDC connectors.

**Warning: The plugins in this repository may contain endpoints that are not secured by any means of authentication. These endpoints may be dangerous in production and must never be exposed to the Internet!**

## Structure

    ├── plugins
    │   ├── connector_api    # basic API plugin that adds (unauthorized!) endpoints for easy creation/deletion/retrieval of a new DAPS certificate
    ├── scripts              # scripts internally used by the plugins

## Endpoints

The following endpoints are made available by the connector API plugin:


| Endpoint         | Description                                                                                                              |
|------------------|--------------------------------------------------------------------------------------------------------------------------|
| POST /api/v1/connectors/add       | Given a payload containing a client_name and did, generate a new certificate and onboard it to the DAPS service. Returns the certificate details.  |
| GET /api/v1/connectors/details/:client_id | Returns the stored attributes corresponding to that client_id                                                     |
| POST /api/v1/connectors/details | Given a single client_id or client_name or a list of one of them, return the corresponding stored attributes. The client_id takes prevalence over client_name in the request if both are specified.  |

