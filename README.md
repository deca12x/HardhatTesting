# Hardhat Testing Template

Testing with Hardhat codealong 25th April 2022
https://www.youtube.com/watch?v=dDr7glOjtvI&ab_channel=Chainlink

OUR FLOW, Test Driven Development (TDD):
    1) Write your tests for each usecase (types of tests described below)
    2) Deployed functionality in smart contract - all tests will fail because there is no implementation in our smart contract
    3) Write the implementation until it satisfies all tests.

TYPES OF TESTS
    1) Unit Tests:
        Within a local blockcahin (Hardhat node), test one deployed contract and the rest as mocks
    2) Integration Tests:
        Local blockchain, but this time all contracts are deployed
    3) End-to-end tests:
        All contracts deployed, but this time on a Mainnet Fork
        ...i.e. copy whole state of the mainnet in a specific block
        Why? Locally there aren't other protocols affecting mainnet state, so it sin't a faithful replica
    4) Property-based tests:
        aka "fuzz tests" look at edge cases
        ...the fuzzer generates random inputs for our smart contracts to stress test it

FIXTURES
    They are testing scenarios that are executed once and then remembered by making snapshots of the blockchain
    Why? Make testing faster by avoiding repetition
    e.g. deploy token or mint NFT before doing all other tests. With fixtures, you can mint only once

TOOLS FOR TESTING WITH HARDHAT
    1) Waffle: library for writing and testing smart contracts
    2) Mocha: Javascript/Typescript testing framework for browser or node.js
    3) Chai: assertion library for browser or node.js - i.e. used to assert conditions (==)

CODE COVERAGE
    Check % of source code executed during a test - aim hor more than 90%


Try running some of the following tasks:

```shell
yarn compile
yarn test
yarn test --parallel
yarn coverage

npx hardhat accounts
npx hardhat compile
npx hardhat clean
npx hardhat test
npx hardhat node
npx hardhat help
REPORT_GAS=true npx hardhat test
npx hardhat coverage
npx hardhat run scripts/deploy.ts
TS_NODE_FILES=true npx ts-node scripts/deploy.ts
npx eslint '**/*.{js,ts}'
npx eslint '**/*.{js,ts}' --fix
npx prettier '**/*.{json,sol,md}' --check
npx prettier '**/*.{json,sol,md}' --write
npx solhint 'contracts/**/*.sol'
npx solhint 'contracts/**/*.sol' --fix
```

# Performance optimizations

For faster runs of your tests and scripts, consider skipping ts-node's type checking by setting the environment variable `TS_NODE_TRANSPILE_ONLY` to `1` in hardhat's environment. For more details see [the documentation](https://hardhat.org/guides/typescript.html#performance-optimizations).
