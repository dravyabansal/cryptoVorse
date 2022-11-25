<h1>
 Welcome to The Crypto Studio
</h1>

<p>
<img src="./public/logo.webp" alt="alt text" width="200" height="200"/>
</p>

[Demo video](https://youtu.be/e4lI4cYYG3U)

Our application is hosted on those links 
 * [stable dapp link](https://the-crypto-studio.vercel.app/)
 * [Valist IPFS link](https://bafybeieekfc5qpb5253kom33wlw3hb75w62ug3ob34upylkwf22ikf7axu.ipfs.gateway.valist.io/)
 * [Spheron IPFS link](https://the-crypto-studio-20be90.spheron.app/)
 

Authors
 * [nijoe1](https://github.com/nijoe1)
 * [Suhel-Kap](https://github.com/Suhel-Kap)

## Description
Crypto Studio is a Dynamic ERC721 Collection built for digital artists. Under the hood, we are utilizing tableland a new narrative that brings SQL into smart contracts that unlocked us to create a native dynamic experience for our users NFTs. We are also leveraging IPFS for storing (images - HTML - mp3) files for our NFTs into the network through NFT.STORAGE. 

The Crypto Studio Collection supports all kind of NFTs like :

  * Interactive visualizers using the CID of HTML pages 
  * Song Albums for singers,trapers,electronic music creators
  * Just classic Image NFTs
  
We provide them all of them from our UI!

[Collection on OpenSea](https://testnets.opensea.io/collection/cryptostudio-2xpo9crut9)

Each Artist/User first has to mint a Space. A space is like his signature on top of his NFTs. Digital artists can create a whole Collection|Album based on their space.A space is nothing more that a pair (trait_type = SpaceName , value = "A name space") on top of every NFT. Artists can only mint an NFT on top of their owned spaces. If they dont grab a unique space they are not allowed to mint their creations.

Our platform is open to everyone. For now, we are providing some precoded dynamic & interactive audio visualizers for newcomers to come and mint them with their preferred soundtrack and change it whenever they want to.
  * The future of CryptoStudio is to make it more accessible to the public. We want to make it so that anyone can create their own Dynamic NFTs with zero coding    experience by creating a free and open to use web-based tool for designing and developing dynamic 2D & 3D NFT models by introducing **The Studio Playground**
  * We also want to make it so that digital artists can come and build cool things by providing a guide (DOCS) of how to use our native Dynamic features written   natively inside the CryptoStudio smart contract on top of their creations.


Our NFTs are based on HTML files and a p5.js script for playing the visualizer and the sound. In the upcoming versions we are going to use more libraries like p5.js.

The HTML file is getting uploaded on IPFS and that derives the animation_url that is part of the NFT metadata.

The dynamic features for changing the audio track of an NFT come into place by using the changeNFTaudio function which is located inside our contract. This function can be called only by the Owner of an NFT that wants to change the soundtrack of his NFT. The contract interacts with tableland to update the audio column of that NFT with the new audio CID!
  * We also added the addAttribute & updateAttribute functions for users to monetize their NFTs us they want ( Add , remove , update ) attributes and create new   dynamic utilities

NFT owners can add and update their NFT metadata by interacting with the cryptoStudio Smart contract as they want except the animationURL and the spaceName trait attributes, to keep the basic art and the creatorSignature immutable.

**Here is the prototype Architecture of our NFTs** 

<p align="left">
<img src="./public/architecture.png"/>
Here is an HTML example :
<br />
https://github.com/Suhel-Kap/the-crypto-studio/blob/main/constants/nfts/nft7.html
</p>



## SOCIAL_LAYER
 
Each user has his profile based on the ceramic network using orbis.club

We also include a public grouChat for anyone into cryptoStudio to connect with each other. This is established by using Orbis.club and ceramic network which is an IPFS implementation!

Each collection space contains a seperated group chat with tokengated access controll by leveraging Orbis.club & lit.protocol for the spaceNFT owners and give them a decentralized discord experience.

# Technologies Used

  ## IPFS & FILECOIN usage
  
  This is how we used IPFS & FILECOIN
   <br />
   <br />
     **NFT.STORAGE**
     <br />
       All the files that consist an NFT are stored on the IPFS network using NFT.STORAGE
       The code snippets that are using NFT.STORAGE modules are located here:
       <br />
        **https://github.com/Suhel-Kap/the-crypto-studio/blob/main/hooks/useNftStorage.ts**
        <br />
        **https://github.com/Suhel-Kap/the-crypto-studio/blob/main/pages/create-nft.tsx**
        <br />
        **https://github.com/Suhel-Kap/the-crypto-studio/blob/main/pages/api/updateHtml.ts**
    <br />
    <br />
    **SPHERON**
    <br />
         We uploaded our frontend into IPFS using Spheron.
         Here is the Spheron IPFS hosted frontend url of The Crypto Studio :
         <br />
         **https://the-crypto-studio-20be90.spheron.app/**
    <br />
    <br />
    **VALIST**
    <br />
         We uploaded our frontend into IPFS using Valist.
         Here is the Valist IPFS hosted frontend url of The Crypto Studio :
         <br />
         **https://bafybeieekfc5qpb5253kom33wlw3hb75w62ug3ob34upylkwf22ikf7axu.ipfs.gateway.valist.io/**
    <br />
    <br />
    **CERAMIC NETWORK** which is based on the IPFS libP2P stack
    <br />
        We are leveraging Orbis.club for our users Profiles and for creating communication discord like channels for each Space
        but also a unified and open GroupChat for the Crypto Studio users!
        <br />
         **https://github.com/Suhel-Kap/the-crypto-studio/blob/main/components/ChatContent.tsx**
         <br />
         **https://github.com/Suhel-Kap/the-crypto-studio/blob/main/components/ChatBox.jsx**
         <br />
         **https://github.com/Suhel-Kap/the-crypto-studio/blob/main/pages/create-nft.tsx**
         <br />
         **https://github.com/Suhel-Kap/the-crypto-studio/blob/main/components/UpdateProfile.tsx**
         <br />

   ## Tableland usage 
  Tableand is used to create the metadata layer of the Crypto Studio NFTs inside the Smart Contract
     take a deeper look in the SmartContract 
     <br />
     
  Here are the data inside the SQL Tables. Only our SmartContract has access control on the tables!!!
  Check our decentralized databases content :
     <br />
  main_table = **https://testnet.tableland.network/query?s=SELECT%20*%20FROM%20main_80001_3764**
        
  attribute_table = **https://testnet.tableland.network/query?s=SELECT%20*%20FROM%20attribute_80001_3765**
        
  spaces_table = **https://testnet.tableland.network/query?s=SELECT%20*%20FROM%20space_group_80001_3766**
<br />
  ## SmartContract
<br />
  Our contract is deployed and verified on polygon mumbai here is the mumbaiScan Link . 
<br />
https://mumbai.polygonscan.com/address/0xCa23f7a27bF973bb9E21a6FA8bA21cd4a89A51DD#code

 
 ---
 
