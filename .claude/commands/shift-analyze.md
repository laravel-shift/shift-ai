# Shift Analyze

Determine the current Laravel major version from `composer.json` and guide the user toward upgrading if they're not on Laravel 13 yet.

## Steps

1. Read `composer.json` from the project root.

2. Find the `laravel/framework` entry under `require`. The version constraint will look like `^12.0`, `~11.0`, `12.*`, or similar. Extract the **major version number** — the leading integer before the first dot.

3. If the major version is **13 or higher**, tell the user their app is already on Laravel 13+ and no Shift upgrade is needed.

4. If the major version is **less than 13**, calculate the next target: `current_major + 1`. Then tell the user something like:

   > Your app is on Laravel {current}. The next upgrade is Laravel {next}. Would you like to run Shift to apply it?

   If the user agrees (or has already asked to proceed), invoke the `/shift-run` command and pass it the target major version (`{next}`).

## Notes

- Only look at `laravel/framework` — not `laravel/laravel` or any other package.
- Strip any constraint prefix characters (`^`, `~`, `>=`, `*`) to isolate the numeric major version.
- Treat version strings like `^12.0`, `^12`, `~12.3`, `12.*` all as major version `12`.
- Do not attempt to parse the installed version from `composer.lock` — always use `composer.json`.
