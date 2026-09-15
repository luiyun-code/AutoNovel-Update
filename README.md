# AutoNovel Update Channel

Public binary distribution surface for **AutoNovel 2.1+**.

Application source remains private in `luiyun-code/AutoNovel`; this repository is deliberately not a source mirror.

## Canonical Portable channel

AutoNovel clients read:

`https://raw.githubusercontent.com/luiyun-code/AutoNovel-Update/main/latest.json`

Starting with the release after alpha.3, every Windows Portable release uses exactly:

- `AutoNovel.exe`
- `AutoNovel.exe.sig`
- `AutoNovel.exe.sha256`
- `latest.json`

No NSIS `setup.exe`, MSI, source code, runtime DLL bundle or permanent updater helper belongs to the AutoNovel Portable publication line.

Release tags use `v<semver>`.

## Alpha.3 historical naming bridge

`v2.1.0-alpha.3` was published before the permanent executable filename was frozen. Its immutable historical binary is:

`AN_2.1.0-alpha.3_x64.exe`

That filename is valid only for alpha.3. Alpha.4 and all later releases must publish `AutoNovel.exe`.

`v2.1.0-alpha.1` and `v2.1.0-alpha.2` are historical installer-era test releases. The old `releases/latest` pointer intentionally remains on alpha.2 so an already-installed legacy client cannot interpret a raw Portable EXE as an installer. Portable clients use repository-root `latest.json` instead.

## Security boundary

- Never publish AutoNovel source, SQLite/user data, credentials, signing private keys, passwords, PATs or secret-bearing CI logs here.
- The updater private key stays outside both repositories and is provided only to the trusted private build pipeline.
- Clients verify detached signatures against the public key embedded in AutoNovel before replacing the executable.
- A missing, malformed, unsigned, wrong-platform, downgraded, wrong-source or noncanonical update fails closed.
- The temporary updater helper is created at runtime under `%TEMP%`, is not a distributed asset and is removed after successful replacement.
- Do not hand-edit a generated signature, checksum or release manifest after publication.

## Ownership

`luiyun-code/AutoNovel` is the private source/integration repository.

`luiyun-code/AutoNovel-Update` is the public signed binary/update-metadata repository only.
