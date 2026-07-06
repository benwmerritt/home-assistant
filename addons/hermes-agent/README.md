# Hermes Agent

Runs the official NousResearch Hermes Agent Docker image as a Home Assistant add-on and exposes a browser terminal through Home Assistant Ingress.

Hermes state is persisted in the add-on data directory under `/data/hermes`. The launcher sets `HERMES_HOME`, `HERMES_WRITE_SAFE_ROOT`, and the Hermes subprocess `PATH` to use that persisted location.

## First Setup

Open the Hermes sidebar panel after installing the add-on. From the terminal, run one of:

- `hermes setup --portal`
- `hermes setup`
- `hermes model`
- `hermes setup gateway`
- `hermes --tui`

The add-on can optionally start `hermes gateway run` in the background while the terminal remains available. For first setup, keep `start_gateway` disabled until Hermes is configured.

## Options

- `start_gateway`: Start the Hermes gateway automatically. Defaults off so first-run setup can happen from the terminal before the gateway starts.
- `gateway_allow_all_users`: Set `GATEWAY_ALLOW_ALL_USERS`. Keep this off unless you understand the exposure.
- `hass_url`: Home Assistant URL visible from inside the add-on. Defaults to the internal add-on network name. At startup the add-on always rewrites `http://homeassistant.local:8123` to `http://homeassistant:8123`, because mDNS `.local` names do not resolve from inside the add-on container.
- `hass_token`: Optional Home Assistant long-lived access token.
- `telegram_bot_token`: Optional Telegram bot token.
- `telegram_allowed_users`: Optional comma-separated Telegram user allowlist.

For a simple first run, leave secrets blank, open the terminal, and use Hermes' own setup flow.
