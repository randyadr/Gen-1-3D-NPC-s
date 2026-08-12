# GitHub auto-update setup — v1.1.4

This package is already configured for the public GitHub repository:

`randyadr/gen1_true_3d_characters`

## First upload

1. Create the public GitHub repository `randyadr/gen1_true_3d_characters`.
2. Upload **the contents of this folder** to the repository root.
3. Make sure the default branch is `main`.
4. Commit/push the files.
5. GitHub Actions runs `.github/workflows/release.yml` and publishes release `v1.1.4` with:

   `gen1_true_3d_characters-1.1.4.zip`

The release workflow verifies that `manifest.json` is at the ZIP root and stamps the real GitHub repository slug into every published release.

## Future updates

For the next mod update, change the mod files and bump `manifest.json` from `1.1.4` to `1.1.5`, then push to `main`. The workflow will create:

`gen1_true_3d_characters-1.1.5.zip`

If you push a real mod-file change without manually bumping the manifest version, the workflow can increment the newest release tag's patch version automatically.

## Gen1Recomp mod index

After `v1.1.4` exists as a GitHub Release, submit the mod once to `bryanthaboi/gen1recomp-mod-index` with these values:

- id: `gen1_true_3d_characters`
- title: `Gen1 TRUE 3D Characters`
- version: `1.1.4`
- categories: `ART`, `CONTENT`
- github: `randyadr/gen1_true_3d_characters`
- repo: `https://github.com/randyadr/gen1_true_3d_characters`
- automatic_version_check: `true`
- api: `2`
- game_version: `0.0.0-dev || >=0.1.37 <2.0.0`
- profile: `content`
- permissions: `engine_internals`
- dependency: `DRAMATIC_SHAPE@>=1.7.0 <2.0.0`

Once accepted, the index can follow later GitHub Releases automatically.
