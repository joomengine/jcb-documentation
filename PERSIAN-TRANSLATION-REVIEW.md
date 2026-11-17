# Persian translation review

This checklist records improvements for the Persian documentation while [PR #35](https://github.com/joomengine/jcb-documentation/pull/35) is in progress. All four existing Persian files are also changed by that PR, so this review leaves those files to the contributor. Apply the recommendations in that branch rather than maintaining competing edits.

Review baseline: `master` at `9721dac0d22538423eb2db63a212a7d3f3ec2017` and PR #35 at `313cc2a3e66d2665a50d3f7421319b0dd73683db`.

## Translation assessment

The two translated feature pages already on `master` preserve the English instructions overall. The wording changes below improve technical precision; they do not require a wholesale rewrite. The Persian `README.md` and `index.md` on that baseline are still English copies. PR #35 translates them, so continue that work there.

## Preserve the complete index

- [ ] Retain all 94 level-three sections from [the English index](english/index.md). PR #35 currently retains only nine. Translate the complete contents without deleting the remaining navigation, table rows, video timestamps, or section links. Untranslated entries may remain in English until they are ready.
- [ ] Correct the two chapter ranges near the top of `persian/index.md`: “one through seventy-one” means chapters 1–71, and “six through seventy-one” means chapters 6–71. Use `فصل‌های اول تا هفتاد و یکم` and `فصل‌های ششم تا هفتاد و یکم`, respectively.
- [ ] Preserve the full video timelines and documentation-section lists. The current PR also shortens the Hello World and Field Types tables.
- [ ] Remove the closing guidance copied from the onboarding README, or adapt it to the index. Its references to Steps 1, 4, and 6 currently have no corresponding steps on that page.

## Keep navigation usable during translation

At the reviewed `master` baseline, 13 of the 16 local link occurrences in [the Persian Admin Views feature guide](persian/Features/JCB-Admin-Views.md) point to files that do not exist in the Persian directory. The entry pages have the same missing-target problem. The corresponding English files exist.

- [ ] Keep a Persian destination when that translated file exists in the contributor's branch.
- [ ] For a page that is not translated yet, link directly to its existing English counterpart. Retain a section fragment only after checking it against the destination heading.
- [ ] Recheck the completed branch, because PR #35 adds several translated pages and changes which links need an English fallback.
- [ ] Add a short reader-facing note explaining that links to untranslated lessons open the English version.

These examples refer to pages that are absent from the reviewed Persian branch:

| Link location | Missing destination | Working English fallback |
| --- | --- | --- |
| `persian/Features/JCB-Admin-Views.md` | `../Admin-Views.md` | `../../english/Admin-Views.md` |
| `persian/README.md` | `./JCB-Fields.md` | `../english/JCB-Fields.md` |
| `persian/index.md` | `./Field-Types.md` | `../english/Field-Types.md` |

Also correct these issues in the PR's `persian/index.md`:

- [ ] Change the community discussions URL from `https://github.org/orgs/joomengine/discussions` to <https://github.com/orgs/joomengine/discussions>.
- [ ] Close the missing backtick in the `_Sidebar.md` link label.
- [ ] Replace the Field Types fragment `#2-creating-field-types` with the actual destination fragment. For the current English page, this is `#2-views-field-types-and-fields`.

## Polish technical terminology

Use these terms consistently in the existing feature guide and the new translations. Keep literal code identifiers and interface labels where readers need to match them to the application.

| Meaning | Current wording in the feature guide | Suggested wording |
| --- | --- | --- |
| Code placeholders | `مکان‌نماهای کد` | `جای‌نگهدارهای کد` |
| Video timestamps | `زمان‌بندی‌ها` | `زمان‌های متناظر در ویدیو` |
| Layouts | `لایه‌ها` | `چیدمان‌ها` |
| Lowercase names | `نام‌های کوچک` | `نام‌هایی با حروف کوچک` |
| Lookup tables | `جداول جستجو` | `جداول مرجع (Lookup tables)` |

- [ ] In the naming instruction, explicitly retain both lowercase letters and underscore separators: `نام‌هایی با حروف کوچک و جداشده با زیرخط`.
- [ ] Use one consistent translation for Admin Views, such as `ویوهای مدیریتی`, throughout the related pages.
- [ ] Keep Markdown ordered-list markers in ASCII form (`1.`, `2.`, and so on). Persian numerals can appear in prose, but do not reliably create Markdown numbered lists.
- [ ] Remove the duplicated introductory sentence in `persian/Adding-Admin-Views-to-a-Component.md` about understanding the concepts before applying them.

## Final review before merging PR #35

- [ ] Compare every translated page with its English counterpart for missing instructions, changed numeric values, and altered code examples.
- [ ] Check all local file destinations and section fragments against the final branch tree, including English fallbacks.
- [ ] Preview the Markdown tables, numbered lists, and mixed Persian/code text.
- [ ] Confirm that all 94 index sections remain and that video timestamps and code examples retain their original values.

These are recommendations for the contributor's branch. Adding this checklist does not implement the translation or navigation fixes in PR #35.
