# `nginx.rewrite` - ContEco

Nginx Rewrite implements a generic URL rewrite template using environment variables.
See `conteco.docs.overview` for more information on the ContEco ecosystem.

## Configuration Changes

The base image has the following configuration changes:
- Implementation of a generic service URL rewrite template
- custom entrypoint which generate the service specific config from the template prior to startup of Nginx

The environment variables are set in the service `environment` file. It consists of the absolute URL of the service and network internal service name.
```bash
location ${CONTECO_NGINX_CONF_LOCATION}/ {
  proxy_pass http://${CONTECO_NGINX_CONF_PROXY_PASS}/;
  rewrite ^${CONTECO_NGINX_CONF_LOCATION}/(.*) /$1 break;
}


```

## Tags

* 1.19.3
