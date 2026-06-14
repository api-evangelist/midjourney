---
title: Midjourney GraphQL Schema
description: Conceptual GraphQL schema for Midjourney's AI image generation capabilities, covering job lifecycle, prompt configuration, image results, Discord integration, and subscription/usage tracking.
---

# Midjourney GraphQL Schema

## Overview

Midjourney is an AI image generation platform accessible via Discord bot commands, a web application, and an emerging official API. This conceptual GraphQL schema represents the full surface area of Midjourney's capabilities: submitting generation jobs, controlling prompt parameters, retrieving image results, managing Discord channel context, and tracking subscription usage.

The schema is derived from Midjourney's public documentation at [docs.midjourney.com](https://docs.midjourney.com/), community-documented patterns from the Discord-based workflow, and the structure of Midjourney's forthcoming official API.

## Schema File

- [midjourney-schema.graphql](midjourney-schema.graphql)

## Type Summary

### Job Types

| Type | Description |
|---|---|
| `Job` | Core entity representing any generation job with status, prompt, parameters, and result |
| `JobID` | Strongly-typed wrapper for a job's unique identifier and short code |
| `JobType` | Enum of job categories: TEXT_TO_IMAGE, VARIATION, UPSCALE, REMIX, BLEND, DESCRIBE, SHORTEN, etc. |
| `TextToImage` | A text-prompt-driven image generation job |
| `Variation` | A variation job derived from a parent image result |
| `Upscale` | An upscale job increasing resolution of a selected image variant |
| `Remix` | A remix job regenerating an image with a modified prompt |
| `Blend` | A blend job combining multiple source images |
| `Describe` | A describe job generating prompt suggestions from an uploaded image |
| `Shorten` | A shorten job condensing a long prompt to its most impactful tokens |

### Prompt and Parameter Types

| Type | Description |
|---|---|
| `Prompt` | Full prompt including text content and optional image URL references |
| `TextPrompt` | The textual component of a Midjourney prompt with token estimates |
| `ParameterSet` | Complete set of generation parameters attached to a prompt |
| `AspectRatio` | Enum of supported aspect ratio presets (1:1, 16:9, 4:3, etc.) |
| `ModelVersion` | Enum of Midjourney model versions (V4, V5, V5.1, V5.2, V6, V6.1, Niji variants) |
| `StyleVersion` | Enum of style sub-versions (DEFAULT, RAW, CUTE, EXPRESSIVE, ORIGINAL, SCENIC) |
| `Quality` | Enum controlling render detail vs. generation time (QUARTER, HALF, BASE, HIGH) |
| `Stylize` | Stylize parameter (0–1000) for Midjourney's aesthetic influence |
| `Chaos` | Chaos parameter (0–100) for variation between grid results |
| `NoParam` | Negative prompt exclusion terms via --no flag |
| `Tile` | Flag enabling seamless tiling pattern generation |
| `Turbo` | Flag for fastest generation mode at higher GPU cost |
| `Relax` | Flag for slow generation consuming no fast hours |
| `Raw` | Flag disabling default Midjourney aesthetic post-processing |
| `ImageWeight` | Image-prompt blending weight (0.5–2.0) |
| `SeedValue` | Seed for reproducible generation results |
| `Stop` | Partial completion stop parameter (10–100 percent) |
| `Repeat` | Repeat count for multi-run jobs from a single prompt |
| `NijiMode` | Enum for Niji anime-style sub-modes |

### Image Result Types

| Type | Description |
|---|---|
| `ImageResult` | Output of a completed generation job including grid and variants |
| `ImageURL` | CDN-hosted URL for a generated or source image |
| `ImageGrid` | The 2x2 grid image produced by a standard generation |
| `ImageWidth` | Pixel width wrapper for a generated image |
| `ImageHeight` | Pixel height wrapper for a generated image |
| `ImageVariant` | A single variant extracted from an image grid |
| `UpscaleResult` | High-resolution result of an upscale operation |

### Discord Integration Types

| Type | Description |
|---|---|
| `DiscordChannel` | A Discord channel used for Midjourney bot interactions |
| `DiscordMessage` | A Discord message produced by or sent to the Midjourney bot |
| `DiscordGuild` | A Discord server where the Midjourney bot is active |
| `WebhookMessage` | A webhook-delivered event payload from Midjourney |
| `MessageEmbed` | An embed object within a Discord message |
| `MessageAttachment` | A file attachment in a Discord message |

### Policy and Access Types

| Type | Description |
|---|---|
| `ContentPolicy` | Configuration governing what Midjourney will generate |
| `ImageRating` | Enum for content safety ratings (SAFE, SENSITIVE, RESTRICTED, BLOCKED) |
| `APIKey` | A Midjourney API authentication key with scopes and expiry |
| `Token` | An OAuth or session access token |
| `BotToken` | A Discord bot token for bot-mode API access |

### Rate Limiting and Queue Types

| Type | Description |
|---|---|
| `TaskQueue` | Queue position and estimated wait for generation jobs |
| `RateLimit` | Rate limit metadata including remaining quota and reset time |

### Subscription and Usage Types

| Type | Description |
|---|---|
| `SubscriptionTier` | Enum of subscription plans (FREE, BASIC, STANDARD, PRO, MEGA) |
| `SubscriptionTierDetail` | Full subscription plan details with entitlements and pricing |
| `FastHour` | Monthly fast-hour credit balance |
| `RelaxMode` | Relax mode availability and queue time |
| `Usage` | Aggregate usage statistics for a user |
| `UsageRecord` | A single job's contribution to usage tracking |
| `MonthlyUsage` | Aggregated totals for a calendar month |

## Root Operations

### Queries

- `job(id)` — Retrieve a specific generation job by ID
- `jobs(status, jobType, limit, offset)` — List jobs for the authenticated user
- `taskQueue` — Current queue state and estimated wait
- `rateLimit(resource)` — Rate limit status for an endpoint
- `usage` — Aggregate usage summary for the authenticated user
- `monthlyUsage(year, month)` — Monthly usage breakdown
- `fastHours` — Current fast-hour balance
- `relaxMode` — Relax mode availability
- `subscription` — Active subscription tier and entitlements
- `apiKeys` — List API keys for the authenticated user
- `contentPolicy` — Current content policy rules
- `upscaleResult(jobId)` — Retrieve an upscale result
- `discordGuilds` — List Discord guilds with active bot
- `discordChannel(channelId)` — Get a specific channel

### Mutations

- `createTextToImage(prompt, ...)` — Submit a text-to-image generation job
- `createVariation(parentJobId, variantIndex, ...)` — Create an image variation
- `createUpscale(parentJobId, variantIndex, ...)` — Upscale an image variant
- `createRemix(parentJobId, newPrompt, ...)` — Remix with a modified prompt
- `createBlend(imageURLs, dimensions)` — Blend multiple images
- `createDescribe(imageURL)` — Generate prompts from an image
- `createShorten(prompt)` — Shorten a long prompt
- `cancelJob(jobId)` — Cancel a queued or running job
- `createAPIKey(name, scopes)` — Create a new API key
- `revokeAPIKey(keyId)` — Revoke an existing API key

### Subscriptions

- `jobStatusUpdated(jobId)` — Real-time status updates for a specific job
- `userJobEvents` — All job events for the authenticated user
- `queuePositionChanged` — Queue position changes

## Notes

Midjourney does not yet publish an official GraphQL or REST API as of mid-2026. The primary interaction surface remains Discord slash commands (`/imagine`, `/blend`, `/describe`, `/shorten`) and the web application at midjourney.com. An official API has been announced and is in limited beta. This schema is a conceptual representation suitable for planning integrations, generating mock servers, or documenting expected API surface area once the official API is generally available.

Key Midjourney-specific concepts reflected in this schema:

- **Fast Hours** — GPU time purchased via subscription, consumed by turbo and fast-mode jobs
- **Relax Mode** — Unlimited generation at lower priority, consuming no fast hours
- **Job Grid** — Standard generations produce a 2x2 grid of image variants
- **Upscaling** — Selecting one grid variant for higher-resolution rendering
- **Seed Reproducibility** — Seeds allow near-identical regeneration of prior results
- **Chaos** — Controls diversity within a generation batch
- **Stylize** — Midjourney's aesthetic influence on prompt interpretation
