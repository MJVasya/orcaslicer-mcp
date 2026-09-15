# Fork of MaxEllis/orcaslicer-mcp

This repository is a GitHub **fork** of [MaxEllis/orcaslicer-mcp](https://github.com/MaxEllis/orcaslicer-mcp) (`uvx orcaslicer-mcp`, stdio, Claude Desktop).

**The Grok.com changes are not in this tree.** They live in:

**https://github.com/MJVasya/grok-orca-connector**

That repo wraps the MaxEllis **Orca Remote API** (`:13130`) as **streamable HTTP MCP** and publishes it through a Cloudflare quick tunnel so **[grok.com Custom](https://grok.com/connectors)** can call tools. Grok.com cannot attach to stdio and cannot reach `127.0.0.1`.

```
Grok.com Custom  --HTTPS-->  https://xxxx.trycloudflare.com/mcp
                                  cloudflared quick tunnel
                                     :18783  host-rewrite bridge
                                     :18785  HTTP-MCP wrapper  (streamable HTTP)
                                     :13130  MaxEllis Orca Remote API
AD5X LAN :8898 stays on the printer network (not tunneled)
```

| | This fork (upstream package) | [grok-orca-connector](https://github.com/MJVasya/grok-orca-connector) |
|---|---|---|
| Transport | stdio (`uvx orcaslicer-mcp`) | **Streamable HTTP MCP** |
| Client | Claude Desktop / local agents | **grok.com Custom** |
| Reachability | localhost | Cloudflare quick tunnel |
| Printer | optional klipper-mcp companion | Flashforge AD5X LAN `ad5x_*` |

Keep this fork for `git fetch upstream` / PRs back to MaxEllis.
Run the Grok stack from **grok-orca-connector** (`start-orca-grok-stack` / `stop-orca-grok-stack`).

```bash
git remote add upstream https://github.com/MaxEllis/orcaslicer-mcp.git
git fetch upstream
git merge upstream/main
```
