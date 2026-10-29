# Sample Hardhat 3 Project (`node:test` and `viem`)

This project showcases a Hardhat 3 project using the native Node.js test runner (`node:test`) and the `viem` library for Ethereum interactions.

To learn more about Hardhat 3, please visit the [Getting Started guide](https://hardhat.org/docs/getting-started#getting-started-with-hardhat-3). To share your feedback, join our [Hardhat 3](https://hardhat.org/hardhat3-telegram-group) Telegram group or [open an issue](https://github.com/NomicFoundation/hardhat/issues/new) in our GitHub issue tracker.

## Project Overview

This example project includes:

- A simple Hardhat configuration file.
- Foundry-compatible Solidity unit tests.
- TypeScript integration tests using [`node:test`](https://nodejs.org/api/test.html), the new Node.js native test runner, and [`viem`](https://viem.sh/).
- Examples demonstrating how to connect to different types of networks, including locally simulating OP mainnet.

## Cómo empezar

### 1. Requisitos

- [Node.js](https://nodejs.org/) (incluye `npm`)
- [Git](https://git-scm.com/)

### 2. Crear el proyecto Hardhat

```shell
npm init -y
npm install --save-dev hardhat
npx hardhat --init
```

En el asistente de `--init` se eligió:

- Carpeta: `.` (la carpeta actual)
- Tipo de proyecto: TypeScript con Node Test Runner y Viem
- Convertir `package.json` a ESM: sí
- Instalar dependencias: sí

### 3. Compilar y probar

```shell
npx hardhat compile
npx hardhat test
```

### 4. Subir el proyecto a GitHub

Crear primero el repositorio vacío en GitHub (sin README ni `.gitignore`) y luego:

```shell
git init
git add .
git commit -m "Proyecto inicial Hardhat 3"
git branch -M main
git remote add origin https://kevin4965-hue@github.com/kevin4965-hue/tokenETH.git
git push -u origin main
```

> Nunca subir llaves privadas, frases semilla ni API keys. Esos valores van en `.env` (ignorado por `.gitignore`) o en `npx hardhat keystore`.

## Usage

### Running Tests

To run all the tests in the project, execute the following command:

```shell
npx hardhat test
```

You can also selectively run the Solidity or `node:test` tests:

```shell
npx hardhat test solidity
npx hardhat test nodejs
```

### Make a deployment to Sepolia

This project includes an example Ignition module to deploy the contract. You can deploy this module to a locally simulated chain or to Sepolia.

To run the deployment to a local chain:

```shell
npx hardhat ignition deploy ignition/modules/Counter.ts
```

To run the deployment to Sepolia, you need an account with funds to send the transaction. The provided Hardhat configuration includes a Configuration Variable called `SEPOLIA_PRIVATE_KEY`, which you can use to set the private key of the account you want to use.

You can set the `SEPOLIA_PRIVATE_KEY` variable using the `hardhat-keystore` plugin or by setting it as an environment variable.

To set the `SEPOLIA_PRIVATE_KEY` config variable using `hardhat-keystore`:

```shell
npx hardhat keystore set SEPOLIA_PRIVATE_KEY
```

After setting the variable, you can run the deployment with the Sepolia network:

```shell
npx hardhat ignition deploy --network sepolia ignition/modules/Counter.ts
```
