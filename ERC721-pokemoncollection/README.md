# Pokemon Collection Example

## STEPS TO DEPLOY A NEW COLLECTION OF XXX (>100) NFTS
1. Create /image /nft folders
2. Add images to /images named from 0 to <XXX> (0.png, 1.png, 2.png)
3. Publish /images folder to IPFS as CARs. It produces an <Images IPFS URL>
4. Add metadata JSON files to /nfts folder named from 0 to XXX. Ensure all metadata files link to <Images IPFS URL>
5. Publish /nft folder to IPFS as CCARs type. It produces an <NFTs IPFS URL>
6. Open REMIX IDE and use <NFTs IPFS URL> as base URI in the smart contract code. 
7. Set in a environment variable the destination of the NFTs minted <DESTINATION ADDRESS>

The Smart Contract `PokemonCollection.sol` implements the basic functionality to deploy an NFT collection and to mint every NFT based on a base URI:

```js
    function _baseURI() internal pure override returns (string memory) {
        return "ipfs://<NFTs IPFS URL>/";
    }

```

Then you have two ways to mint every NFT:
- Minting every NFT in a single transaction:

```js
safeMint(msg.sender, "1");
```


- Minting all NFTs in the constructor

```js
    constructor(string memory name_, string memory symbol_) ERC721(name_, symbol_) {
        for (uint i = 0; i <= <XXX>; i++){
                _safeMint(<DESTINATION AADDRESS>, i);
        }
    }
```

## Examples: 

## <Images IPFS URL>

ipfs://bafybeifaa5x53logldqmhp32jay6j5pob5ictg2yotwrxdzle3rauf4w64/Pikachu.png
ipfs://bafybeifaa5x53logldqmhp32jay6j5pob5ictg2yotwrxdzle3rauf4w64/Squirtle.png
ipfs://bafybeifaa5x53logldqmhp32jay6j5pob5ictg2yotwrxdzle3rauf4w64/Bulbasaur.png
ipfs://bafybeifaa5x53logldqmhp32jay6j5pob5ictg2yotwrxdzle3rauf4w64/Charmander.png

They share the same base path <Images IPFS URL>: `ipfs://bafybeifaa5x53logldqmhp32jay6j5pob5ictg2yotwrxdzle3rauf4w64/`


## <NFTs IPFS URL> IPFS URI (CAR / .car

Pikachu:    ipfs://bafybeierekdpsansxskq5nyq3ujsugdlmy7fwpaq2rvdvzsnhg5cduezba/1
Squirtle:   ipfs://bafybeierekdpsansxskq5nyq3ujsugdlmy7fwpaq2rvdvzsnhg5cduezba/2
Bulbasaur:  ipfs://bafybeierekdpsansxskq5nyq3ujsugdlmy7fwpaq2rvdvzsnhg5cduezba/3
Charmander: ipfs://bafybeierekdpsansxskq5nyq3ujsugdlmy7fwpaq2rvdvzsnhg5cduezba/4

They share the same base path <NFTs IPFS URL>: `ipfs://bafybeierekdpsansxskq5nyq3ujsugdlmy7fwpaq2rvdvzsnhg5cduezba/`

IPFS CID <IPFS CID>: `bafybeierekdpsansxskq5nyq3ujsugdlmy7fwpaq2rvdvzsnhg5cduezba`

## Other Examples

## Individual IPFS URIs for NFTs: 
Pikachu:    ipfs://bafkreictyefww5sfaei6zgvinna4skk2dvuykc2kz2j7cx757qbzqsrkmy
Squirtle:   ipfs://bafkreic7olitla35uie25nkvtj677iinfduu24s6omaclqpqp2zz6j3muq
Bulbasaur:  ipfs://bafkreidn7g4jtd624bqshqzw3aasoh6puxp26hdi254txdfzsf5exlei6y
Charmander: ipfs://bafkreib6zgvduwipueciybyxnygopg4jn2x7nqajxsx4hoji4zwxx4fm2i
...