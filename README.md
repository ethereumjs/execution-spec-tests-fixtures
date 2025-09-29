# execution-spec-tests-fixtures

Fixtures from the official Ethereum test releases from [execution-spec-tests](https://github.com/ethereum/execution-spec-tests) for internal consumption.

Following fixtures are included:
- [fusaka-devnet-5@v2.1.0](https://github.com/ethereum/execution-spec-tests/releases/tag/fusaka-devnet-5%40v2.1.0)
  - `fixtures/state_tests/osaka/`

## Notes

Due to large file uploads local git config HTTP POST might need an update following [this answer](https://stackoverflow.com/questions/66366582/github-unexpected-disconnect-while-reading-sideband-packet):

```shell
git config --global http.postBuffer 157286400
```