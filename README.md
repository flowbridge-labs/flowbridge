# FlowBridge

**Build workflows where AI agents hand work to each other.**

Pick agents from the marketplace, drop them onto a canvas, and connect their inputs and outputs. A research agent can gather sources, hand them to a writing agent, and send the draft to a reviewer. You set up the workflow once and skip the copy-paste between steps.

The web app uses the Provance API to run workflows and stream progress back to the editor.

![Provance application preview](image-1.png)

## What you can do

- Build workflows on a React Flow canvas and configure each agent's inputs.
- Run workflows and inspect live logs, step outputs, and run history.
- Browse the marketplace or claim an ERC-8004 agent you own through 8004scan.
- Approve wallet payments when a workflow step requests one.

## Run locally

Use Node.js 24 and pnpm 10.6.5, the version specified in `package.json`. You also need access to a running Provance API and a Privy app ID.

1. Install dependencies.

   ```bash
   pnpm install --frozen-lockfile
   ```

2. Create `.env.local` in the project root.

   ```dotenv
   VITE_API_URL=http://localhost:4000/api/v1
   VITE_PRIVY_APP_ID=your_privy_app_id
   ```

   Set `VITE_API_URL` to the API base URL for your environment. The value above is the client's default for a local backend. Replace the Privy placeholder with your app ID.

3. Start the client and open the local URL printed by Vite.

   ```bash
   pnpm dev
   ```

## App routes

| Route | Purpose |
| --- | --- |
| `/` | Landing page |
| `/auth` | Sign-in dialog |
| `/docs` | Redirects to the introduction |
| `/docs/:slug` | Documentation article |
| `/app` | Workflow dashboard |
| `/app/workflows/:id` | Workflow editor and run history |
| `/app/agents` | Agent marketplace |
| `/app/wallet` | Wallet page |

## Development

The client uses React, TypeScript, Vite, and Tailwind CSS. React Flow powers the workflow editor, TanStack Query and Zustand manage data and state, and Privy, Wagmi, and Viem support wallet interactions.

| Command | Purpose |
| --- | --- |
| `pnpm dev` | Start the development server |
| `pnpm build` | Type-check and build for production |
| `pnpm lint` | Run ESLint |
| `pnpm preview` | Serve the production build locally |

If you build agents, the [agent integration guide](src/content/docs/agents.md) explains how to claim a registered agent and describe the actions, inputs, and outputs that appear in the workflow editor. The docs also cover [building workflows](src/content/docs/workflows.md) and [agent payments](src/content/docs/payments.md).
