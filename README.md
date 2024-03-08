# EOS System Contract v3.3.0 Upgrade

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

## Compile EOS System Contracts (`v3.3.0`)

```bash
gh repo clone eosnetworkfoundation/eos-system-contracts
cd eos-system-contracts
git checkout v3.3.0
export CDT_INSTALL_DIR="<path>/cdt/build"
./build.sh
```

```bash
$ shasum -a 256 ./contracts/eosio.system/eosio.system.wasm
2bbf23ed66d4958071a5c9725029e628941cdc1d242f9b9bb4794d7be3dd04f2  ./contracts/eosio.system/eosio.system.wasm

$ shasum -a 256 ./contracts/eosio.wrap/eosio.wrap.wasm
ecb8e3a5e1841acb71067e886b1c50d647d54906b232beb725bd8ac331ad78bb  ./contracts/eosio.wrap/eosio.wrap.wasm

$ shasum -a 256 ./contracts/eosio.msig/eosio.msig.wasm
9bddf7e0444a3a5f457f88509824ec8c46dcbedbf7b15ffdf6dd03d7f8ec33e8  ./contracts/eosio.msig/eosio.msig.wasm
```

## Protocol Upgrades

| Protocol Feature | SHA-256 Hash
|------------------|--------------
| BLS_PRIMITIVES2  | 63320dd4a58212e4d32d1f58926b73ca33a247326c2a5e9fd39268d2384e011a
| DISABLE_DEFERRED_TRXS_STAGE_1 | fce57d2331667353a0eac6b4209b67b843a7262a848af0a49a6e2fa9f6584eb4
| DISABLE_DEFERRED_TRXS_STAGE_2 | 09e86cb0accf8d81c9e85d34bea4b925ae936626d00c984e4691186891f5bc16

## MSIG Schedules

### MSIG 1 - `setcode`
- Upgrade `setcode` & `setabi` for all system contracts
 - `eosio`
 - `eosio.msig`
 - `eosio.wrap`

### MSIG 2 - `activate`
- Activate `DISABLE_DEFERRED_TRXS_STAGE_1` + `BLS_PRIMITIVES2` + `DISABLE_DEFERRED_TRXS_STAGE_2`
- Create `eosio.wram` account + create `eosio.token@RAM` token
