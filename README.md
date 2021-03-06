# mod_auth_cas

#### Table of Contents

1. [Overview](#overview)
2. [Module Description - What the module does and why it is useful](#module-description)
3. [Usage - Configuration options and additional functionality](#usage)
4. [Reference - An under-the-hood peek at what the module is doing and how](#reference)
5. [Limitations - OS compatibility, etc.](#limitations)
6. [Development - Guide for contributing to the module](#development)

## Overview

This module installs and configures `auth_cas` for Apache httpd. This module is
frequently used for single sign-on systems.

This module depends on `puppetlabs/apache` to install and configure Apache httpd.

## Usage

This module takes the following parameters, most of which are required.

### `certificatepath`

The path to the CA certificate used to validate the CAS server. Optional, defaults
to `/etc/pki/tls/certs/ca-bundle.crt` on Red Hat systems and `/etc/ssl/certs/ca-certificates.crt`
on Debian systems.

### `loginurl`

The URL to redirect users to when they attempt to access a CAS
protected resource and do not have an existing session. Required.

### `validateurl`

The URL to use when validating a ticket presented by a client in
the HTTP query string (ticket=...).

### `proxyvalidateurl`

The URL to use when performing a proxy validation. This is currently
an unimplemented feature, so setting this will have no effect.

### `path`

The path in which to install the CAS cache. Optional, defaults to `/cas`.

### `version`

The version of the CAS protocol to use. Optional, defaults to `1`.

### `debug`

Enable debug messages from mod_auth_cas. For this to work, you also need
to set `LogLevel Debug` in your global or vhost config. Optional,
defaults to `Off`.

### `validateserver`

Validate the SSL certificate of your CAS server. It is not recommended
to turn this off as it presents a security risk. Optional, defaults to `On`.

## Limitations

This module was written for use with CentOS 6 and Apache 2.2 and has since
been extended to work with CentOS 7 and Apache 2.4. It should work with
Debian too, but this hasn't been tested. Please let me know how you get on.

## Development

Feel free to send pull requests for new features. A lot of the possible CAS
configuration parameters are not (yet) implemented in this module because
they aren't used at my site.

Also welcome are modifications to support other distributions, or simply
a note to say it works as-is on your distro.
