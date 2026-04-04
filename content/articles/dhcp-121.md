---
title: "DHCPv4 Option 121 Calculator"
date: 2025-10-18
categories: 
  - show-n-tell
tags: 
  - "dhcp"
  - "elm"
  - "networking"
---

* * *

Use [dhcp-121.devhuman.net](https://dhcp-121.devhuman.net) to calculate DHCP Classless Static Route option (option 121) values.

<!--more-->

## Static Routes

If your network consists of multiple subnets with devices communicating across them, then you could either install a static route in your primary router and have devices use that as their default gateway, or install the static route on each individual device.

Neither option is particularly attractive since, in the first case, you incur an unnecessary extra hop and in the second case, you lose centralised configuration management.

A third option specified in [IETF](https://www.ietf.org/)'s [RFC3442](https://datatracker.ietf.org/doc/html/rfc3442) is the Classless Static Route DHCPv4 option. Simply put, this adds a new DHCP option that allows servers to communicate a list of static routes mapping classless subnet routes to the routers that can route to them.

## Use My Calculator

While it is trivial (and maybe even fun) to construct DHCP Option 121 values by hand, my calculator website simplifies this process quite a bit.

You can find it here at [dhcp-121.devhuman.net](https://dhcp-121.devhuman.net). The source code is open-source and available on [GitHub](https://github.com/ananthb/dhcp-121). Let me know if you found it useful!

## Classless Static Routes via DHCP Option 121

The DHCP option value is specified as a compact, space-conscious hex-encoded string. It is convenient to think of each option value as a table with the first column being a classless subnet "destination" and the second one being that subnet router's IPv4 address.

| Destination | Router |
| --- | --- |
| 0.0.0.0/0 | 10.0.0.1 |
| 10.10.0.0/16 | 192.168.1.1 |

The option 121 value in hexadecimal for the above table works out to [`000a000001100a0a0000c0a80101`](https://dhcp-121.devhuman.net/#000a000001100a0a0000c0a80101
) .

### Let's Calculate Option 121 values

We start at the destination value in the first row with an output buffer of the empty string.

Output: `""`

1. The subnet mask of the destination represents the length of the destination network, which is encoded first in the output. We convert it to hex and add it to our output.

Output: `0`

2. To encode the destination network, we only encode the relevant bits of the network governed by its length. Since its length is zero, we can simply represent the network itself using 0.

Output: `00`

3. We now encode each octet of the router's IP address in hex and add it to our output string. `10.0.0.1` becomes `0a 00 00 01` (spaces added for clarity).

Output: `000a000001`

We repeat steps 1, 2, and 3 for each row of the table. Let's walk through the slightly more complex second row as well.

1. Convert the /16 subnet mask to hex (10) and add it to the output.

Output: `000a00000110`

2. Since the network length is 16 we are only concerned about the first 16 bits of the destination network, which in this case is 10.10. Converting that to hex gives us `0a0a` which we add to the output.

Output: `000a000001100a0a`

3. Finally, we encode the IP address in hex and add it to the output.

Output: `000a000001100a0a0000c0a80101`
