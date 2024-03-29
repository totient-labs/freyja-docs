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
  freyjaContractAddresses: new Map([[
    39, "0x08575118e7fe21e31e25791b3ef5507518ce67dd"
  ]]),
  relayerFeeAddress: "0x75e8ea1abd794bf1ecb2a895ce4d0f2388abb62d",
  relayerFee: new BigNumber("0.03"),
  expirationWindow: 15 * 60
};

let p = new FreyjaLiquidityProvider(config);

const [order, signature] = p.createSignedSwap(
  39,
  "0x4086b2d7eb716ca7c81b680792b8ecd2cfa2a7c8", // fromTokenAddress
  "0x151b77a9abd9d4b950b2ad87c5e7a35d917feba4", // toTokenAddress
  new BigNumber("100000000000000000000"), // toTokenAmount
  new BigNumber("74262065361517630937327166920207355685869415776792017265093194255793485770502"), // nonce
  new BigNumber("164587396890052500000") // quote
);

console.log(order);
console.log(signature);
```
### Freyja Contract Addresses
Freyja's contract is deployed at:

`Mainnet` - `N/A`

`Testnet` - `0x08575118e7fe21e31e25791b3ef5507518ce67dd`
