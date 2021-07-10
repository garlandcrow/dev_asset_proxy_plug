# DevAssetProxy

Phoenix plug to proxy a locally running instance of the dev server.<br />
This plug will only serve assets when the env parameter has the value of `:dev`.<br />
Phoenix will be allowed a chance to resolve any assets not resolved by the dev server.<br />

## Installation

```elixir
defp deps do
  [
    {:dev_asset_proxy_plug, "~> 0.3.0"}
  ]
end
```

And run:

\$ mix deps.get

## Usage

Add DevAssetProxy.Plug as a plug in the phoenix project's endpoint.

## Arguments

- **port** - _(required)_ The port that the dev server is listening on.
- **assets** - _(required)_ a list of the paths in the static folder that dev server should handle serving. The plug will ignore requests to any other path.
- **env** - _(required)_ the current environment the project is running under.

## Example

in `endpoint.ex`

```elixir
  plug DevAssetProxy.Plug,
    port: 8080,
    assets: ~w(public @vite @inertiajs node_modules css src __vite_ping),
    env: Mix.env()
```
