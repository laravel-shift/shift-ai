# Shift Run

Run a Shift against this repository via the Shift API. The target Laravel version is: $ARGUMENTS

## Steps

1. Check if `SHIFT_API_TOKEN` is set in the environment. If it's missing, ask the user to provide their Shift API token. Once provided, save it to `.claude/settings.local.json` under the `env` key so it's automatically available in all future sessions:
   ```json
   {
     "env": {
       "SHIFT_API_TOKEN": "their_token"
     }
   }
   ```
   If `.claude/settings.local.json` already exists, merge the key into the existing `env` object rather than overwriting the file.

2. Determine the GitHub remote and current branch by running:
   ```bash
   git remote get-url origin
   git branch --show-current
   ```
   Parse the remote URL to extract `owner/repo` — handle both SSH (`git@github.com:owner/repo.git`) and HTTPS (`https://github.com/owner/repo.git`) formats. Strip any trailing `.git`.

3. Build the `scs` connection string in the format `github:owner/repo:branch`.

4. Run the Shift via the API:
   ```bash
   curl -X POST -H 'Accept: application/json' \
     -d "api_token=$SHIFT_API_TOKEN" \
     -d "code=$ARGUMENTS" \
     -d "scs=github:owner/repo:branch" \
     https://laravelshift.com/api/run
   ```

5. Report the API response to the user. If successful, let them know the Shift has been queued and they can monitor progress on laravelshift.com.
