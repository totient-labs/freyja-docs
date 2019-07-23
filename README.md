# Freyja v1.0.0 Documentation
Freyja is a lightweight decentralized exchange protocol on Vechain. It provides the infrastructure to facilitate VIP180 token swaps.

### Javascript Library
```
npm install @totient-labs/freyja
```

### Liquidity Provider Example Code
```
import { FreyjaLiquidityProvider } from "@totient-labs/freyja";
import { BigNumber } from "bignumber.js";

let config = {
  providerPrivateKey: "0xdce1443bd2ef0c2631adc1c67e5c93f13dc23a41c18b536effbbdcbcdb96fb65",  // First local node PK for testing
  freyjaContractAddress: "0x08575118e7fe21e31e25791b3ef5507518ce67dd",
  relayerFeeAddress: "0x75e8ea1abd794bf1ecb2a895ce4d0f2388abb62d",
  relayerFee: new BigNumber("0.03"),
  expirationWindow: 15 * 60
};

let p = new FreyjaLiquidityProvider(config);

const [order, signature] = p.createSignedSwap(
  "0xb69ded9f0da15d240ee6803dacd7fcf68744e8ff", // fromTokenAddress
  "0x1b8ec6c2a45cca481da6f243df0d7a5744afc1f8", // toTokenAddress
  new BigNumber("100000000000000000000"), // toTokenAmount
  new BigNumber("79229934413466317933680713858907708646367323220373121180078535278650577904653"), // nonce
  new BigNumber("300000000000000000000") // quote
);

console.log(order);
console.log(signature);
```
### Freyja Contract Addresses
Freyja's contract is deployed at:

`Mainnet` - `N/A`

`Testnet` - `0x08575118e7fe21e31e25791b3ef5507518ce67dd`
