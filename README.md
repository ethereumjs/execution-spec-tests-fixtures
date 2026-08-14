# execution-spec-tests-fixtures

Fixtures from official Ethereum test releases ([execution-specs](https://github.com/ethereum/execution-specs)) for EthereumJS consumption.

Split by **EthereumJS support**, not upstream `_stable` / `_develop` names:

- `stable/`: expected to pass on current EthereumJS `master`
- `dev/`: upcoming fork / EIP work not yet fully supported

How we bump a snapshot: `packages/vm/DEVELOPER.md` in the monorepo (Updating fixtures). Glamsterdam mixed tests live at a **stable path** `dev/blockchain_tests/amsterdam/glamsterdam/` and are replaced in place on each glamsterdam-devnet bump.

## `stable` Fixtures

From [v5.4.0](https://github.com/ethereum/execution-spec-tests/releases/tag/v5.4.0) | Dec 7, 2025 | Osaka + some pre-Osaka tests (293 JSON files):

- `state_tests/osaka/`
- `state_tests/prague/`
- `state_tests/cancun/`
- `state_tests/shanghai/`
- `blockchain_tests/osaka/`

Test exclusions (GitHub file size limit):

- `blockchain_tests/osaka/eip7934_block_rlp_limit/test_block_at_rlp_size_limit_boundary.json` (101 MB)
- `blockchain_tests/osaka/eip7934_block_rlp_limit/test_block_rlp_size_at_limit_with_all_typed_transactions.json` (168 MB)
- `blockchain_tests/osaka/eip7934_block_rlp_limit/test_fork_transition_block_rlp_limit.json` (134 MB)

## `dev` Fixtures

- [tests-glamsterdam-devnet@v7.2.1](https://github.com/ethereum/execution-specs/releases/tag/tests-glamsterdam-devnet%40v7.2.1) | Jul 24, 2026 | glamsterdam-devnet-7 | Amsterdam EIP mix, BAL definitions included | **661 JSON files**
  - `blockchain_tests/amsterdam/glamsterdam/` (replaced in place from v7.0.0; upstream path `blockchain_tests/for_amsterdam/amsterdam/`)
  - Supersedes [v7.1.0](https://github.com/ethereum/execution-specs/releases/tag/tests-glamsterdam-devnet%40v7.1.0) (EIP-7928: tx recipient excluded from BAL when EIP-7702 auth halt precedes load) and [v7.2.0](https://github.com/ethereum/execution-specs/releases/tag/tests-glamsterdam-devnet%40v7.2.0) (EIP-8037: calldata floor binds block regular-gas dimension). v7.2.1 adds EngineX fixtures upstream only; we do not consume them.
- [bal@v3.0.1](https://github.com/ethereum/execution-spec-tests/releases/tag/bal%40v3.0.1) | Jan 13, 2026 | EIP-7928 only | No mixture, no BAL definitions, EVM tests passing | 110 JSON files
  - `blockchain_tests/amsterdam/v301_single_bal_no_bal_defs/eip7928_block_level_access_lists/`
- [bal@v2.0.0](https://github.com/ethereum/execution-spec-tests/releases/tag/bal%40v2.0.0) | Dec 12, 2025 | EIP-7928 only | No mixture, BAL definitions, somewhat outdated | 102 JSON files
  - `blockchain_tests/amsterdam/v200_bal_defs_somewhat_outdated/eip7928_block_level_access_lists/`

No files in this `dev/` glamsterdam set exceeded the GitHub ~100 MB limit.

## Notes

Upstream glamsterdam tarballs unpack as `fixtures/blockchain_tests/for_<fork>/…`. We copy only `state_tests` / `blockchain_tests` we consume (not engine-x, sync, or transaction tests).

Local download cache (gitignored via `fixtures*`): `fixtures_*.tar.gz` and extract dirs. Do not re-download if the tarball is already present and the sha256 matches the GitHub asset.

Large pushes may need a bigger HTTP buffer ([details](https://stackoverflow.com/questions/66366582/github-unexpected-disconnect-while-reading-sideband-packet)):

```shell
git config --global http.postBuffer 157286400
```
