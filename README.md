# Asuswrt-Merlin DDNS for CloudFlare

This is a custom shell script for Asuswrt-Merlin router firmware to update DDNS via CloudFlare for both IPv4 and IPv6.

## Setup

1. Add an `A record` in [CloudFlare](https://www.cloudflare.com/) for your domain. IP for the record can be anything since the script will overwrite it later anyway. Optionally add an `AAAA record` if you want to use IPv6.

1. Download [ddns-start](ddns-start) script and modify the following variables with your own settings:

   | Variable      | Description                                                                                                                                                                                                                                                                                     |
   | ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `API_TOKEN`   | Your API Token generated from the [User Profile 'API Tokens' page](https://dash.cloudflare.com/profile/api-tokens). I recommend creating a token with minimal access to limit exposure:<br />**Permission**: Zone > DNS > EDIT<br />**Zone Resources**: Include > Specific Zone > \<your zone\> |
   | `ZONE_ID`     | Your Zone ID, hex16 string                                                                                                                                                                                                                                                                      |
   | `RECORD_NAME` | Your DNS record name, e.g. host.example.com                                                                                                                                                                                                                                                     |
   | `RECORD_TTL`  | TTL for the record in seconds, defaults to 1 (auto)                                                                                                                                                                                                                                             |
   | `UPDATE_IPv6` | Set it to `true` if you want the script to update the AAAA record. Make sure you have an `AAAA record` setup in CloudFlare as instructed in step 1. Defaults to `false`.                                                                                                                        |

1. SSH to your router and place `ddns-start` under `/jffs/scripts/`

1. Make sure it's executable `chmod +x /jffs/scripts/ddns-start`

1. Log into the router web UI

   1. Go to `Advanced Settings` > `WAN` > `DDNS`
   1. Set `Server` to `Custom`
   1. Click the `Apply` button

## References

- <https://github.com/RMerl/asuswrt-merlin.ng/wiki/Custom-DDNS>
- <https://github.com/RMerl/asuswrt-merlin.ng/wiki/User-scripts>
