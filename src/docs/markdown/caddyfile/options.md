---
title: Global options (Caddyfile)
---

# Global options

The Caddyfile has a way for you to specify options that apply globally. Some options act as default values, while others customize the behavior of the Caddyfile [adapter](/docs/config-adapters).

The very top of your Caddyfile can be a **global options block**. This is a block that has no keys:

```
{
	...
}
```

There can only be one at most, and it must be the first block of the Caddyfile.

Possible options are:

```
{
	http_port  <port>
	https_port <port>
	order <dir1> first|last|[before|after <dir2>]
	storage <module_name> {
		<options...>
	}
	experimental_http3
	acme_ca <directory_url>
	email   <yours>
	admin   <addr>
}
```

- **http_port** is the port for the server to use for HTTP. For internal use only; does not change the HTTP port for clients. Default: 80
- **https_port** is the port for the server to use for HTTPS. For internal use only; does not change the HTTPS port for clients. Default: 443
- **order** sets or changes the standard order of HTTP handler directive(s). Can set directives to be `first` or `last`, or `before` or `after` another directive.
- **storage** configures Caddy's storage mechanism. Default: `file_system`
- **experimental_http3** enables experimental draft HTTP/3 support. Note that HTTP/3 is not a finished spec and client support is extremely limited. This option will go away in the future. _This option is not subject to compatibility promises._
- **acme_ca** specifies the URL to the ACME CA's directory. It is strongly recommended to set this to Let's Encrypt's [staging endpoint](https://letsencrypt.org/docs/staging-environment/) for testing or development. Default: Let's Encrypt's production endpoint.
- **email** is your email address. Mainly used when creating an ACME account with your CA, and is highly recommended in case there are problems with your certificates.
- **admin** customizes the admin API endpoint.
