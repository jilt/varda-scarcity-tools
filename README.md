# Varda Scarcity tools 
Built to allow floor price control for large NFT collections through DeFi Farming mechanics on NEAR.
These tools make large usage of [Open-Rpc Near Client Generator](generator) and the [Open RPC Near Token Standards](https://github.com/swappland/open-rpc-near-token-standards). Refer to the
OpenRPC specification and the JSON schema specification to get started.


[generator]: https://github.com/shipsgold/open-rpc-near-client-generator
[market-spec]: https://playground.open-rpc.org/?schemaUrl=https://raw.githubusercontent.com/swappland/swappland-market-contract-spec/main/build/openrpc.json&uiSchema[appBar][ui:splitView]=false&uiSchema[appBar][ui:input]=false&uiSchema[appBar][ui:examplesDropdown]=false
[openrpc]: https://open-rpc.org

## Goal

This tool allows NFT collectors to swap their nfts with the Varda smart contract allowing them to get seed tokens from [the ref.finance farms smart contracts](https://guide.ref.finance/developers-1/cli-farming#stake-unstake-seed)
or farming rewards from [the burrowland farming contracts](https://github.com/NearDeFi/burrowland/blob/main/contract/API.md)
The Investor that will use this tool on his website or metaverse plot will have to invest in one of these two DeFi exchanges in order for his collections' owners to be able to swap their collectibles for DeFi assets, ensuring the floor price of the collection not to go too low.

## Use Case

**Brian** owns Mr.Brownie NFTs and needs to seel it asap
**Joe** owns the Mr.Brownie NFT collection and doesn't want **Brian** to sell for a low price
**Joe** invests 40% of the collection's earnings on a DeFi farms and get regular rewards for it, he decides to add the scarcity tool to the collection's website in order for Brian not to sell too low his NFTs, because he can always redeem farming tokens (the amount will depend on the invested amount and the percentage the owner decide to give while setting up the scarcity tool) while swapping NFTs with a Vault address that owns a part of the PFP collectibles.

**Brian** is not interested in DeFi farms and doesn't know what the swap is about but he understand that this gives him a sure amount of money for his collectible and so prefers to do the swap and then learn about DeFi rather than put his NFT on sale and have to wait for someone to buy it.
**Joe** gets the rewards of farming in the Vault address when people are selling his collectibles for an higher price than the value of the farming rewards.


### Installation 
```
npm install @swappland/market-contract-client
```

```ts
import SwapplandClient from "@swappland/market-contract-client"

const testnetContractId ="mkt.landofswapps.testnet"
const mainnetContractid = "mkt.swappland.near"

// Setup Purely for example
const accountId: string = "some_account_you_have_in_credentials.near"
const keystore = new keyStores.UnencryptedFileSystemKeyStore(`${os.homedir()}/.near-credentials`)
const near = new Near({
    networkId: "testnet",
    nodeUrl: "https://rpc.testnet.near.org",
    walletUrl: "https://wallet.testnet.near.org",
    explorerUrl: "https://explorer.testnet.near.org", 
    deps: {keyStore}, headers:{}})

// The only thing the client really needs  followed by the contractId
const account:Account = await near.account(accountId);

const client = new SwapplandClient({account, contractId: testnetContractId})

```

### Build 
```
npm install
npm run build
```

### Early days note.
It's early days and the interface is still subject to change depending on usecases that come up. 
A few methods still need to be deprecated around the adminstration of the contract here's a that was 
easy link to the [spec][market-spec](beware some non essential methods are now deprecated, but are pending removal from spec).


## Contributing

The specification is written in [OpenRPC][openrpc] uses the [Open-Rpc Near Client Generator](generator) and the [Open RPC Near Token Standards](https://github.com/swappland/open-rpc-near-token-standards). Refer to the
OpenRPC specification and the JSON schema specification to get started.


[generator]: https://github.com/shipsgold/open-rpc-near-client-generator
[market-spec]: https://playground.open-rpc.org/?schemaUrl=https://raw.githubusercontent.com/swappland/swappland-market-contract-spec/main/build/openrpc.json&uiSchema[appBar][ui:splitView]=false&uiSchema[appBar][ui:input]=false&uiSchema[appBar][ui:examplesDropdown]=false
[openrpc]: https://open-rpc.org

