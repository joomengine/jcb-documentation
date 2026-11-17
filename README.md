# Joomla Component Builder Documentation

Learn to build and maintain Joomla extensions with **Joomla Component Builder (JCB)**. This repository brings together practical guides, feature references, and written lessons that accompany the JCB video tutorials.

The documentation covers setting up a development environment, planning components, building administrator and site views, defining fields and validation, retrieving data with Dynamic Gets, working with templates and layouts, adding custom code, and compiling and maintaining extensions. It is written for developers with some PHP and Joomla experience.

## Choose your language

Start with the onboarding guide in your preferred language, or use its topic index to find a specific lesson.

| Language | Start here | Topic index | Coverage |
| --- | --- | --- | --- |
| English (`en-GB`) | [Onboarding guide](./english/README.md) | [Browse topics](./english/index.md) | Source documentation |
| Persian / فارسی (`fa-IR`) | [راهنمای شروع](./persian/README.md) | [فهرست مطالب](./persian/index.md) | Partial translation; more chapters and review welcome |

Translations grow through community contributions. If a chapter is missing in your language, use the English documentation while it is being translated. Some lessons describe earlier Joomla or JCB releases; check the version and editing notes on the page when following a tutorial.

## Help translate the documentation

We would love to make these guides available to everyone who uses Joomla. You can translate a single page, review an existing translation, or help complete a language. You do not need to translate the entire documentation to contribute.

Work is already under way on [Persian additions in PR #35](https://github.com/joomengine/jcb-documentation/pull/35) and a [French draft in PR #36](https://github.com/joomengine/jcb-documentation/pull/36). Check the [open pull requests](https://github.com/joomengine/jcb-documentation/pulls) before starting so you can coordinate with other contributors.

### Languages needing translations

The checklist follows the [Joomla 6 language-pack directory](https://downloads.joomla.org/language-packs/translations-joomla6) and the broader [Joomla Core Language Team roster](https://volunteers.joomla.org/teams/joomla-cms-language-team), including regional and script variants. Joomla language-pack availability varies by release, and the roster also includes languages seeking maintainers. Checked on 17 November 2026.

The languages below still need merged JCB documentation. French already has a draft PR, as noted above. Language names remain unlinked until reading pages are available.

| Language | Joomla language tag |
| --- | --- |
| Afrikaans | `af-ZA` |
| Albanian | `sq-AL` |
| Amharic | `am-ET` |
| Arabic Unitag | `ar-AA` |
| Armenian | `hy-AM` |
| Basque | `eu-ES` |
| Belarusian | `be-BY` |
| Bengali, Bangladesh | `bn-BD` |
| Bosnian | `bs-BA` |
| Bulgarian | `bg-BG` |
| Catalan | `ca-ES` |
| Chinese, Simplified | `zh-CN` |
| Chinese, Traditional | `zh-TW` |
| Croatian | `hr-HR` |
| Czech | `cs-CZ` |
| Danish | `da-DK` |
| Dari | `fa-AF` |
| Dutch | `nl-NL` |
| Dzongkha | `dz-BT` |
| Esperanto | `eo-XX` |
| Estonian | `et-EE` |
| Finnish | `fi-FI` |
| Flemish | `nl-BE` |
| French | `fr-FR` |
| French, Canada | `fr-CA` |
| Galician | `gl-ES` |
| Georgian | `ka-GE` |
| German | `de-DE` |
| German, Austria | `de-AT` |
| German, Liechtenstein | `de-LI` |
| German, Luxembourg | `de-LU` |
| German, Switzerland | `de-CH` |
| Greek | `el-GR` |
| Hebrew | `he-IL` |
| Hindi, India | `hi-IN` |
| Hungarian | `hu-HU` |
| Indonesian, Bahasa Indonesia | `id-ID` |
| Irish | `ga-IE` |
| Italian | `it-IT` |
| Japanese | `ja-JP` |
| Kazakh | `kk-KZ` |
| Khmer | `km-KH` |
| Korean | `ko-KR` |
| Laotian | `lo-LA` |
| Latvian | `lv-LV` |
| Lithuanian | `lt-LT` |
| Macedonian | `mk-MK` |
| Malay | `ms-MY` |
| Montenegrin | `cnr-ME` |
| Ndonga | `ng-NA` |
| Norwegian Bokmål | `nb-NO` |
| Norwegian Nynorsk | `nn-NO` |
| Pashto Afghanistan | `ps-AF` |
| Polish | `pl-PL` |
| Portuguese, Brazil | `pt-BR` |
| Portuguese, Portugal | `pt-PT` |
| Réunion Creole French | `fr-RE` |
| Romanian | `ro-RO` |
| Russian | `ru-RU` |
| Serbian, Cyrillic | `sr-RS` |
| Serbian, Latin | `sr-YU` |
| Sinhala | `si-LK` |
| Slovak | `sk-SK` |
| Slovenian | `sl-SI` |
| Spanish | `es-ES` |
| Spanish, Colombia | `es-CO` |
| Swahili | `sw-KE` |
| Swedish | `sv-SE` |
| Syriac, East | `sy-IQ` |
| Tamil, India | `ta-IN` |
| Thai | `th-TH` |
| Turkish | `tr-TR` |
| Turkmen | `tk-TM` |
| Ukrainian | `uk-UA` |
| Urdu, Pakistan | `ur-PK` |
| Uyghur | `ug-CN` |
| Vietnamese | `vi-VN` |
| Welsh | `cy-GB` |

The English source above is available to all English readers. Contributions adapting it for Joomla's regional English variants are also welcome:

| Regional English variant | Joomla language tag |
| --- | --- |
| English, Australia | `en-AU` |
| English, Canada | `en-CA` |
| English, New Zealand | `en-NZ` |
| English, USA | `en-US` |

Do you speak a language that is not listed? You are welcome to propose it in a pull request too.

### Open a translation pull request

1. Fork this repository and create a branch from `master`.
2. Use the [English documentation](./english/README.md) as your source. Add translated pages to the appropriate language folder, following the existing `english/` and `persian/` structure. For a new language or regional variant, state its language name and Joomla language tag in your PR.
3. Keep the source filenames and folder structure so pages remain easy to compare. Translate the prose while preserving code, commands, placeholders, and technical identifiers. Check that navigation links lead to existing translated pages; link to the English page when its translation is not yet available.
4. Include a translated `README.md` and `index.md` as entry points when starting a new language. State which pages are translated and which still need work, and check the rendered Markdown and links.
5. Open a pull request describing the language and pages you added or reviewed. Once a language has usable entry pages, add its reading links to **Choose your language** above and update the translation checklist as needed.

Improvements to existing translations and the English source are welcome too. For questions about terminology or coordination, [open an issue](https://github.com/joomengine/jcb-documentation/issues) or join the [JCB community discussions](https://github.com/orgs/joomengine/discussions).
