# WariHash Public API 
This is a repository for WariHash's public API. The API allows anyone to setup a form where users can purchase hashing power and direct them to the stratum server of their choosing. Mining pools for example, could use this API to allow their customers to purchase and augment their hashing power. 

We provide direct API access, and also provide a library that can be integrated into websites that utilizes the API for easy integration. 

## Authentication

You will need to register an account with us, where you will be provided with an API token. 

## API's

get_bids - retreive bids

bid_make - use this to buy hashrate and get an invoice

get_configs - get_configs returns information about available algos, min/max durations for each segment (We may have to simplify or provide some functions for this part...) 

## Library

Work in Progress: We will provide you with a library that comes with pre-made forms that utilizes the API. The library can be used for easy integration into your platform, or can be used as a referece to implement more customized solutions.
