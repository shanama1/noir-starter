# Noir with Vite and Hardhat

[![Netlify Status](https://api.netlify.com/api/v1/badges/e4bd1ebc-6be1-4ed2-8be8-18f70382ae22/deploy-status)](https://app.netlify.com/sites/noir-vite-hardhat/deploys)

This example uses [Vite](https://vite.dev/) as the frontend framework, and
[Hardhat](https://hardhat.org/) to deploy and test.

## Getting Started

1. Install [yarn](https://yarnpkg.com/) (tested on yarn v1.22.19)

2. Install [Node.js >20.10 (latest LTS)](https://nodejs.org/en) (tested on v18.17.0)

3. Install [noirup](https://noir-lang.org/getting_started/nargo_installation/#option-1-noirup) with

   ```bash
   curl -L https://raw.githubusercontent.com/noir-lang/noirup/main/install | bash
   ```

4. Install Nargo v0.19.4 with

   ```bash
   noirup -v 0.19.4
   ```

5. Install dependencies with

   ```bash
   yarn
   ```

6. Navigate to the circuits directory with

   ```bash
   cd circuits
   ```

7. Write your Noir program in `./circuits/src`.

   > **Note:** You can read more about writing Noir programs in the
   > [Noir docs](https://noir-lang.org/).

8. Generate the verifier contract with

   ```bash
   nargo codegen-verifier
   ```

9. Navigate back into the vite-hardhat_ directory with

    ```bash
    cd ..
    ```

## Test locally

1. Copy `vite-hardhat/.env.example` to a new file `vite-hardhat/.env`.

2. Start a local development EVM at <http://localhost:8545> with

   ```bash
   npx hardhat node
   ```

   or if foundry is preferred, with

   ```bash
   anvil
   ```

3. Run the [example test file](./test/index.test.ts) with

   ```bash
   yarn test
   ```

The test demonstrates basic usage of Noir in a TypeScript Node.js environment.

## Deploy locally

1. Copy `vite-hardhat/.env.example` to a new file `vite-hardhat/.env`.

2. Start a local development EVM at <http://localhost:8545> with

   ```bash
   npx hardhat node
   ```

   or if foundry is preferred, with

   ```bash
   anvil
   ```

3. Build the project and deploy contracts to the local development chain with

   ```bash
   NETWORK=localhost yarn build
   ```

   > **Note:** If the deployment fails, try removing `yarn.lock` and reinstalling dependencies with
   > `yarn`.

4. Once your contracts are deployed and the build is finished, you can preview the built website with

   ```bash
   yarn preview
   ```

## Deploy on networks

You can choose any other network in `hardhat.config.ts` and deploy there using this `NETWORK`
environment variable.

For example, `NETWORK=mumbai yarn build` or `NETWORK=sepolia yarn build`.

Make sure you:

- Update the deployer private keys in `vite-hardhat/.env`
- Have funds in the deployer account
- Add keys for alchemy (to act as a node) in `vite-hardhat/.env`

Feel free to contribute with other networks in `hardhat.config.ts`
