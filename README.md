# EOS System Contract v3.3.0 Upgrade

> [Release Notes](https://github.com/eosnetworkfoundation/eos-system-contracts/releases/tag/v3.3.0)

## [Build CDT](https://github.com/AntelopeIO/cdt) (`v4.0.1`)

```bash
git clone --recursive https://github.com/AntelopeIO/cdt
cd cdt
git checkout v4.0.1
mkdir build
cd build
cmake ..
make -j $(nproc)
```

## [Compile EOS System Contracts](https://github.com/eosnetworkfoundation/eos-system-contracts/releases/tag/v3.3.0) (`v3.3.0`)

```bash
gh repo clone eosnetworkfoundation/eos-system-contracts
cd eos-system-contracts
git checkout v3.3.0
export CDT_INSTALL_DIR="<path>/cdt/build"
./build.sh
```

```bash
$ shasum -a 256 ./build/contracts/eosio.system/eosio.system.wasm
a2d9c10b72a586409f77be944094c161e4170bb0a7bab6e072b19161001e1930  ./build/contracts/eosio.system/eosio.system.wasm

$ shasum -a 256 ./build/contracts/eosio.wrap/eosio.wrap.wasm
ecb8e3a5e1841acb71067e886b1c50d647d54906b232beb725bd8ac331ad78bb  ./contracts/eosio.wrap/eosio.wrap.wasm

$ shasum -a 256 ./build/contracts/eosio.msig/eosio.msig.wasm
9bddf7e0444a3a5f457f88509824ec8c46dcbedbf7b15ffdf6dd03d7f8ec33e8  ./contracts/eosio.msig/eosio.msig.wasm
```

## Protocol Upgrades

| Protocol Feature | SHA-256 Hash
|------------------|--------------
| DISABLE_DEFERRED_TRXS_STAGE_1 | fce57d2331667353a0eac6b4209b67b843a7262a848af0a49a6e2fa9f6584eb4
| DISABLE_DEFERRED_TRXS_STAGE_2 | 09e86cb0accf8d81c9e85d34bea4b925ae936626d00c984e4691186891f5bc16

## MSIG Schedules

### MSIG - [`upgrade.v3.3`](https://bloks.io/msig/eosnationftw/upgrade.v3.3)

> https://bloks.io/msig/eosnationftw/upgrade.v3.3
>
> https://eosauthority.com/msig/eosnationftw/upgrade.v3.3?network=eos
>
> https://msig.app/eos/eosnationftw/upgrade.v3.3

**Steps**
- Step 1 `setcode.v3.3` - Deploy all system contracts
- Step 2 `activate.v3.3` - Activate protocol feature
- Step 3 `eosio.wram` - Create `eosio.wram` account

### Step 1 - `setcode.v3.3`
- Upgrade `setcode` & `setabi` for all system contracts
 - `eosio`
 - `eosio.msig`
 - `eosio.wrap`

### Step 2 - `activate.v3.3`
- Activate protocol features:
  - ~~`BLS_PRIMITIVES2`~~
  - `DISABLE_DEFERRED_TRXS_STAGE_1`
  - `DISABLE_DEFERRED_TRXS_STAGE_2`

### Step 3 - `eosio.wram`
- Create `eosio.wram` account with `eosio` permissions
- ~~Create `0,RAM` token using `eosio.token` contract with max supply `418945440768` (418GB)~~
