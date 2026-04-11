# Grant Request

A React + Vite frontend for managing grant requests on the Stellar Soroban blockchain.

This project lets coordinators create grant records, applicants submit their requests, approvers approve decisions, and coordinators close the grant process on-chain.

## Screenshots

![App page](public/ss1.png)

_App page screenshot showing the grant request UI._

![Contract page](public/ss2.png)

_Contract page screenshot showing blockchain contract interaction and request tracking._

## Key Features

- Connect to Stellar using the Freighter wallet
- Create grant request records with coordinator, applicant, title, details, and track
- Submit requests on behalf of applicants
- Approve requests through on-chain approval flows
- Close grant requests with confirmation
- Lookup individual requests, list all requests, and read total request count

## Tech Stack

- React 19
- Vite
- Stellar SDK
- Freighter API
- Soroban testnet

## Prerequisites

- Node.js 18+ installed
- `npm` available
- Freighter wallet browser extension installed and configured for Stellar testnet

## Setup

```bash
npm install
npm run dev
```

Open the local Vite server URL shown in the terminal.

## Available Scripts

- `npm run dev` — start development server
- `npm run build` — build production assets
- `npm run preview` — preview the production build locally
- `npm run lint` — run ESLint checks

## How to Use

1. Open the app in your browser.
2. Click `Connect Freighter` to connect your Stellar wallet.
3. Use the `Create` tab to create a grant request record with a unique ID, coordinator address, applicant address, track, title, details, and creation timestamp.
4. Switch to the `Workflow` tab to submit the request, approve it, or close it when the process is complete.
5. Use the `Lookup` tab to fetch a specific record, list all grant requests, or get the total request count.

## Contract Integration

The frontend communicates with a Soroban contract through `lib/stellar.js`.

- `CONTRACT_ID` is the deployed contract identifier used by the frontend
- `DEMO_ADDR` is a demo address used for read-only request simulation
- Write operations require a connected Freighter wallet
- Read operations are simulated against the Soroban testnet

If you deploy a new contract, update `CONTRACT_ID` and `DEMO_ADDR` in `lib/stellar.js`.

## Supported Grant Actions

- `createRequest` — create a new grant request record
- `submitRequest` — submit the request as an applicant
- `approveRequest` — approve the request as a coordinator
- `closeRequest` — close the grant request process on-chain
- `getRequest` — fetch a grant request by ID
- `listRequests` — list all grant request records
- `getRequestCount` — read the total number of requests

## Project Structure

- `src/App.jsx` — main React UI for grant workflows
- `src/App.css` / `src/index.css` — application styling
- `lib/stellar.js` — Soroban contract helper functions and Freighter integration
- `contract/` — Soroban smart contract workspace
- `public/` — static public files and screenshots

## Notes

- This demo is built for the Stellar testnet and requires Freighter to sign transactions.
- Grant record IDs must be unique.
- Addresses must be valid Stellar public keys (beginning with `G`).
- `createdAt` should be provided as a Unix timestamp in seconds.

## Contribution

To improve this project, consider adding:

- grant request status labels and approval history
- applicant and coordinator role separation in the UI
- better validation for Stellar addresses and timestamps
- richer request metadata and comments
- deployment and contract setup instructions for Soroban
