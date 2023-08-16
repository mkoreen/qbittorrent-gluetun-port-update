# qBittorrent Gluetun port update

Docker container to automatically update qBittorrent's listening port from Gluetun.

## Setup

Connect your qBittorent container and this container to Gluetun. If you are using docker-compose for everything, this means `network-mode: service:gluetun`. Refer to the Gluetun Wiki for more information.

### Environment Variables

| Variable                     | Default      | Example                        | Description                                                                                                                                                                |
|------------------------------|--------------|--------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `QBITTORRENT_WEBUI_HOST`     | `127.0.0.1`  | `192.168.1.10`                 | IP Address where the qBittorrent WebUI is hosted. This should probably never change.                                                                                       |
| `QBITTORRENT_WEBUI_PORT`     | `8080`       | `5392`                         | Port the qBittorrent WebUI is running on. This is configurable in the qBittorrent container. Note that this is the port *inside* the container, not the one forwarded out. |
| `QBITTORRENT_WEBUI_USERNAME` | `admin`      | `technosam`                    | Username to log into the qBittorrent WebUI.                                                                                                                                |
| `QBITTORRENT_WEBUI_PASSWORD` | `adminadmin` | `correct-horse-battery-staple` | Password to log into the qBittorrent WebUI.                                                                                                                                |
| `GLUETUN_CONTROL_HOST`       | `127.0.0.1`  | `192.168.1.11`                 | IP Address where the Gluetun control server is hosted. This should probably never change.                                                                                  |
| `GLUETUN_CONTROL_PORT`       | `8000`       | `6921`                         | Port the Gluetun control server is running on. Note that this is the port *inside* the container, not the one forwarded out.                                               |
| `INITIAL_DELAY_SEC`          | `10`         | `30`                           | Time in seconds to wait before making the first attempt to update the port.                                                                                                |
| `CHECK_INTERVAL_SEC`         | `60`         | `600`                          | Time in seconds to wait before checking each subsequent time.                                                                                                              |
| `ERROR_INTERVAL_SEC`         | `5`          | `3`                            | Time in seconds to wait before checking again if an error occurred.                                                                                                        |
| `ERROR_INTERVAL_COUNT`       | `5`          | `10`                           | Number of times an error can be encountered before waiting `CHECK_INTERVAL_SECONDS` instead. This will prevent a permanent error state from blowing up logs.               |
