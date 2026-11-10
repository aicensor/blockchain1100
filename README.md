# blockchain1100

Archive of blockchain learning material and project snapshots from `D:\1100`.

## Contents

| File | Size | Stored as |
|------|------|-----------|
| `bitcoinbook-develop.zip` | 14 MB | whole file |
| `ethereumbook-develop.zip` | 12 MB | whole file |
| `node-v24.19.0-x64.zip` | 33 MB | whole file |
| `winrar-x64-611.zip` | 3 MB | whole file |
| `interactivelab-clone.zip` | 240 MB | split, `parts/interactivelab-clone.zip/` |
| `interactivelab.zip` | 238 MB | split, `parts/interactivelab.zip/` |
| `mychain-js.zip` | 234 MB | split, `parts/mychain-js.zip/` |

GitHub rejects any single file over 100 MB, so the three large archives are
stored as 95 MiB parts under `parts/<original-name>/`.

## Rebuilding a split archive

Linux / macOS / Git Bash:

```bash
cd parts/interactivelab.zip
cat interactivelab.zip.part* > ../../interactivelab.zip
```

Windows (cmd):

```
cd parts\interactivelab.zip
copy /b interactivelab.zip.part000+interactivelab.zip.part001+interactivelab.zip.part002 ..\..\interactivelab.zip
```

PowerShell:

```powershell
cd parts\interactivelab.zip
Get-ChildItem *.part* | Sort-Object Name | ForEach-Object { [IO.File]::ReadAllBytes($_.FullName) } | Set-Content ..\..\interactivelab.zip -Encoding Byte
```

Do the same in `parts/interactivelab-clone.zip/` and `parts/mychain-js.zip/`.

## Verifying

Each part folder has:

- `PARTS.sha256` — checksums of the parts as stored here
- `ORIGINAL.sha256` — checksum of the rebuilt archive

```bash
sha256sum -c PARTS.sha256          # inside the part folder
sha256sum -c ORIGINAL.sha256       # from the repo root, after rebuilding
```
