# Anvil Uplink Notes

## Installation Commands
- `pip install anvil-uplink`
- `pip show anvil-uplink`

These commands install the Anvil Uplink client library and verify that it is available in the Python environment.

## Basic Module Check
```bash
python - <<'PY'
import anvil.server
print('anvil.server imported; API methods include connect, call, wait_forever:')
print([name for name in dir(anvil.server) if not name.startswith('_')][:8])
PY
```

Running the snippet above confirms that the `anvil.server` module is available and lists several of its public helpers. You can replace the inspection step with real code once you have an Uplink key from an Anvil app.
