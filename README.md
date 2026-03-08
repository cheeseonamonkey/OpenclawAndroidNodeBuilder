# OpenclawAndroidNodeBuilder

GitHub Actions repo that builds the current Android APK for [`openclaw/openclaw`](https://github.com/openclaw/openclaw) and publishes a rolling release.

Find the installable APK on the **[releases page](https://github.com/cheeseonamonkey/OpenclawAndroidNodeBuilder/releases/tag/android-latest)**.

## What it does
- Triggers on:
  - manual run (`workflow_dispatch`, optional `source_ref`, default `main`)
  - weekly schedule (`0 9 * * 1`)
- Checks out `openclaw/openclaw` at the selected ref.
- Builds `apps/android` with Gradle (`:app:assembleDebug`).
- Validates APK, computes SHA-256 + size, uploads artifacts.
- Publishes/overwrites release tag `android-latest` with APK + `.sha256`.

## Outputs
- CI artifact: `openclaw-android-debug`
- GitHub Release:
  - tag: `android-latest`
  - name: `Android latest`
  - files: latest debug APK + checksum

## Workflow file
- `.github/workflows/build-android.yml`

## Notes
- This pipeline currently ships **debug** APKs.
- Build source defaults to `openclaw/openclaw@main` unless overridden in manual dispatch.
