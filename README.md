![Near, Inc. logo](https://nearprotocol.com/wp-content/themes/near-19/assets/img/logo.svg?t=1553011311)

# Template for NEAR Protocol workshop activities

## Environment Setup

##### IMPORTANT: Make sure you have the latest version of NEAR Shell and Node Version >= 12.x 

1. [Node.js](https://nodejs.org/en/download/package-manager/)
2. (optional) `near-shell`

```
npm i -g near-shell
```

3. (optional) yarn

```
npm i -g yarn
```

4. Clone this repo locally

5. Run `yarn` in the repo folder to install dependencies

## Working with contracts

### To run unit tests

```bash
yarn test
```

### To build the contract

```bash
yarn build
```

### To deploy the contract


1. Login with NEAR Shell

- *You will need to install NEAR Shell first if you haven't already done so*

```bash
near login
```

2. Deploy the contract to the account with which you logged in above

```bash
near deploy --accountId <contract account>

# for example: 
# near deploy --accountId alice
```

### To invoke methods on a deployed contract

- *Signer account may be the same as contract account for testing but will almost certainly **not be the same** in production*
- *See `assembly/main.ts` for available contract methods*

```bash
near call <contract account> <contract method> --accountId <signer account>

# for example: 
# near call alice sayMyName --accountId alice
```

## Walkthrough

### filesystem

```bash
   ├── README.md               # this file
   ├── as-pect.config.js       # configuration for as-pect
   ├── asconfig.js             # AssemblyScript contract build script
   ├── assembly                # AssemblyScript contract 
   │   ├── __tests__
   │   │   ├── as-pect.d.ts    # header file for as-pect type detection
*  │   │   └── main.spec.ts    # AssemblyScript contract unit tests
   │   ├── as_types.d.ts       # header file for AssemblyScript type detection
*  │   ├── main.ts             # AssemblyScript contract
   │   └── tsconfig.json       # TypeScript config
   ├── package.json            # Node.js package manager
   └── yarn.lock               # Yarn lock file
```

The two critical files in this project are marked with an asterisk (`*`) in the tree view above.  They are:
- `assembly/__tests__/main.spec.ts` (contract unit tests)
- `assembly/main.ts` (the contract)

The rest of the files support the development, testing and deployment of the contract

### `yarn`

[![asciicast](https://asciinema.org/a/hYujvtaaO3ol9FTkzt9lOnH2j.svg)](https://asciinema.org/a/hYujvtaaO3ol9FTkzt9lOnH2j)

### `yarn test`

[![asciicast](https://asciinema.org/a/gLwYhhzPYQyW2wICQtbbz06Ph.svg)](https://asciinema.org/a/gLwYhhzPYQyW2wICQtbbz06Ph)

### `yarn build`

#### Size & Speed Optimized (default)

```
 12K	out/main.wasm     (40% reduction in contract size for this contract)
 48K	out/main.wat
```

[![asciicast](https://asciinema.org/a/qPz0GYYwHRkzYkQ4kj8xpUmJM.svg)](https://asciinema.org/a/qPz0GYYwHRkzYkQ4kj8xpUmJM)

#### Non Optimized

```
 20K	out/main.wasm
104K	out/main.wat
```

*This can be useful for a more readable `WAT` file*

[![asciicast](https://asciinema.org/a/I9UJri2aVKLaBfV4ZPv6EIVnk.svg)](https://asciinema.org/a/I9UJri2aVKLaBfV4ZPv6EIVnk)

