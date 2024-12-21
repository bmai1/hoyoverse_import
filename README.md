MacOS/IOS packet sniffing to get ZZZ gacha history url for rng.moe with [mitmproxy](https://github.com/mitmproxy/mitmproxy)
as an alternative to using Stream or some other app

### IOS Certificates

There is an IOS 18.1.1 bug where self-signed CA Certificates can't be trusted.

https://forums.developer.apple.com/forums/thread/764673

https://github.com/mitmproxy/mitmproxy/discussions/7194

To resolve, update to IOS 18.2 or reset device.

### Set up mitmproxy

1. Configure proxy for MacOS
  - System Preferences > Network > Wifi > Advanced > Proxies
  - Check HTTP and HTTPS
  - Server: 127.0.0.1:8080 (localhost port 8080)


2. Configure proxy for IOS
  - Settings > Wifi > HTTP Proxy > Manual
  - Server: Laptop IP Address (System Preferences > Network > Wifi)
  - Port: 8080


3. Start mitmproxy (defaults to port 8080): `mitmproxy --mode regular`

4. Install certificate on phone to decrypt HTTPS traffic
  - Open http://mitm.it on Safari
  - Settings > General > VPN & Device Management > Install mitmproxy 
  - Settings > General > About > Certificate Trust Settings > Trust mitmproxy
    - This step is very important, otherwise it can't decrypt HTTPS requests and will only display the CONNECT requests to HoYoverse


5. Flows should appear in terminal. Open ZZZ > Signals > Signal Details > Search History
6. Copy GET request beginning with `https://public-operation-nap-sg.hoyoverse.com/common/gacha_record/api/getGachaLog?` and ending with `&end_id=`
7. Paste into https://zzz.rng.moe/en/tracker/import

![Exclusive Channel - mai rng moe - 12_20_2024](https://github.com/user-attachments/assets/08a204d2-6818-4fcf-bd39-ec67c3326f1b)
