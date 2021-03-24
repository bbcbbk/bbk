# heroku-vless
Deploy VLESS server to heroku

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https://github.com/bbcbbk/bbk/tree/main)

# Vmess/VLESS Client Setup

| Connection Variables | Values |
| -------------------- | ------ |
| `Address` | yourAppName.herokuapp.com </br> Cloudflare Reverse Proxy IP |
| `SNI` | Same as Host |
| `AllowInsecure` | false |
| `Port` | 443 |
| `Host` | yourAppName.herokuapp.com </br> Cloudflare Reverse Proxy Domain Name |
| `Path` | /wo18cm?ed=2048 |
| `id` | Generate using UUID generator |
| `Flow` | null (Websocket do Not support Xtls)
| `encryption` | none |
| `Transport` | ws |
| `Tls` | Tls must open, otherwise you will be disconnected |

# Client Support Status

| Client | Status |
| ------ | ------ |
| `2dust V2RayN` </br> `2dust V2RayNG` | Vless+Ws+Tls |
| `OpenWrt SSRPlus` | Vless+Ws+Tls |
| `OpenWrt Passwall` | Vless+Ws+Tls |
| `QV2Ray` | Vless+Ws+Tls |

# Cloudflare Reverse Proxy Code

```
const SingleDay = 'yourAppName.herokuapp.com'
const DoubleDay = 'yourAppName.herokuapp.com'
addEventListener(
    "fetch",event => {
    
        let nd = new Date();
        if (nd.getDate()%2) {
            hostha = SingleDay
        } else {
            hostha = DoubleDay
        }
        
        let url=new URL(event.request.url);
        url.hostname= hostha;
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```

# Acknowledgments

- [Project V](https://github.com/v2ray/v2ray-core.git)
- [Project X](https://github.com/XTLS/Xray-core.git)
- [HeroKu](https://heroku.com)
- [heroku-vless](https://github.com/DanyTPG/heroku-vless.git)
- [Better Cloudflare IP](https://github.com/XIU2/CloudflareSpeedTest.git)
