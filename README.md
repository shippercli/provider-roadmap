# Provider Roadmap

## Goal

Broaden Shipper from a panel-focused deployment tool into a provider-agnostic deployment system that supports multiple infrastructure models.

## Current coverage

- Server control panels: Ploi, Laravel Forge, EasyPanel
- Shared hosting panels: cPanel
- Self-managed container app platforms: Coolify
- Prebuilt file deployment: [FTP / FTPS 1.0.0](https://github.com/shippercli/provider-ftp/releases/tag/v1.0.0) (hosting compatibility beta)

FTP/FTPS provides a file-transfer fallback for existing hosting. It does not execute commands, provision servers or manage runtimes, so generic SSH remains a separate gap. See the [verification matrix](https://github.com/shippercli/provider-gap-matrix#distribution-and-verification) for release evidence and limitations.

## Key gap

Current provider count overstates actual coverage breadth. Most existing providers cluster around the same deployment model: managed server panels.

## Roadmap principles

- Prefer coverage breadth over adding another similar panel
- Add one generic fallback provider early
- Design around a shared capability contract
- Mark feature support explicitly as supported, partial, or unsupported
- Keep provider packages independent

## Recommended rollout

### Phase 1: coverage foundation

1. SSH / Generic Server
2. Coolify (released; continue expanding verified coverage)
3. Vercel
4. Railway or Render

### Phase 2: modern app platforms

1. Fly.io
2. DigitalOcean App Platform
3. Dokku
4. Platform.sh

### Phase 3: orchestration and enterprise

1. Kubernetes
2. AWS-focused provider family
3. Google Cloud / Azure platform integrations

## Why these providers

### SSH / Generic Server

- Best provider-agnostic fallback
- Works across many VPS and dedicated server setups
- Reduces dependence on specific panels

### Coolify

- Expands coverage into self-hosted app-platform workflows
- Broad stack relevance
- Good fit for multi-service projects

### Vercel

- Covers frontend and edge-oriented deployments
- Adds strong fit for Next.js and static app workflows
- Broadens the product story beyond traditional servers

### Railway / Render

- Adds mainstream PaaS deployment model
- Useful for apps, workers, cron jobs, and managed services

## Prioritization matrix

| Provider | Coverage gain | Complexity | Strategic value | Priority |
| --- | --- | --- | --- | --- |
| SSH / Generic Server | High | Medium | High | P1 |
| Coolify | High | Medium | High | P1 |
| Vercel | High | Medium | High | P1 |
| Railway | High | Medium | High | P1 |
| Render | High | Medium | High | P1 |
| Fly.io | Medium | Medium | Medium | P2 |
| DigitalOcean App Platform | Medium | Medium | Medium | P2 |
| Dokku | Medium | Medium | Medium | P2 |
| Kubernetes | Very high | High | High | P3 |

## Packaging recommendation

- `provider-ssh`
- `provider-coolify`
- `provider-vercel`
- `provider-railway`
- `provider-render`

Each provider should remain its own package and repository.

## Success criteria

- Shipper no longer appears panel-specific
- Provider catalog spans at least five distinct deployment models
- Capability support is explicit per provider
- Documentation clearly separates core workflow from provider-specific behavior
