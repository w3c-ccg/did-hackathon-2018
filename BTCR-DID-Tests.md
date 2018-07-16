## A list of BTCR based DIDs & transactions on Bitcoin Testnet for testing resolvers

### Test #1 — BTCR DID MVP (Minimum Viable Product) Valid & Unrevoked DID Document Example

Under BTCR Method 1.0, any existing legacy P2PKH transaction with an unspent tip can be a valid BTCR DID. No OP_RETURN or other information in the transaction is required. This means that even old dust (small change from other payments) can be used.

Right now we don't support newer segwit P2WPKH transaction, but should be possible in 1.0. However P2SH and P2WSH will have to wait.

This test also tests tsref encoders — by default, output 0 is the revocation/rotation "tip", which is correct in this case.

> TESTNAME: TEST #1 BTCR DID MPV Test
> TRANSACTION ID: 80871cf043c1d96f3d716f5bc02daa15a5e534b2a00e81a530fb40aa07ceceb6
> TXREF: did:btcr:x705-jzv2-qqaz-7vuz
> CONFIRMED IN BLOCK: 1353983
> BLOCKINDEX: 83
> OUTPUTINDEX: 0
> TIP ADDRESS: 80871cf043c1d96f3d716f5bc02daa15a5e534b2a00e81a530fb40aa07ceceb6
> IMPLICIT DID DOCUMENT:
```json
{
    "@context": "https://w3id.org/btcr/v1",
    "id": "did:btcr:x705-jzv2-qqaz-7vuz",
    "publicKey": [
        {
            "id": "did:btcr:x705-jzv2-qqaz-7vuz#keys-1",
            "owner": "did:btcr:x705-jzv2-qqaz-7vuz",
            "type": "EdDsaSAPublicKeySecp256k1",
            "publicKeyHex": "02e0e01a8c302976e1556e95c54146e8464adac8626a5d29474718a7281133ff49"
        }
    ],
    "authentication": [
        {
            "type": "EdDsaSAPublicKeySecp256k1Authentication",
            "publicKey": "#keys-1"
        }
    ],
    "SatoshiAuditTrail": [
        {
            "chain": "testnet",
            "blockhash": "0000000000000035b43f523828f38f5c97e5e34c524f7971940602d9c7d425ed",
            "blockindex": 83,
            "outputindex": 1,
            "blocktime": "2018-07-16T19:27:31.572Z",
            "time": 1499501000,
            "timereceived": "2018-07-16T19:27:31.572Z",
            "burn-fee": -0.05
        }
    ]
}
```
> SUPPLEMENTARY DID Document: UNDEFINED
> CONSTRUCTED DID Document:
```json
{
    "@context": "https://w3id.org/btcr/v1",
    "id": "did:btcr:x705-jzv2-qqaz-7vuz",
    "publicKey": [
        {
            "id": "did:btcr:x705-jzv2-qqaz-7vuz#keys-1",
            "owner": "did:btcr:x705-jzv2-qqaz-7vuz",
            "type": "EdDsaSAPublicKeySecp256k1",
            "publicKeyHex": "02e0e01a8c302976e1556e95c54146e8464adac8626a5d29474718a7281133ff49"
        }
    ],
    "authentication": [
        {
            "type": "EdDsaSAPublicKeySecp256k1Authentication",
            "publicKey": "#keys-1"
        }
    ],
    "SatoshiAuditTrail": [
        {
            "chain": "testnet",
            "blockhash": "0000000000000035b43f523828f38f5c97e5e34c524f7971940602d9c7d425ed",
            "blockindex": 83,
            "outputindex": 1,
            "blocktime": "2018-07-16T19:27:31.572Z",
            "time": 1499501000,
            "timereceived": "2018-07-16T19:27:31.572Z",
            "burn-fee": -0.05
        }
    ]
}
```
#### Test #1 — BTCR DID MVP (Minimum Viable Product) Valid & Unrevoked DID-based Verifiable Credential

This verifiable credential was properly signed & valid (using https://json-ld.org/playground-dev/), and a check of the transaction output address should prove there is no transaction associated with it, thus this credential should be considered unrevoked.

Essentially this is a self-signed claim, with ID of /credential/0 that says that it claims it calls itslef "BTCR Test #1" and that it knows did:btcr:xyv2-xzyq-qqm5-tyke, which is Christopher Allen's test DID.
```json
{
  "@context": [
    "https://w3c.github.io/vc-data-model/vocab/context.jsonld",
    "http://schema.org/",
    "https://w3id.org/security/v1"
  ],
  "id": "did:btcr:x705-jzv2-qqaz-7vuz",
  "type": [
    "VerifiableCredential"
  ],
  "claim": {
    "id": "did:btcr:x705-jzv2-qqaz-7vuz/credential/0",
    "alternatename": "Test #1 — BTCR DID MVP Valid & Unrevoked",
    "knows": "did:btcr:xyv2-xzyq-qqm5-tyke"
  },
  "signature": {
    "type": "EcdsaKoblitzSignature2016",
    "created": "2018-07-16T21:25:37Z",
    "creator": "ecdsa-koblitz-pubkey:02e0e01a8c302976e1556e95c54146e8464adac8626a5d29474718a7281133ff49",
    "signatureValue": "H1dv6EXaRrkDX+hvmfbR+cMsbh5iTvvP8DtFe/xoxFpUKd/6E7KVuzqSar6cHjIH7Ti1gnla36SAnNL/DVQ9YzM="
  }
}
```

 (This Verifiable Claim is based an a pre-release version of the spec and signature method — Contact ChristopherA@LifeWithAlacrity.com if you need the WIF private key to update this credential).

