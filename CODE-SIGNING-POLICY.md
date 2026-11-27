# Code signing policy

## Windows

The Windows installer (`.msi`, also offered as `-msi.zip`), the portable `.zip` and the program in them
(`aitrack.exe`) are not code-signed yet, so Windows SmartScreen may show "Unknown publisher" the first time (choose
"Run anyway"). Check the download against `SHA256SUMS` (below) before you open it. This file will be updated when
signing starts.

## macOS

The macOS app (`.dmg` and `.zip`) is signed with an Apple Developer ID and notarized by Apple.

## Linux

The `.deb` package is not signed. Check it against `SHA256SUMS` before you install it.

## How a release is made

- Each build is made by the project owner on their own computer from the private source. No hosted build service
  is used.
- The owner approves each release and uploads the files by hand to
  [Releases](https://github.com/ai4coo/aiTrack/releases), together with `SHA256SUMS`.
- Signing keys and passwords stay on the owner's build computers and are never stored in a repository.

## Checking a download

`SHA256SUMS` on the release lists the SHA-256 checksum of every file.

- **Windows** (PowerShell): `Get-FileHash .\aiTrack-Setup-<version>-win-x64.msi -Algorithm SHA256`
- **macOS**: `shasum -a 256 aiTrack-<version>-macos-arm64.dmg`
- **Linux**: `sha256sum -c --ignore-missing SHA256SUMS`

Compare the result with the line for that file in `SHA256SUMS`.

## Roles

- **Authors** (who write the code that is built and signed): the project owner, Take Two Partners, LLC (GitHub:
  [ai4coo](https://github.com/ai4coo)). Currently the only maintainer.
- **Reviewers** (who review changes before they are merged into `main`): the project owner, currently the
  only maintainer.
- **Approvers** (who approve each signing request): the project owner, currently the only maintainer. Every
  release is approved by the project owner before it is started.

The maintainer's GitHub account is protected with two-factor authentication.

## Privacy

See [PRIVACY.md](PRIVACY.md): aiTrack does not transfer any information to other networked systems except the requests
listed there, which are needed for it to work.

## Reporting a problem

If you think a signed file is wrong or malicious, write to aitrack@sirgene.com.
