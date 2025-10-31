# ns8-copyparty

## Warning

- This is currently beta stage.
- Currently only the http/https and webdav protocols are provided.

This module provides [copyparty](https://github.com/9001/copyparty) for NethServer 8.

copyparty a file server with resumable uploads/downloads using any web browser

## Install

Instantiate the module with:
```
    add-module ghcr.io/epetersen-lab/copyparty:latest 1
```

The output of the command will return the instance name.
Output example:
```
    {"module_id": "copyparty1", "image_name": "copyparty", "image_url": "ghcr.io/epetersen-lab/copyparty:latest"}
```

## Configure

Let's assume that the copyparty instance is named `copyparty1`.

Launch `configure-module`, by setting the following parameters:

- `host`: Port used by the web-interface and streaming to players.
- `username`: Username for login to copyparty
- `password`: Password for login to copyparty
- `http2https`: Enable/Disable HTTP to HTTPS redirection
- `lets_encrypt`: Enable/Disable Let's Encrypt certificate

Example:
```
    api-cli run configure-module --agent module/copyparty1 --data - <<EOF
    {
      "host": "copyparty.example.com",
      "username": "copyparty",
      "password": "secret",
      "http2https": true,
      "lets_encrypt": false
    }
    EOF
```

The above command will:

- start and configure the copyparty instance
- set the username for logging into copyparty to 'copyparty'
- set the password for logging into copyparty to 'secret'
- enable the http2https redirection when accessing the instance
- disable to usage of a Let's Encrypt certificate

## Uninstall

To uninstall the instance:
```
    remove-module --no-preserve copyparty1
```
