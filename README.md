# Proyecto de ejemplo Hardhat 3 (`node:test` y `viem`)

Este proyecto es un ejemplo de Hardhat 3 que usa el ejecutor de pruebas nativo de Node.js (`node:test`) y la librería `viem` para interactuar con Ethereum.

Para aprender más sobre Hardhat 3, visita la [guía de inicio](https://hardhat.org/docs/getting-started#getting-started-with-hardhat-3). Para compartir comentarios, únete al grupo de Telegram de [Hardhat 3](https://hardhat.org/hardhat3-telegram-group) o [abre un issue](https://github.com/NomicFoundation/hardhat/issues/new) en el repositorio de Hardhat en GitHub.

## Descripción del proyecto

Este proyecto de ejemplo incluye:

- Un archivo de configuración de Hardhat sencillo.
- Pruebas unitarias en Solidity compatibles con Foundry.
- Pruebas de integración en TypeScript usando [`node:test`](https://nodejs.org/api/test.html), el ejecutor de pruebas nativo de Node.js, y [`viem`](https://viem.sh/).
- Ejemplos de cómo conectarse a distintos tipos de redes, incluida una simulación local de OP mainnet.

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

## Uso

### Ejecutar las pruebas

Para ejecutar todas las pruebas del proyecto:

```shell
npx hardhat test
```

También puedes ejecutar solo las pruebas de Solidity o solo las de `node:test`:

```shell
npx hardhat test solidity
npx hardhat test nodejs
```

### Desplegar en Sepolia

El proyecto incluye un módulo de Ignition de ejemplo para desplegar el contrato. Puedes desplegarlo en una cadena simulada localmente o en Sepolia.

Para desplegar en una cadena local:

```shell
npx hardhat ignition deploy ignition/modules/Counter.ts
```

Para desplegar en Sepolia necesitas una cuenta con fondos para pagar la transacción. La configuración de Hardhat usa dos variables de configuración:

- `SEPOLIA_RPC_URL`: la URL del nodo RPC de Sepolia (por ejemplo, de Alchemy o Infura).
- `SEPOLIA_PRIVATE_KEY`: la llave privada de la cuenta que quieres usar.

Puedes definirlas con el plugin `hardhat-keystore` o como variables de entorno.

Para definirlas con `hardhat-keystore`:

```shell
npx hardhat keystore set SEPOLIA_RPC_URL
npx hardhat keystore set SEPOLIA_PRIVATE_KEY
```

Después de definir las variables, ejecuta el despliegue en la red Sepolia:

```shell
npx hardhat ignition deploy --network sepolia ignition/modules/Counter.ts
```
