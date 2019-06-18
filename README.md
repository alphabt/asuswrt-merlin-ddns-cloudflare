# Asuswrt-Merlin DDNS for CloudFlare

This is a custom shell script for Asuswrt-Merlin router firmware to update DDNS via CloudFlare.

## Setup

1. Add an A record in [CloudFlare](https://www.cloudflare.com/) for your domain. IP for the record can be anything since the script will overwrite it later any way.

1. Download [ddns-start](ddns-start) script and modify the following variables with your own settings:

    `EMAIL` is your CloudFlare account email

    `APIKEY` is your API key

    `ZONEID` is your Zone ID, hex16 string

    `RECORDNAME` is your DNS record name, e.g. sub.example.com

    `RECORDTTL` is the TTL for the record in seconds, defaults to auto

1. SSH to your router and place `ddns-start` under `/jffs/scripts/`

1. Log into the router web UI

    1. Go to `Advanced Settings` > `WAN` > `DDNS`
    2. Set `Server` to `Custom`
    3. Click the `Apply` button

## References

- <https://github.com/RMerl/asuswrt-merlin/wiki/Custom-DDNS>
- <https://github.com/RMerl/asuswrt-merlin/wiki/User-scripts>
