# AutoNovel Update Channel

Public binary distribution surface for **AutoNovel AN 2.1+**.

The application source code remains private in `luiyun-code/AutoNovel`. This repository is deliberately **not** a source mirror.

## Canonical Portable channel

AN 2.1 Portable clients read the public updater pointer from the repository root:

`https://raw.githubusercontent.com/luiyun-code/AutoNovel-Update/main/latest.json`

Each Portable Windows release contains only the signed single-EXE update assets produced by the private AutoNovel build pipeline:

- `latest.json`
- `AN_<version>_x64.exe`
- `AN_<version>_x64.exe.sig`
- `AN_<version>_x64.exe.sha256`

No NSIS `setup.exe`, MSI, source code, runtime DLL bundle or permanent updater helper belongs to the AN 2.1 Portable publication line.

Release tags use `v<semver>`, for example `v2.1.0-alpha.3`.

## Alpha migration boundary

`v2.1.0-alpha.1` and `v2.1.0-alpha.2` are historical installer-based test releases. They are retained only so the already-installed alpha.2 client is not pointed at a raw EXE through its retired installer updater.

Portable alpha releases use the repository-root `latest.json` pointer. `v2.1.0-alpha.3` is the one-time manual migration build; the first Portable self-replacement human test is alpha.3 to alpha.4.

## Security boundary

- Never publish AutoNovel source, SQLite/user data, credentials, signing private keys, passwords, PATs, or CI logs containing secrets here.
- The updater private key stays outside both repositories and is provided only to the trusted private build pipeline.
- Portable clients verify detached signatures against the public key embedded in the application before replacing `AN.exe`.
- A missing, malformed, unsigned, wrong-platform, downgraded, wrong-source, or noncanonical update must fail closed.
- The temporary updater helper is created at runtime under `%TEMP%`, is not a distributed asset, and is removed after successful replacement.
- Do not hand-edit a generated signature, checksum, or release manifest after publication.

## Ownership

`luiyun-code/AutoNovel` is the private source/integration repository.

`luiyun-code/AutoNovel-Update` is the public signed binary/update-metadata repository only.
