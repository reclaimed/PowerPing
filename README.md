# PowerPing - Advanced Windows Ping 

[![](https://img.shields.io/badge/version-1.3.0-brightgreen.svg)]() [![Codacy Badge](https://api.codacy.com/project/badge/Grade/8017007ba00645b390013970e5b6df43)](https://www.codacy.com/app/Killeroo/PowerPing?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=Killeroo/PowerPing&amp;utm_campaign=Badge_Grade) [![Build status](https://ci.appveyor.com/api/projects/status/fq7jnpmlejm7jych?svg=true)](https://ci.appveyor.com/project/Killeroo/powerping) 

Small improved command line ICMP ping program lovingly inspired by windows and linux, written in C#.

![alt text](docs/screenshots/screenshot.png "PowerPing in action")

# Downloads
Stable versions can be downloaded [[here]](https://github.com/Killeroo/PowerPing/releases)

Nightly dev builds can be found [[here]](https://ci.appveyor.com/api/projects/killeroo/powerping/artifacts/build%2Fx64%2FPowerPing.exe?job=Platform%3A%20x64&branch=dev) ([x86](https://ci.appveyor.com/api/projects/killeroo/powerping/artifacts/build%2Fx86%2FPowerPing.exe?job=Platform%3A%20x86&branch=dev))



## Features

- Basic ping functionality
- Coloured output
- Display options
- [ICMP packet customisation](https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol#Control_messages)
- [Scanning](https://en.wikipedia.org/wiki/Ping_sweep)
- [Flooding](https://en.wikipedia.org/wiki/Ping_flood)
- [ICMP packet capture (/listen)](docs/screenshots/screenshot3.png)
- [IP location lookup](docs/screenshots/screenshot4.png)
- [Whois lookup](https://en.wikipedia.org/wiki/WHOIS)
- [Graphing](docs/screenshots/screenshot2.png)

_Future features:_

- [Traceroute](https://en.wikipedia.org/wiki/Traceroute)
- [Tunnelling](https://en.wikipedia.org/wiki/ICMP_tunnel)
- [IPv6/ICMPv6](https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol_version_6)

## Usage: 
     PowerPing [--?] | [--ex] | [--li] | [--whoami] | [--whois] | [--loc] | [--fl] | [--sc] |
               [--g] | [--cg] | [--t] [--4] [--rng] [--df] [--rb number] [--b number] 
               [--c number] [--w number] [-i number] [--in number] [--pt number] [--pc number]
               [--m "message"] [--s number] [--ti timing] [--sh] [--dm] [--ts] [--nc] [--input] [--sym] [--r]
               [--nt] [--q] [--res] [--ia] [--l number] [dp number] [--chk] target_name | target_address
               
## Arguments:
    Ping Options:
        --infinite   [--t]            Ping the target until stopped (Ctrl-C to stop)
        --ipv4       [--4]            Force using IPv4
        --random     [--rng]          Generates random ICMP message
        --dontfrag   [--df]           Set 'Don't Fragment' flag
        --buffer     [--rb]  number   Sets recieve buffer size (default is 5096)
        --beep       [--b]   number   Beep on timeout (1) or on reply (2)
        --count      [--c]   number   Number of pings to send
        --timeout    [--w]   number   Time to wait for reply (in milliseconds)
        --ttl        [--i]   number   Time To Live for packet
        --interval   [--in]  number   Interval between each ping (in milliseconds)
        --type       [--pt]  number   Use custom ICMP type
        --code       [--pc]  number   Use custom ICMP code value
        --size       [--s]   number   Set size of packet (overwrites packet message)
        --message    [--m]   message  Ping packet message
        --timing     [--ti]  timing   Timing levels:
                                            0 - Paranoid    4 - Nimble
                                            1 - Sneaky      5 - Speedy
                                            2 - Quiet       6 - Insane
                                            3 - Polite      7 - Random
    
    Display Options:
        --shorthand  [--sh]           Show less detailed replies
        --displaymsg [--dm]           Display ICMP message contents
        --timestamp  [--ts]           Display timestamp
        --nocolor    [--nc]           No colour
        --input                       Require user input
        --symbols    [--sym]          Renders replies and timeouts as ASCII symbols
        --request    [--r]            Show request packets
        --notimeouts [--nt]           Don't display timeout messages
        --quiet      [--q]            No output, only shows summary upon completion or exit
        --resolve    [--res]          Resolve hostname of address from DNS
        --inputaddr  [--ia]           Show input address instead of revolved one
        --checksum   [--chk]           Display checksum of packet
        --limit      [--l]   number   Limits output to just replies (0) or requests (1)
        --decimals   [--dp]  number   Num of decimal places to use (0 to 3)

    Features:
        --scan       [--sc]  address  Network scanning, specify range "127.0.0.1-55"
        --listen     [--li]  address  Listen for ICMP packets
        --flood      [--fl]  address  Send high volume of pings to address
        --graph      [--g]   address  Graph view
        --compact    [--cg]  address  Compact graph view
        --location   [--loc] address  Location info for an address
        --whois              address  Whois lookup for an address
        --whoami                      Location info for current host

    Others:
        --help       [--?]            Displays this help message
        --version    [--v]            Shows version and build information
        --examples   [--ex]           Shows example usage

## Examples:
     powerping 8.8.8.8                    -     Send ping to google DNS with default values (3000ms timeout, 5 pings)
     powerping github.com --w 500 --t     -     Send pings indefinitely to github.com with a 500ms timeout
     
     powerping 127.0.0.1 --m Meow         -     Send ping with packet message "Meow" to loopback address
     powerping 127.0.0.1 --pt 3 --pc 2    -     Send ping with ICMP type 3 (dest unreachable) and code 2
     
     powerping 8.8.8.8 /c 5 -w 500 --sh   -     Different argument switches (/, - or --) can be used in any combination
     powerping google.com /ti Paranoid    -     Sends using the 'Paranoid' timing option
     powerping google.com /ti 1           -     Same as above

## Screenshots

![alt text](docs/screenshots/screenshot1.png "Powerping's Graph view")
![alt text](docs/screenshots/screenshot2.png "Powerping Listening for ICMP activity")
![alt text](docs/screenshots/screenshot4.png "Powerping showing request packets and sending random ICMP data")

[More screenshots](docs/screenshots/)

## License

MIT License

Copyright (c) 2018 Matthew Carney <matthewcarney64@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

### Note: 
**Requires _Elevated Rights (Admininstrator)_ to Run**
