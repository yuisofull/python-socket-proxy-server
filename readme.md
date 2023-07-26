# Web Proxy Server with Caching and Time-based Access Control

This is a Python web proxy server that provides caching functionality, time-based access control, and also works as an HTTP server for serving static files. The proxy server allows clients to access web resources through it, and it caches the responses from web servers to improve response time for subsequent requests. Additionally, the proxy server can limit access based on specified time ranges and serve static files when appropriate.

## Requirements

- Python 3.x
- `config.ini` file with cache time, whitelist URLs, and time restriction settings

## Installation

1. Clone the repository or download the `proxy.py` script and `config.ini` file to your machine.

2. Ensure you have Python 3.x installed.

3. Modify the `config.ini` file to set the cache time, whitelist URLs, and time restriction settings according to your requirements.

## Configuration

The `config.ini` file contains the following parameters:

- `cache_time`: The time, in seconds, to cache responses from web servers. (e.g., `cache_time = 900` for 15 minutes)
- `whitelisting`: Comma-separated list of URLs that are allowed to access through the proxy.
- `time`: The time range during which access is allowed (format: `HH-HH`, e.g., `8-20` for 8 AM to 8 PM).
- `timeout`: The timeout value in seconds for connections to web servers.
- `enabling_whitelist`: A boolean flag to enable or disable URL whitelisting (set to `True` to enable).
- `time_restriction`: A boolean flag to enable or disable time-based access control (set to `True` to enable).

## Usage

Run the proxy server by executing the following command:

```bash
python proxy.py <HOST> <PORT>
```

Replace `<HOST>` and `<PORT>` with the desired host and port number on which you want the proxy server to listen for incoming connections.

## Features

### Caching

- The proxy server caches responses from web servers for a configurable duration (`cache_time` in `config.ini`). Subsequent requests for the same resource within the cache duration will be served from the cache, reducing response time and improving performance.

### Time-Based Access Control

- The proxy server can restrict access to specific time ranges (`time` in `config.ini`). Only requests received during the specified time range will be allowed, and requests outside this range will receive a "403 Forbidden" response.

### Whitelisting

- Optionally, the proxy server can enforce URL whitelisting (`whitelisting` in `config.ini`). If enabled (`enabling_whitelist = True` in `config.ini`), only requests to URLs listed in the whitelist will be allowed, and requests to other URLs will receive a "403 Forbidden" response.

### HTTP Server for Static Files

The proxy server can work as an HTTP server with the following additional features:

#### Submit Feature

To save a message in a server text file, use the following `curl` command:

```bash
curl -X POST -d "HELLO WORLD" <url>/submit
```

#### Upload Feature

To upload a file and save it under a specified file name, use the following `curl` command:

```bash
curl -H "File-Name: <file name>" --data-binary @<file path> <url>
```

#### Download Feature

To download an uploaded file, use the following `curl` command:

```bash
curl <url>/<uploaded file name>
```

Alternatively, you can open your browser and go to `<url>/<uploaded file name>` to download the file.

## Example Usage

1. Start the proxy server by running:

```bash
python proxy.py 127.0.0.1 8888
```

2. Set your web browser or application to use the proxy server at `127.0.0.1:8888`.

3. Access web resources as usual through your browser or application. The proxy server will handle caching, access control, and also serve static files with the additional features described above.

4. Modify the `config.ini` file to customize cache time, whitelist URLs, and time restrictions according to your needs.

## Notes

- The proxy server supports `GET`, `HEAD`, `POST`, and additional features such as `SUBMIT` and `UPLOAD`. Unsupported methods will receive a "403 Forbidden" response.
- The proxy server will close the connection after each request-response cycle.

Please feel free to customize and use this web proxy server to meet your specific requirements. If you have any questions or need further assistance, don't hesitate to reach out. Happy proxying!