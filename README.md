# RTL87x3G Watch SDK

This repository is the west manifest repository for the RTL87x3G Watch SDK. The examples below use `watch/v1.14.3.2`; replace it with the required version tag when necessary.

## Documentation

For the complete SDK documentation, see the [RealMCU RTL87x3G SDK Documentation](https://docs.realmcu.com/sdk/rtl87x3g/common/en/latest/index.html).

## Initialize a Specific Version

```bash
west init -m https://github.com/rtkconnectivity/rtl87x3g-zsdk.git --mr watch/v1.14.3.2 rtl87x3g-watch-sdk
cd rtl87x3g-watch-sdk
west update
```

After initialization, this repository is located at `rtl87x3g-watch-sdk/zephyrproject/realtek-app`.

## Update the SDK

Check out the required version tag in `realtek-app`, then update the other west-managed repositories:

```bash
cd rtl87x3g-watch-sdk/zephyrproject/realtek-app
git fetch
git checkout watch/v1.14.3.2
west update
```

## Fetch Release Assets

> **Important:** After updating the SDK version, back up the existing firmware (`bin/`) and tools (`tools/`), then run `fetch_assets.py` to update them to the new version.

Large files such as `bin/` and `tools/` are distributed through GitHub Releases. After checking out the required version, run:

```bash
cd rtl87x3g-watch-sdk/zephyrproject/realtek-app
python fetch_assets.py
```

The script reads `assets.yaml` for the checked-out version, downloads the corresponding assets, verifies their SHA-256 checksums, and extracts them into the repository. Common options:

```bash
python fetch_assets.py --force          # Force assets to be downloaded and extracted again
python fetch_assets.py --keep-archives  # Keep ZIP archives after extraction
```

If PyYAML is not installed, install it first:

```bash
pip install pyyaml
```
