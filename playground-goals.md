# Goals for a BTCR playground

Here are some proposed goals for BTCR playgrounds and a programmer's tutorial in particular.

## Actions in any playground
What actions should be available in any BTCR playground?
1. create DID
2. validate DID (offline validation)
3. lookup DID
4. verify DID (including BTC check)
5. post DID indirectly
6. post DID directly (if possible)
7. revoke DID
8. rotate DID
9. test suite
10. test net v main net examples

## Programmer's tutorial
The goal of the tutorial is to walk a programmer through the parts of creating and using DIDs in a way that will make it easier for them to understand and use DIDs in their own work.

1. Present a programmable interface (sandbox)
2. Walk through from first principles through to constructing a working library
3. Provide exercises and worked-through examples
4. Be language specific (Joe is working on a JavaScript tutorial.)



## MVP Wallet

A really rough-draft of high level MVP wallet.

1. Master Seed

2. - Create master seed (BIP32)

   - Archive and test recovery of master seed (BIP 39)

   - - Possibly update to use instead new Lightning varient of BIP39
     - Possibly save recovery words using updated wordset
     - Possibly save recovery words as poem

   - Derive Identity Root, Account Roots, and children of first Account Roots used for DIDs

   - This might be possibly a different app, say on an iPod Touch, that creates the children addresses for the DID wallet app via QR codes.

3. create my DID

4. - Fund first child of Account root

   - Create DID Document Extension

   - - Post DID Document Extension to IPFS (unsigned) or BTCR Service Endpoint (signed) such as Github

   - Create initial DID transaction with DID Document Extension

5. revoke my DID

6. - Possibly print pre-signed revocation transaction as QR code that can allow anyone to revoke that DID.

7. rotate my DID to next child address with a new transaction and DID Document

8. - Alternatively rotate to a brand new seed’s child for special cases
   - Possibly a pre-signed rotation transaction.

9. lookup other BTC DIDs and validate them (via explorer service or SPV validation)

10. Issue web of trust simple endorsements about other DIDs, and share them back to holder, optionally post them publicly as IPFS documents or appended to BTCR ServiceEndpoint

11. Verify other web of trust simple endorsements about me, save them locally.

 