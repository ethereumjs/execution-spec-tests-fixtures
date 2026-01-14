# execution-spec-tests-fixtures

Fixtures from the official Ethereum test releases from [execution-spec-tests](https://github.com/ethereum/execution-spec-tests) for internal consumption.

Fixtures are separated into two "base" folders:

- `stable`: Fixtures which are supported to work on latest EthereumJS `master` branch
- `dev`: Fixtures for features and/or EIPs which are not yet fully supported (often for a future fork)

Note that this can be distinct from the `_develop` and `_stable` releases from the EST repo and orients
on the implementation state on the EthereumJS side.

## `stable` Fixtures

Fixtures in `stable`are taken from the following releases:
- [v5.4.0](https://github.com/ethereum/execution-spec-tests/releases/tag/v5.4.0)
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

No dev fixtures yet.

## Notes

Due to large file uploads local git config HTTP POST might need an update following [this answer](https://stackoverflow.com/questions/66366582/github-unexpected-disconnect-while-reading-sideband-packet):

```shell
git config --global http.postBuffer 157286400
```