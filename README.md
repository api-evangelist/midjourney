# midjourney (midjourney)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Midjourney is an independent research lab that produces an artificial intelligence program creating images from textual descriptions, accessible primarily through a Discord bot interface.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/midjourney/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/midjourney/refs/heads/main/apis.yml)

## Timestamps

- **Modified:** 2026-05-19

## APIs

### Midjourney Image Generation API

The Midjourney Image Generation API provides programmatic access to Midjourney's AI-powered image generation capabilities. Developers can submit text prompts to generate images, upscale selected outputs to higher resolutions, create variations of generated images, and use describe functionality to generate prompts from existing images.

- **Human URL:** [https://docs.midjourney.com/](https://docs.midjourney.com/)
- **Base URL:** `https://api.midjourney.com`

#### Tags

- AI
- Creative Tools
- Generative AI
- Image Generation
- Text to Image

#### Properties

- [Documentation](https://docs.midjourney.com/)
- [OpenAPI](openapi/midjourney-image-generation-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/midjourney-image-generation.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/midjourney-image-generation.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [AsyncAPI](asyncapi/midjourney-image-generation-asyncapi.yml) — [AsyncAPI Specification](https://www.asyncapi.com/docs/reference/specification/latest)
- [JSON Schema](json-schema/midjourney-image-generation-job-schema.json) — [JSON Schema](https://json-schema.org/specification)

### Midjourney Web Application

The Midjourney Web Application provides a browser-based interface for generating AI images using text prompts. Users can create images, explore a gallery of community creations, manage their generated image library, and access advanced features such as image editing, blending, and variation generation. The web application serves as the primary interface for interacting with Midjourney's generative AI models, complementing the original Discord-based experience with a dedicated creative workspace.

- **Human URL:** [https://www.midjourney.com/](https://www.midjourney.com/)
- **Base URL:** `https://api.example.com`

#### Tags

- AI
- Creative Tools
- Image Generation
- User Interface
- Web Application

#### Properties

- [Documentation](https://docs.midjourney.com/)
- [Postman Collection](collections/midjourney-image-generation.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/midjourney-image-generation.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Midjourney Discord Bot

The Midjourney Discord Bot is the original interface for accessing Midjourney's AI image generation service. Users interact with the bot through Discord slash commands such as /imagine, /blend, /describe, and /shorten to generate and manipulate AI-created images. The bot supports features including text-to-image generation, image upscaling, variation creation, and image blending, all within the Discord messaging platform.

- **Human URL:** [https://docs.midjourney.com/hc/en-us](https://docs.midjourney.com/hc/en-us)
- **Base URL:** `https://api.example.com`

#### Tags

- AI
- Bot
- Chat Interface
- Discord
- Image Generation

#### Properties

- [Documentation](https://docs.midjourney.com/hc/en-us)
- [Postman Collection](collections/midjourney-image-generation.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/midjourney-image-generation.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [GitHub Organization](https://github.com/midjourney)
- [LinkedIn](https://www.linkedin.com/company/midjourney)
- [JSON-LD](json-ld/midjourney-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
