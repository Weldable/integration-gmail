# Tech Debt — integration-gmail

## [2026-04-29] src/index.ts — monolithic file (~856 lines)
All actions and helpers are in a single file. Consider splitting into `src/actions/` modules (messages, threads, labels, drafts) as the action surface grows.
