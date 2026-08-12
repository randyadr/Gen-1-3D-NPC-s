# GitHub auto-update setup

This repository package is prepared for Gen1Recomp's built-in GitHub mod updater.

## One-time setup

1. Create a new **public GitHub repository**. Recommended repository name: `gen1_true_3d_characters`.
2. Upload **the contents of this folder** to the repository root. `manifest.json` must be at the repository root.
3. In `manifest.json`, replace:

   `YOUR_GITHUB_USERNAME/gen1_true_3d_characters`

   with your real GitHub `owner/repo` (for example `SomeUser/gen1_true_3d_characters`).
4. Commit/push to the `main` branch.
5. GitHub Actions runs `.github/workflows/release.yml` and creates release `v1.1.3` with:

   `gen1_true_3d_characters-1.1.3.zip`

6. Install that generated release ZIP once in Gen1Recomp. From then on, the installed mod contains the real `github` repo slug and the game's **Update / Versions** UI can follow future releases.

> The release workflow also stamps `${{ github.repository }}` into the manifest inside every published ZIP, so even if you forget step 3, generated release ZIPs still point to the correct repository. Editing the source manifest is still recommended.

## Future updates

Normal workflow:

1. Change the mod files.
2. Bump `manifest.json` `version` (recommended), e.g. `1.1.4`.
3. Push to `main`.
4. The GitHub Action publishes `gen1_true_3d_characters-1.1.4.zip`.

If you change files without bumping `manifest.json`, the workflow follows Gen1Recomp's official release behavior and increments the newest release tag's patch version automatically.

You can also run **Actions > Release > Run workflow** and enter an exact version.

## Gen1Recomp mod index

After the repository has at least one GitHub Release, submit it once to `bryanthaboi/gen1recomp-mod-index`. Use:

- id: `gen1_true_3d_characters`
- title: `Gen1 TRUE 3D Characters`
- version: `1.1.3` (or whatever your first public release is)
- categories: `ART`, `CONTENT`
- github: your real `owner/repo`
- repo: `https://github.com/<owner>/<repo>`
- automatic_version_check: `true`
- api: `2`
- game_version: `0.0.0-dev || >=0.1.37 <2.0.0`
- profile: `content`
- permissions: `engine_internals`
- dependency: `DRAMATIC_SHAPE@>=1.7.0 <2.0.0`

Once accepted, the mod index checks GitHub Releases automatically; you do not submit a new index PR for every version.
