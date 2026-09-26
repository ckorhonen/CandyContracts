# Repository Guide

- Solidity contracts are configured by `hardhat.config.js`, which targets Solidity 0.8.11.
- The README documents `npm install`, `npx hardhat compile`, and `npx hardhat test`; use the focused compile/test command for a contract change.
- The configured `accounts` task prints signer addresses. Keep private keys and network credentials out of tracked files, and do not use a live network merely to validate instruction changes.

Run the documented commands from the repository root with Node/npm and the locked Hardhat dependencies installed. `contracts/CandyCreatorV1A.sol` is the main NFT contract; `contracts/modules/`, `token/`, and `eip/` provide supporting behavior. `contracts/@openzeppelin/` is vendored code; avoid broad edits there. `test/` covers basic behavior, permissions, payments, public minting, and whitelist minting; `scripts/` contains execution examples, not test gates.

Use Hardhat's default local network for compile/tests, without a live `--network` override. For example, `npx hardhat test test/Permissions.js` focuses permission behavior; run other relevant suites for changed mint/payment semantics. Compiler acquisition may require network/cache access, which is a prerequisite to report rather than a passing compilation. Preserve contract interfaces and financial invariants unless explicitly changed, keep unrelated work intact, and report compiled contracts, executed tests, and unverified deployment behavior. Do not deploy or send real transactions for routine checks.
