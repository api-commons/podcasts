# Podcasts

The common podcast vocabulary -- the shows people subscribe to and the episodes they publish -- distilled from the APIs that already exist. Music has its own context. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Podcasts, Podcasting, Podcast Hosting, Podcast, Audio, Spoken Word in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| show | 13 | 11 | id 82%, name 82%, description 64%, author 55% | podcasts 7, shows 6, podcast 2 |
| episode | 11 | 9 | id 100%, description 89%, name 89%, duration 78%, audio_url 67%, show_id 56% | episodes 11 |

Cohort: 88 providers with harvested OpenAPI, 13 crosswalks. Of the providers exposing a show: 38% create, 85% list, 69% fetch, 15% update, 15% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- An episode agrees on title, description, duration, the audio URL and the show it belongs to -- the RSS enclosure model every podcast API inherits, because every podcast is an RSS feed first.
- A show agrees on title, description and author.

## Measured against the standard

The census reads what providers publish. Where the domain has a standard, the standard's own
definition is read as one more voice: how much of the measured core it defines, and what it
defines that no provider in the cohort publishes. Crosswalks are in [standards/](standards).

| Standard | Concept | Core defined by the standard | Fields only the standard has |
| --- | --- | ---: | ---: |
| [schemaorg-30.1](https://github.com/schemaorg/schemaorg/tree/v30.1) | `episode` | 67% | 124 |
| [schemaorg-30.1](https://github.com/schemaorg/schemaorg/tree/v30.1) | `show` | 75% | 118 |

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- Podcasts, shows and podcast feeds are one concept, published as `/shows`.
- Audio streaming of music is music's.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
