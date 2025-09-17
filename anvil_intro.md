# Getting Started with Anvil Uplink

Anvil (https://anvil.works) lets you build full-stack web apps entirely in Python. With the Anvil Uplink client library you can
connect Python scripts that run outside of the Anvil cloud (for example, on your own machine or a server) to an Anvil app.

## What You Can Do with Anvil
- **Call Anvil server functions from local Python code.** Use `anvil.server.call("function_name")` to invoke functions you
define in your Anvil app.
- **Expose local Python functions to your Anvil app.** Decorate a local function with `@anvil.server.callable` and it becomes
reachable from Anvil forms or server modules.
- **Stream data between Anvil and external systems.** Because your local Python code has full access to the libraries installed
on your machine, you can integrate with databases, file systems, or other APIs and relay the results to your Anvil UI.

## Verifying the Installation
```bash
python - <<'PY'
import anvil.server
print('Available helper names:', [name for name in dir(anvil.server) if not name.startswith('_')][:8])
PY
```

## Minimal Uplink Example
```python
import anvil.server

anvil.server.connect("YOUR-UPLINK-KEY")

@anvil.server.callable
def say_hello(name: str) -> str:
    return f"Hello, {name}!"

anvil.server.wait_forever()
```
Replace `YOUR-UPLINK-KEY` with a key generated inside your Anvil app. Once this script is running, the `say_hello` function can
be called from the app with `anvil.server.call("say_hello", "Anvil")`.
