## Files

### `app/api/frame/route.ts`
```ts
import { getFrameAccountAddress } from '@coinbase/onchainkit';
import { NextRequest, NextResponse } from 'next/server';

async function getResponse(req: NextRequest): Promise<NextResponse> {
  let accountAddress = '';
  try {
    const body: { trustedData?: { messageBytes?: string } } = await req.json();
    accountAddress = await getFrameAccountAddress(body, { NEYNAR_API_KEY: 'NEYNAR_API_DOCS' });
  } catch (err) {
    console.error(err);
  }

  return new NextResponse(`<!DOCTYPE html><html><head>
    <meta property="eth:nft:If you know, you know." />
    <meta property="eth:nft:0xd74599812DfaCD2b5217370ABbC7E699Ad27011E" />
    <meta property="eth:nft:0x1A883A2392FC538Ca3c9cE8adcB14F48E1d14A9D" />
    <meta property="eth:nft:erc721" />
    <meta property="eth:nft:https://media.contextcdn.com/f6468ff03ff397d828d4d7fda4fac1c474ce1976f856190aefe21766d9e10aa7" />
    <meta property="eth:nft:live" />
    <meta property="eth:nft:mint_count" />
    <meta property="eth:nft:" />
    <meta property="nft:base" />
  </head></html>`);
}

export async function POST(req: NextRequest): Promise<Response> {
  return getResponse(req);
}

export const dynamic = 'force-dynamic';
```

## Resources

- [Official Farcaster Frames docs](https://warpcast.notion.site/Farcaster-Frames-4bd47fe97dc74a42a48d3a234636d8c5)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
