# execution-spec-tests-fixtures

Fixtures from the official Ethereum test releases from [execution-spec-tests](https://github.com/ethereum/execution-spec-tests) for internal consumption.

Fixtures are separated into two "base" folders:

- `stable`: Fixtures which are supported to work on latest EthereumJS `master` branch
- `dev`: Fixtures for features and/or EIPs which are not yet fully supported (often for a future fork)

Note that this can be distinct from the `_develop` and `_stable` releases from the EST repo and orients
on the implementation state on the EthereumJS side.

## `stable` Fixtures

Fixtures in `stable` are taken from the following releases:
- [v5.4.0](https://github.com/ethereum/execution-spec-tests/releases/tag/v5.4.0) | Dec 7, 2025 | Osaka + some pre-Osaka tests
  - `state_tests/osaka/`
  - `state_tests/prague/`
  - `state_tests/cancun/`
  - `state_tests/shanghai/`
  - `blockchain_tests/osaka/`

Test exclusions (file size limit GitHub):
- `blockchain_tests/osaka/eip7934_block_rlp_limit/test_block_at_rlp_size_limit_boundary.json` (101 MB)
- `blockchain_tests/osaka/eip7934_block_rlp_limit/test_block_rlp_size_at_limit_with_all_typed_transactions.json` (168 MB)
- `blockchain_tests/osaka/eip7934_block_rlp_limit/test_fork_transition_block_rlp_limit.json` (134 MB)

## `dev` Fixtures

The fixtures in `dev` currently consist of multiple consecutive releases to ease development (different release characteristics):
- [bal@v5.0.0](https://github.com/ethereum/execution-spec-tests/releases/tag/bal%40v5.0.1) | Jan 27, 2026 | Various Amsterdam EIPs | BAL definitions included
  - `blockchain_tests/amsterdam/v500_mixed_with_other_eips/`
- [bal@v3.0.1](https://github.com/ethereum/execution-spec-tests/releases/tag/bal%40v3.0.1) | Jan 13, 2026 | Only EIP-7928 Block Level Access Lists (BAL) | No mixture, no BAL definitions, already EVM tests passing
  - `blockchain_tests/amsterdam/v301_single_bal_no_bal_defs/eip7928_block_level_access_lists/`
- [bal@v2.0.0](https://github.com/ethereum/execution-spec-tests/releases/tag/bal%40v2.0.0) | Dec 12, 2025 | Only EIP-7928 Block Level Access Lists (BAL) | No mixture, BAL definitions, somewhat outdated
  - `blockchain_tests/amsterdam/v200_bal_defs_somewhat_outdated/eip7928_block_level_access_lists/`

## Notes

Due to large file uploads local git config HTTP POST might need an update following [this answer](https://stackoverflow.com/questions/66366582/github-unexpected-disconnect-while-reading-sideband-packet):

```shell
git config --global http.postBuffer 157286400
```