# dotUSD watch

A single read-only page about the dotUSD stablecoin on Asset Hub Polkadot.

- **Live view** (`index.html`): supply against the 10,000,000 ceiling, the DOT price in the
  DOT/dotUSD pool, and the DOT price in the existing DOT/USDT pool as an on-chain reference,
  block by block. Before dotUSD exists it says so and lists what referendum 1944 does on
  enactment.
- **Simulation** (`index.html?demo`): a model of the pool's first blocks, built from the
  amounts fixed in the referendum's call and the live DOT/USDT price. It is labelled as a
  simulation and is not recorded data.

## How it works

One HTML file. No framework, no libraries, no build step. It reads public Asset Hub RPC
endpoints directly from the browser and fails over between them. Every figure is a plain chain
read: the asset's details, the pool reserves through the chain's own quoting function, and the
referendum's state. Nothing signs or sends a transaction.

The amounts in the simulation come from the referendum's preimage, decoded against the chain's
metadata: 2,853,229.86 DOT paired with 2,500,000 dotUSD, which is a pool opening price of about
$0.876 per DOT.

## Run locally

```bash
python3 -m http.server 4190
```

then open `http://localhost:4190/` or `http://localhost:4190/?demo`.

## Licence

MIT.
