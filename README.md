# Substrate Cumulus Parachain Template

A new [Cumulus](https://github.com/paritytech/cumulus/)-based Substrate node, ready for hacking ☁️..

This project is originally a fork of the
[Substrate Node Template](https://github.com/substrate-developer-hub/substrate-node-template)
modified to include dependencies required for registering this node as a **parathread** or
**parachain** to a **relay chain**.

The stand-alone version of this template is hosted on the
[Substrate Devhub Parachain Template](https://github.com/substrate-developer-hub/substrate-parachain-template/)
for each release of Polkadot. It is generated directly to the upstream
[Parachain Template in Cumulus](https://github.com/paritytech/cumulus/tree/master/parachain-template)
at each release branch using the
[Substrate Template Generator](https://github.com/paritytech/substrate-template-generator/).

👉 Learn more about parachains [here](https://wiki.polkadot.network/docs/learn-parachains), and
parathreads [here](https://wiki.polkadot.network/docs/learn-parathreads).


🧙 Learn about how to use this template and run your own parachain testnet for it in the
[Devhub Cumulus Tutorial](https://docs.substrate.io/tutorials/v3/cumulus/start-relay/).

A light client version of the UI is available at https://github.com/aaely/light-client-ui. You will need to 
add your wallet address to the chain spec to get access to funds because the keyring package is not available
with webpack 5, which is a requirement for the smoldot-light-node. I am unable to access the injected dev 
accounts without the keyring package for transfers of funds. To do this, do the following:

(assuming you already have rust, node, and npm installed)
cargo build --release
./target/release/parachain-collator build-spec --chain local > ChainSpecPlain.json

Open the created ChainSpecPlain.json file and add your address into the array under "balances".

./target/release/parachain-collator build-spec --chain ./ChainSpecPlain.json --raw > ChainSpecRaw.json

In the UI, you will need to ensure the created chain_spec file is imported in the /src/Recoil/recoil.tsx file. I have not been able to get this to sync correctly as of yet, but, upon returning the api object,and in theory, everything should work exactly as they did on the WsProvider version of the wrapper.
