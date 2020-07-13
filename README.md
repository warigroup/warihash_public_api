# WariHash Public API 
This is a repository that documents WariHash's public API. The API allows anyone to interface with WarihHash.

## Authentication

No authentiation is required to use the API.

## Available Endpoints

### GET /get_configs/

Get various configurations for the warihash site

#### Returns

    available_algos: (list of string) list of available mining algorithms in the market

    server_time: (string, ISO 8601 format) server time

    payment_vehicle: (string) payment vehicle for all mining markets (i.e, Bitcoin, BTC Testnet)

    mining algorithm name, i.e. sha256d: (dict of dict)

        hashrate_units: (char) hashrate units to use for the mining algorithm

        price_hash_units: (char) the units of hashrate that price is specified with (X in XHashes/sec/Y)

        price_time_units: (string) the units of time that price specified with (Y in YHashes/sec/Y, for example 'hour')

        location, i.e. US east, US west: (dict)

            proxy: (string) address of the proxy for miners to connect to

            hour/day: (dict) value is a dict specfied as below for either the "day" or the "hour" market

                duration_interval: (int) allowed interval of duration for this market in minutes

                duration_min: (int) minimum duration for this market in minutes

                duration_max: (int) maximum duration for this market in minutes

                hashrate_min: (int) minimum hashrate available for this market in hashrate_units, if no hashrate is available, will be None

                hashrate_max: (int) maximum hashrate available for this market in hashrate_units, if no hashrate is available, will be None

