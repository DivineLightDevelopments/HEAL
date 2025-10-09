curl -L -o /tmp/meta.json https://nftstorage.link/ipfs/<CID>
shasum -a 256 /tmp/meta.json | awk '{print $1}'
