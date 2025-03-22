# Solana bootcamp projects practice - 1 favorites

## Memo

1. test file provider will parse and use information in Anchor.toml.
2. anchor program macro is _declarative_, means mecro ecapsulates logics inside, eg:

- program context will default set the user as current wallet's owner, and `#[derive(Accounts)]` will automatically derivce all related accounts information.
- We don't need to code common logic, just provide account struct.

### About keys:

- User's wallet has public key & private key.
- Program has public key & private key, and anchor default use BPF Upgradeable Loader to deploy program to make it upgradeable.
- PDA = f(seed(userPublicID), bump) to create key without private key but only public key. So there is no way to use private key to change PDA corresponding account, only the user can change it.

### About CLI:

- **Solana CLI**: keygen, onchain data retrieve, deploy & upgrade program, revoke instruct
- **Cargo**: create, build, test, manage package for rust project
- **Anchor**: create, build, test, deploy anchor project

\*_During development:_  
Cargo: Manage dependencies and compilation  
Anchor: Build, test, deploy  
Solana CLI: Query chain state, debug

_Production deployment:_  
Anchor: Automated deployment process  
Solana CLI: Fine-grained control over deployment options and parameters

### About unit test:

1. why someRandomGuy cannot change the user's favorites?
   _Because setFavorites context defalut use wallet owner as user, and the PDA is derived from user's public key. So for the favorites account in context, only wallet user can sign its transaction._
