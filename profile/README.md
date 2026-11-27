<a href="https://tenish.ai">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/tenishai/.github/main/profile/banner-dark.png">
    <img src="https://raw.githubusercontent.com/tenishai/.github/main/profile/banner-light.png" alt="Tenish: open-source software for running teams of AI agents" width="100%">
  </picture>
</a>

Run teams of AI agents on your own machines: memory that lasts across sessions, a gateway and broker that hand each agent only the credentials it needs, and a platform to deploy, watch and secure them. Mostly Python, MIT-licensed, and each piece runs on its own.

**[tenish.ai](https://tenish.ai)** · security reports to security@tenish.ai

**Start here:** to run the whole suite on a cluster, use [stack](https://github.com/tenishai/stack). To try one piece alone, open its repo and follow the Quickstart.

<!-- The diagram is an image because the GitHub mobile app shows Mermaid as source and
     does not resolve relative image paths here. Its source is profile/suite.mmd; after
     editing it, re-render both images with mermaid-cli and commit them:
       mmdc -i suite.mmd -o suite-light.png -t default -b white -s 2 -w 1000
       mmdc -i suite.mmd -o suite-dark.png -t dark -b '#0d1117' -s 2 -w 1000
     The banner PNGs come from banner-*.svg (rsvg-convert -w 2400, with Space Grotesk and
     IBM Plex Mono installed). -->
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/tenishai/.github/main/profile/suite-dark.png">
  <img src="https://raw.githubusercontent.com/tenishai/.github/main/profile/suite-light.png" alt="How the suite fits together: stack installs it onto gojira, which deploys and runs it, with noto watching and sero holding secrets. On gojira, kobo builds agents (daedalus) and deploys each one through gojira; agents remember with techne, call models through litellm and tools through liminal; liminal asks bab what an agent may do and fetches credentials from cabal, which routes tasks between agents." width="100%">
</picture>

### Agents

- **[techne](https://github.com/tenishai/techne)**: memory for agents in one local SQLite file. Hybrid keyword and vector recall, and self-maintenance that proposes knowledge for you to review rather than writing it unasked.
- **[cabal](https://github.com/tenishai/cabal)**: control plane, A2A broker and credential store. Every hop between agents gets a short-lived token narrowed to that hop.
- **[liminal](https://github.com/tenishai/liminal)**: MCP gateway. One connection per agent, many tool handlers behind it, credentials fetched per call.
- **[daedalus](https://github.com/tenishai/daedalus)**: agent construction kit. An agent is a directory; tool approval fails closed.

### Platform

- **[stack](https://github.com/tenishai/stack)**: one YAML file and `stack install` bring the suite up on a running gojira, in dependency order, and it is safe to re-run.
- **[kobo](https://github.com/tenishai/kobo)**: a web room to build an agent, deploy it in one click, then teach it and decide who and what it can reach.
- **[bab](https://github.com/tenishai/bab)**: allow, ask a person or deny for each tool call, on OpenFGA; a grant carries a one-hour credential.
- **[gojira](https://github.com/tenishai/gojira)**: opinionated GKE deploy platform; drift and rightsizing come back as pull requests.
- **[noto](https://github.com/tenishai/noto)**: observability for everything gojira deploys, on OpenTelemetry, Mimir, Loki, Tempo and Perses.
- **[sero](https://github.com/tenishai/sero)**: runs OpenBao and syncs its secrets to where workloads read them.
- **[litellm-deploy](https://github.com/tenishai/litellm-deploy)**: the model gateway deployment the stack installs.
