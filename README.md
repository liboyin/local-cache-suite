# Local Cache Suite

A collection of cache/mirror services to run locally

## APT cache

Define in `/etc/apt/apt.conf.d/01proxy`:

```
Acquire::http::Proxy "<server_ip>:3142"
```

## PyPI mirror

Define in `$HOME/.pip/pip.conf`:

```
index-url = <server_ip>:3141/root/pypi/+simple/
trusted-host = <server_ip>
```
