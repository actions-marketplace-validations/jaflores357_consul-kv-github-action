# consul-kv-github-action
GitHub Action to lookup a key in Consul KV and set its value as an environment variable. 

## Inputs

### `url`

**Required** The URL to the Consul HTTP Agent

### `key`

**Required** The path and key to look up in Consul KV

### `name`

**Required** The name of environment var to the value

## Example workflow

```
on: [push]

jobs:
  consul_kv_job:
    runs-on: ubuntu-latest
    name: A job to test getting a value from Consul KV
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: get value from Consul KV
        id: get
        uses: jaflores357/consul-kv-github-action@v1
        with:
          url: demo.consul.io:8500
          key: path/mykey
          name: mykey
      # Use the environment variable set by the key
      - name: prints the value of the key
        run: echo "The value from Consul is ${{ env.name }}"
```
