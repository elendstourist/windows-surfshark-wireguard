# Intro

This is a simple script that generates wireguard client config files for surfshark

You just need to `curl` and `jq`.

I'm using this to generate wireguard-configs on windows because i don't like surfshark client.



# How to use
To use this file:
1. copy `config.json.sample` into `config.json`
2. replace `config.json` values with your account values. Normally user your "email" and "password" that you use on your official client on Android, iOS, or web, not specially OpenVpn username and password
3. run `gen_wg_config.bash`

## usage

```shell
Usage: gen_wg_config.bash [-h]
   -g ignore generating profile files
   -n renew tokens
   -r regenerate the server conf files
   -Z clear settings, keys and server profile files
```

# Caveates

Please consider following caveates

## Your private/public key expires

As the date of writing this, each key pair expires in around 6 days so you need to rerun
the script every now and then.

I suggest to run it in crontab every day, and with `-g` parameter.

## Sometimes checking if public key is peresent fails

If you are not able to use the generated config files, there might be a chance that
there is an unhandleded corner case in `wg_check_pubkey` function. I suggest you to 
run the scring using `-f` parameter to force the script to register the key pair 
without chekcing if it exists.

# TODO

- implement refresh token
- generate luci configuration
