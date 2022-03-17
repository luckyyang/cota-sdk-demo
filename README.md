A demo app showing how to use [CoTA SDK](https://github.com/nervina-labs/cota-sdk-js).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## Learn More

To learn more about CoTA SDK, take a look at the following resources:

- [CoTA SDK Code](https://github.com/nervina-labs/cota-sdk-js) - learn about the code.
- [CoTA Docs](https://developer.mibao.net/docs/develop/cota/overview) - docs that explain what is CoTA.

Any quesion please ask in our [Discussion](https://github.com/rebase-network/hello-world).

## A simple explanation for how to use the SDK
- 所有地址都需要注册 cota，没注册只能收，不能 claim/withdraw/transfer
- NFT 的 owner 可以 mint NFT 给任何人 Alice，tokenIndex 必须从 0x00000000 开始，依次递增
- owner mint 0x00000000 给 Alice 之后，Alice 可以：
	- 什么都不做。Alice 依然拥有 NFT 的所有权，只不过所有权记录在 owner 的 cota 中，没有记录在 Alice 自己的 cota 中
	- claim 给自己。这时所有权也记录在了 Alice 自己的 cota 中，这个操作在转移所有权之前是必要的，可以防止双花
	- claim 给自己，然后 withdraw 给 Bob
	- transfer（相当于 claim + withdraw）给 Bob
- 假设这时 Alice claim 0x00000000 之后，withdraw 给了 Bob
- 此时 Bob 可以做上面的 4 个操作：
	- 什么都不做
	- claim 0x00000000 给自己
	- claim 0x00000000 给自己，然后 withdraw 给 Charlie
	- 直接 transfer 给 Charlie
