# WariHash Public API 
This is a repository that documents WariHash's public API. The API allows anyone to interface with WarihHash.

## Authentication

No authentiation is required to use the API.

## Available Endpoints

### GET /estimate_get/

Get an estimate on pricing for purchasing hashrate.

#### Parameters

    duration: (int) Duration (in minutes) to take the offer for

    hashrate: (int) hashrate to purchase

    hashrate_units: (char) units that hashrate is specified in (K, M, G, T, P for kilo, mega, giga, tera, and peta)

    mining_algo: (string) mining algorithm (sha256d, scrypt, ethash, handshake, or equihash-zcash)

    location: (string) location of miners to purchase from (NA West, NA East, EU West)

    limit_price [optional]: (decimal string) optional limit price specification

#### Returns

    matched_hashrate: (decimal string) matched hashrate

    matched_hashrate_units: units of hashrate for matched_hashrate

    total_payment_amount: (decimal_string) total payment amount in BTC

    average_price: (decimal string) average rate that you'd pay for, expressed with price_hash_units and price_time_units from get_configs/


#### Example

    curl 'https://api.warihash.com/estimate_get/?hashrate=30&hashrate_units=T&location=NA West&duration=180&minig_algo=sha256d'


### GET /get_configs/

Get various configurations for the WariHash site

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

#### Example

    curl 'https://api.warihash.com/get_configs/'
