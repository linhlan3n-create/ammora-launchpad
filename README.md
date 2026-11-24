# Ammora Launchpad — Powered by Ammora

A community-built launchpad interface for **GIWA Sepolia (chain ID 91342)** using the public `@ammora-protocol/sdk@0.3.9`.

## Included

- Wallet connection through an injected EIP-1193 wallet.
- GIWA Sepolia network detection and switch.
- Launch discovery through `AmmoraDataApiClient`.
- Config lookup at a finalized block.
- Runtime-pin file validation and SDK runtime/core verification before preparing a launch.
- V4 launch calldata construction, RPC simulation, wallet signing, receipt confirmation and token/curve code reconciliation.
- Explicit guard against quarantined Config #6.

## Important safety boundaries

- This is **testnet-only**. It is not a mainnet product.
- No private key is stored or requested by this app.
- A wallet transaction is sent only after the user presses the final confirmation button and confirms in their wallet.
- The app requires the official `runtime-pins.giwa.json` file for the SDK's `auto-route` deployment. Obtain it from the [Ammora official examples source](https://docs.ammora.org/examples/source/src/quickstart/runtime-pins.giwa.json.txt).
- Before using a Config, independently inspect its immutable identity, quote asset, token decimals, fees, vesting, LP locks, sale/graduation budgets and derived graduation reserves. The app blocks Config #6. Config #10 is **not** an automatic replacement.
- A Config being enabled does not prove that it is safe for graduation.
- The launch creation path uses an existing, already-reviewed Config. Config creation and partner fee recipient setup are separate workflows.
- A successful local build is not proof of a live chain transaction. Keep the returned transaction hash and verify the canonical receipt.

## Requirements

- Node.js 22 or 24
- MetaMask or another EIP-1193 wallet
- GIWA Sepolia test ETH
- A separately qualified V4 Config ID
- The official runtime pin JSON file

## Run locally

```bash
npm install
npm run dev
```

Open the Vite URL shown in the terminal.

## Build for hosting

```bash
npm run build
npm run preview
```

Deploy the generated `dist/` directory to a static host such as Vercel, Netlify or Cloudflare Pages. Use the build command `npm run build` and output directory `dist`.

## Mission submission

The Ammora Season 2 builder mission asks for:
1. Build with the SDK.
2. Post the build on X.
3. Submit the website link for review.

After deployment, post a short product demo on X and submit the public website URL through the Builder Mission's **Submit your build** action. Review/acceptance is determined by Ammora; this project does not claim approval.

## Official references

- [Ammora SDK quickstart](https://docs.ammora.org/guides/sdk-quickstart)
- [Ammora launchpad guide](https://docs.ammora.org/guides/launchpad)
- [SDK 0.3.9 live deployment status](https://docs.ammora.org/guides/sdk-status)
- [npm package](https://www.npmjs.com/package/@ammora-protocol/sdk)
- [Builder Mission](https://ammora.org/waitlist?topic=sdk)
