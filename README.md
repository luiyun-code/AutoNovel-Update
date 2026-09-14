# AutoNovel Update Channel

Public binary distribution surface for **AutoNovel AN 2.1+**.

The application source code remains private in `luiyun-code/AutoNovel`. This repository is deliberately **not** a source mirror.

## Canonical channel

AutoNovel clients read the public updater manifest from the latest GitHub Release in this repository:

`https://github.com/luiyun-code/AutoNovel-Update/releases/latest/download/latest.json`

Each published Windows update must contain exactly the signed update assets produced by the private AutoNovel build pipeline:

- `latest.json`
- `AN_<version>_x64-setup.exe`
- `AN_<version>_x64-setup.exe.sig`
- `AN_<version>_x64-setup.exe.sha256`

Release tags use `v<semver>`, for example `v2.1.0-alpha.2`.

## Security boundary

- Never publish AutoNovel source, SQLite/user data, credentials, signing private keys, passwords, PATs, or CI logs containing secrets here.
- The updater private key stays outside both repositories and is provided only to the trusted private build pipeline.
- Clients verify update signatures against the public key embedded in the application before installation.
- A missing, malformed, unsigned, wrong-platform, downgraded, or wrong-source update must fail closed.
- Do not hand-edit a generated signature or `latest.json` after the signed package has been staged.

## Ownership

`luiyun-code/AutoNovel` is the private source/integration repository.

`luiyun-code/AutoNovel-Update` is the public signed update distribution repository only.
