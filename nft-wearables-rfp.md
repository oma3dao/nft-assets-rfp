# OMA3 NFT Wearables Request for Proposals (RFP)
# OMA3 NFT Working Group (NFTWG)

## Introduction

This Request for Proposals (RFP) is released by OMA3’s NFT Working Group (NFTWG). The purpose of this RFP is to solicit specification proposals for a cross-platform NFT wearables standard.  It is also a call for non-members with expertise in this area to join OMA3 and help create the standard.

The NFT Wearables standard is defined by the [Metaverse Standards Forum use case document](https://docs.google.com/document/d/1DaHzeooAMzg3fYxXh3FlIgPPlCPFt6Ot8avKp-sqtBY/) entitled “NFT Metadata for Wearables in the Metaverse”.  

The spark for this effort comes from OMA3 member companies that want to launch an NFT wearables collection that can be used interchangeably between their metaverse platforms.  These companies will move forward with the development of this project in parallel with this standardization effort.  The project can be modified later to match the final specification.

## Scope

This RFP leverages the MSF use case document referred to above, but uses different language that is more conducive to measuring the effectiveness of standards proposals.  This RFP creates a more formal description of actors and use case flows. The RFP then outlines high-level threats for circumventing the system.  The RFP finally details a comprehensive range of functional and non-functional requirements. However, this document does not delve into the architectural or design aspects of the system, as these will come from proposals submitted in response to this RFP. This RFP serves to offer a clear acceptance criteria that can be used to judge such specification proposals.

## Use Cases

For more information on the value of use cases, please see Section 3 of the [OMA3 Working Group Process](https://github.com/oma3dao/working-group-process/blob/main/working-group-process.md). 

### Actors

In this RFP, the main actors are as follows:

  * NFT: The immutable element that represents the digital asset that has its data baked into the on-chain data of a blockchain.  An individual NFT can be from the same collection but have different IDs from the other NFTs in the collection.  An NFT can also be a bundle of NFTs that can be identified, sold, and transferred with a single transaction.
  * Creator: Design and mint wearable NFTs with standardized metadata to ensure compatibility across different metaverse platforms.  Creator can be a Platform.
  * Minting Tool: The app that is used to mint NFT. Import files, export metadata.
  * Platform: Provide environments where users can create, import, equip, and use NFT wearables. These platforms must support the standardized metadata format to enable interoperability.
  * User: Interact with the NFTs by purchasing, equipping, and exporting wearables. They expect wearables to function consistently across different platforms.
  * Avatar: the representation of the User in a Platform.
  * Blockchain Infrastructure: Store the data, including metadata and ownership details of the NFT wearables. They are responsible for ensuring secure and verifiable ownership and provenance.  This infrastructure may include offchain servers.
  * Marketplace: Facilitate the discoverability and trading of NFT wearables across different platforms.  

![Figure1](https://github.com/oma3dao/nft-assets-rfp/blob/main/figure%201.png)  
_Figure 1: Main actors_  

### Use Case

Preconditions:
  * Minting Tool is compatible with standards specified by the System.
  * System supports the Blockchain Infrastructure of the Platforms.

Acquisition:
  1. Creator uses Minting Tool and System to create NFT and associated metadata on Blockchain Infrastructure.
  2. Optional:  Creator puts NFT on Marketplace.
  3. User acquires NFT from Platform or Marketplace.
  4. User attaches NFT to their Avatar using the System and optionally Platform.

Display:
  1. User participates in a Platform with their Avatar and NFT.
  2. Platform reads information on the Avatar and NFT using the System and displays the NFT attached to the Avatar in the Platform in a way compatible with the Platform yet still recognizable as the NFT by the User and Creator.

Sale or Trade:
  1. User uses Platform or a Marketplace to sell NFT to or trade with another user.
  2. Platforms use System to discover NFT is no longer owned by User.
  3. Platforms no longer display the NFT attached to the User’s Avatar after the sale.

Avatar Transfer:
  1. User uses System and Platform to attach NFT to a second Avatar.
  2. User participates in a Platform with the second Avatar.
  3. Platform recognizes the NFT is now attached to the second Avatar and displays NFT with the second Avatar.

## Threats

For more information on the value of a threat model, please see Section 4 of the [OMA3 Working Group Process](https://github.com/oma3dao/working-group-process).  The following is a list of mechanisms that can be used to circumvent NFT royalties.

  1. Infrastructure Compromise:
        a. Minting Tool can be compromised or vulnerable to exploitation.
        b. Vulnerabilities in System code could be exploited to steal assets or manipulate application functionality.
  2. Cross-Platform Vulnerabilities: Blockchain Infrastructure transfer mechanism can be compromised.
  3. Platform could represent the NFT in a way not approved by the Creator.
  4. System can attach NFT to the wrong Avatar.
  5. User can attach an NFT owned by someone else to the User’s Avatar.
  6. NFT can be simultaneously displayed on multiple Avatars owned by the User in contradiction to NFT Creator’s desires.
  7. Creators minting NFTs that violate the copyright of another Creator.
  8. Creators pretending to be someone they are not to produce counterfeit/knockoff/bootleg assets.
  9. Malicious actors embed code in metadata causing harm to Platform or users

## Requirements

The below requirements are used as a measure to compare different System design options.  Some of the requirements are required, some are optional.  For more information on how to interpret the language, please see Section 5 of the [OMA3 Working Group Process document](https://github.com/oma3dao/working-group-process). 

### 1. Technical
    1.1. System SHALL give an accurate description of how the NFT can be attached to the Avatar so there is consistency between Platforms.
    1.2  System MAY support information like weight and dimensions that allow Platforms to treat the dynamics of the NFT consistently.
    1.3  System SHOULD support a flexible yet consistent unit system when describing the NFT.
    1.4  System SHOULD enable an open marketplace of SDKs that allow Platforms to interact with NFTs and System.
    1.5  System SHOULD allow an NFT to specify how it attaches Avatars of different sizes
### 2. Interoperability Requirements
    2.1  NFT SHOULD be able to be depicted in any Platform.
    2.2  System MAY leverage existing wearables interoperability technology currently used by Platforms.
    2.3  System MAY define NFT metadata standards to describe how the NFT works with the System and Platforms.
    2.4  System MAY allow for a migration path from existing proprietary metadata formats to the System standard.
    2.5  System SHOULD be consistent with Schema.org when possible.
    2.6  System SHOULD allow any virtual machine to be compatible with the System.
    2.7  System SHALL be compatible with the ERC-721 standard.
    2.8  System MAY support Unity, Unreal Engine, Godot, CryEngine, Lumberyard, GameMaker and other rendering mechanisms.
    2.9  System MAY support the VOX, glTF/GLB, FBX, VRM, HAnim, X3D, MetaHuman, OBJ, and AOUSD/USDZ file standards.
### 3. Creator Rights
    3.1  System MAY give Creator the option to control how the NFT is depicted in a Platform
### 4. User Rights
    4.1  System SHOULD prevent a User from using the NFT on multiple Avatars if the NFT specifies this limitation.
    4.2  System SHOULD prevent non-owners of an NFT from displaying the NFT with their Avatars if the NFT specifies this limitation
### 5. Scalability
    5.1  The System SHOULD support thousands of Platforms.
    5.2  The System SHOULD support millions of NFTs.
### 6. Governance
    6.1 Governance of the System, should it exist, SHOULD be controlled by OMA3
