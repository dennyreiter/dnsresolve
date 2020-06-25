# dnsresolve
Simple Home Assistant component to check DNS resolution as a binary sensor. I use this to make sure my DNS servers and Pi-Hole servers are all working. MOst of this is taken right out of Home Assistant Core, mostly the dnsip component switched up to return a binary sensor.

## Installation
1. Copy the `dnsresolve` folder to the `custom_components` folder in your Home Assistant configuration directory.
2. Add the following code in your `configuration.yaml` file under `binary_sensor:`:
```
  - platform: dnsresolve
    name: My DNS
    hostname: myip.opendns.org
    resolver: 192.168.0.8
```

## Configuration
| key              | required | type    | usage
|------------------|----------|---------|-----------------------------------------------------------------------------------|
| platform         | true     | string  | `dnsresolve`                              |
| name             | false    | string  | The name of your sensor. Defaults to `mydns`
| hostname         | false    | string  | The hostname to check. Defaults to `myip.opendns.org` |
| resolver         | false    | string  | DNS server you are checking. Defaults to `208.67.222.222` |

The defaults aren't much use except to make sure the component is working.  I set the hostname to one of my internal names, and the resolver to my DNS server that I want to check.  If the sensor returns false, that means that more than likely DNS is not working.

