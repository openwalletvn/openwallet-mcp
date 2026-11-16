# OpenWallet MCP

## Local repo layout

Sibling repos share the same parent folder:

| Repo | Relative path from this repo | GitHub (`openwalletvn/…`) |
|------|------------------------------|---------------------------|
| web | `../openwallet-web` | `openwallet-web` |
| api | `../openwallet-api` | `openwallet-api` |
| mcp (this) | `.` | `openwallet-mcp` |
| data (v2) | `../openwallet-data` | `openwallet-data` |
| api v2 | `../openwallet-api-v2` | `openwallet-api-v2` |
| mcp v2 | `../openwallet-mcp-v2` | `openwallet-mcp-v2` |

When asked to "edit local web repo" → work in `../openwallet-web`. "edit local api repo" → work in `../openwallet-api`.

`../api` is an older duplicate clone of `openwallet-api`. It still holds the API's `.env.local` / `.dev.vars` and a stash, so don't delete it until those are moved.

v2 (plan 001 in `openwallet-data/.claude/plans/`) is built next to v1; v1 (this repo, `openwallet-api`, `openwallet-web`) stays in production until the switch.

## Shipping

- A push to `main` deploys production (this repo: Cloudflare Worker via GitHub Actions; web: Vercel). `main` requires a pull request in web; open one rather than bypassing the rule.
- Vercel skips the production build when the same commit was already built as a preview, or starts it late. Check with `vercel ls openwallet` that a Production deployment is Ready.
