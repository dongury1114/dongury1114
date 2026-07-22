# Donggyu Lee

  **Founder & engineer at [DEN](https://theden.kr)** — an independent software studio in Seoul,
  South Korea.

  I build web services end to end and then run them: product, code, infrastructure, and the
  operations that keep them alive while I'm asleep.

  `72 processes` · `129 scheduled jobs` · `47,000+ orders fulfilled` · `5 domains` · self-hosted

  ---

  ### 📈 Replay Trader

  **[replay.flirtinghub.kr](https://replay.flirtinghub.kr)** — free, no sign-up · English / 한국어

  A market-replay training platform. It replays historical BTC/ETH minute data as if it were
  live, so you can practise reading a chart and placing orders without risking capital.
  Everything is paper trading — no order ever reaches an exchange.

  - **The future is withheld at a single choke point.** Bars past the replay cursor never
    reach the chart, the indicators or the order engine. Automated tests assert it.
  - **Binance USDⓈ-M perpetual mechanics** — isolated margin, funding, maker/taker fees,
    liquidation on wick touch, slippage on market fills.
  - **3.4M verified minute bars per symbol** with zero gaps, **136 automated tests**, and a
    public [specification](https://replay.flirtinghub.kr/spec) and
    [guide](https://replay.flirtinghub.kr/guide).

  `Next.js` `TypeScript` `Lightweight Charts™` `DuckDB` `node:sqlite`

  ---

  ### 🧰 Seller Ops

  **Seller Ops** is my shorthand for the machinery that runs a store *after* the sale is made —
  dispatch, inventory, pricing, reviews, ads, reconciliation. None of it has a user interface,
  nobody thanks you for it, and it is only ever noticed when it breaks.

  I run a storefront on Naver Smart Store, Korea's largest marketplace, almost entirely
  unattended — **~30 processes** handling **47,000+ orders from 38,000+ customers** since
  December 2025. What that actually takes:

  - **Exactly-once dispatch.** One paid order must produce exactly one delivery message and
    exactly one fulfilment mark. Neither zero nor two. Failed sends go to a queue that
    survives a restart, retries are idempotent, and anything that exhausts its retries pages
    a human rather than disappearing.
  - **Staying logged in.** The platform actively fingerprints automation. Sessions are kept
    warm on a timer, cookies are written atomically (rename-swap + fsync, so a kill signal
    can't leave half a credential on disk), and a heuristic *stops* renewing when it detects
    IP-level protection — retrying harder is exactly what turns a soft block into a lockout.
  - **Inventory that matches reality.** Stock is seat-based, and two subsystems disagreed on
    whether the account owner counts toward capacity. Reconciliation was additive-only, so
    dead stock accumulated invisibly. Both are now measured against the live source rather
    than a cached count, and the sync fails closed when it can't verify.
  - **Ad spend with a ceiling it can't argue with.** An hourly bid optimiser once overbid.
    It now runs under an absolute cap enforced by a separate watcher that shares no
    configuration with it — a guard the thing it guards cannot switch off.
  - **Append-only audit trails.** Money movements and message sends are journalled to
    append-only logs before the side effect, not after, so a crash mid-operation leaves
    evidence instead of ambiguity.

    append-only logs before the side effect, not after, so a crash mid-operation leaves
    evidence instead of ambiguity.

  ---

  ### 🚀 Operating services

  | Service | | |
  |---|---|---|
  | **[로또여지도 / Lotto Yeojido](https://lottoyeojido.com)** | Maps where Korea's winning lottery tickets were actually sold, from public draw data collected weekly | `Next.js` `SQLite` |
  | **[Flirter](https://flirter.kr)** | Dating-service distribution partner | `Node.js` `PM2` |
  | **[코루트 Koroot](https://koroot.theden.kr)** | Settlement guide for foreign residents in Korea — visas, public services, daily life | `Vite` monorepo |

  **In development**

  | | |
  |---|---|
  | **[쌤노트 / Ssamnote](https://ssamnote.theden.kr)** | Record-keeping for schoolteachers — the notes that don't belong in the official system but matter most when a parental complaint arrives. Private by default, exportable into an evidence pack |
  | **[moomoobio](https://moomoobio.com)** | B2B export marketplace for aesthetics products |

  ---

  ### ⚙️ How it actually runs

  Everything above is self-hosted on my own hardware — no managed platform.

  - **72 processes** supervised by PM2, **129 scheduled jobs**, **5 domains**
  - Exposed through a single **Cloudflare Tunnel**; no inbound ports
  - Health watchdogs, silent-failure wrappers and OOM guards that page me on **Telegram**
  - Commerce automation runs unattended: order dispatch, review replies, inventory
    reconciliation and price monitoring against competitors

  I design for silent failure, because I have been on the wrong end of it: a stale DNS record
  that took every site down for five days, a scheduled job that failed quietly for 98
  consecutive runs because one `cd` was missing, a fully green test suite that was happily
  passing a completely broken app. Every guard rail above exists because something taught me
  it was needed.

  ---

  ### 🛠 Stack

  ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
  ![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white)
  ![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
  ![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
  ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)

  ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
  ![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white)
  ![DuckDB](https://img.shields.io/badge/DuckDB-FFF000?style=flat-square&logo=duckdb&logoColor=black)
  ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
  ![PM2](https://img.shields.io/badge/PM2-2B037A?style=flat-square&logo=pm2&logoColor=white)
  ![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white)

  ---

  ### 📫 Contact

  **contact@theden.kr** — partnership, licensing and integration inquiries
  [theden.kr](https://theden.kr)
