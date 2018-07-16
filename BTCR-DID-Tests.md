## A list of BTCR based DIDs & transactions on Bitcoin Testnet for testing resolvers

### Test #1 — BTCR DID MVP (Minimum Viable Product) Valid & Unrevoked DID Document Example

Under BTCR Method 1.0, any existing legacy P2PKH transaction with an unspent tip can be a valid BTCR DID. No OP_RETURN or other information in the transaction is required. This means that even old dust (small change from other payments) can be used.

Right now we don't support newer segwit P2WPKH transaction, but should be possible in 1.0. However P2SH and P2WSH will have to wait.

This test also tests txref encoders — by default, output 0 is the revocation/rotation "tip", which is correct one in this case.

  TESTNAME: Test #1 — BTCR DID MVP Valid & Unrevoked
  DID TRANSACTION ID: 80871cf043c1d96f3d716f5bc02daa15a5e534b2a00e81a530fb40aa07ceceb6
  DID ADDRESS: mo8pqoxeu4EWSisZ8n94niyvPVJzDL3epg
  DID WIF Private Key: Contact ChristopherA@LifeWithAlacrity.com
  TXREF: did:btcr:x705-jzv2-qqaz-7vuz
  CONFIRMED IN BLOCK: 1353983
  BLOCKINDEX: 83
  OUTPUTINDEX: 0
  TIP ADDRESS: mqkvMtYfTufj3iEXjYHmnopZrsowMFxrKw
  IMPLICIT DID DOCUMENT:
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
  SUPPLEMENTARY DID Document: UNDEFINED
  CONSTRUCTED DID Document:
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

### Test #2 — BTCR DID MVP (Minimum Viable Product) Valid but REVOKED DID Document Example

This test is an example of an MVP that is revoked because the tip address has been spent. This DID, and all claims issued by the key in this DID should be considered revoked. NOTE: the special case that someone funds the TIP address. A unrevoked DID isn't as simple as that there unspent funds on an address, it is that there are also no output transactions associated the tip address.


  TESTNAME: Test #2 — BTCR DID MVP (Minimum Viable Product) Valid but REVOKED
  DID TRANSACTION ID: 2f1838f481be7b4f4d37542a751aa3a27be7114f798feb24ff0fc764730973d0
  DID ADDRESS: n3oaLYUpxwEnQQS8zcX3zGiLUgFi5dH313
  DID WIF Private Key: Contact ChristopherA@LifeWithAlacrity.com
  TXREF: did:btcr:xz35-jzv2-qqs2-9wjt
  CONFIRMED IN BLOCK: 1354001
  BLOCKINDEX: 83
  OUTPUTINDEX: 0
  TIP ADDRESS: mqkvMtYfTufj3iEXjYHmnopZrsowMFxrKw
  REVOCATION TRANSACTION: be5be4b2c4e530b49af139a8448ae2ae8b5882f2e7f5c7908eca0268f72494e9
  IMPLICIT DID DOCUMENT:
```json
{
    "@context": "https://w3id.org/btcr/v1",
    "id": "did:btcr:xz35-jzv2-qqs2-9wjt",
    "publicKey": [
        {
            "id": "did:btcr:xz35-jzv2-qqs2-9wjt#keys-1",
            "owner": "did:btcr:xz35-jzv2-qqs2-9wjt",
            "type": "EdDsaSAPublicKeySecp256k1",
            "publicKeyHex": "020a5a5c8c3575489cd2c17d43f642fc2b34792d47c9b026fafe33b3469e31b841"
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
            "blockhash": "000000000000005561a0b82b1dd8eefd1c3ba0cf674a67cf6699a3f66410df39",
            "blockindex": 83,
            "outputindex": 1,
            "blocktime": "2018-07-16T21:51:32.319Z",
            "time": 1499501000,
            "timereceived": "2018-07-16T21:51:32.319Z",
            "burn-fee": -0.05
        }
    ]
}
```
  SUPPLEMENTARY DID Document: UNDEFINED
  CONSTRUCTED DID Document:
```json
{
    "@context": "https://w3id.org/btcr/v1",
    "id": "did:btcr:xz35-jzv2-qqs2-9wjt",
    "publicKey": [
        {
            "id": "did:btcr:xz35-jzv2-qqs2-9wjt#keys-1",
            "owner": "did:btcr:xz35-jzv2-qqs2-9wjt",
            "type": "EdDsaSAPublicKeySecp256k1",
            "publicKeyHex": "020a5a5c8c3575489cd2c17d43f642fc2b34792d47c9b026fafe33b3469e31b841"
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
            "blockhash": "000000000000005561a0b82b1dd8eefd1c3ba0cf674a67cf6699a3f66410df39",
            "blockindex": 83,
            "outputindex": 1,
            "blocktime": "2018-07-16T21:51:32.319Z",
            "time": 1499501000,
            "timereceived": "2018-07-16T21:51:32.319Z",
            "burn-fee": -0.05
        }
    ]
}
```


#### Test #2 — BTCR DID MVP (Minimum Viable Product) Valid but REVOKED DID Document Example Verifiable Credential

The signature on this claim should be valid, but the the key used in the DID is revoked because under the DID BTCR Method if the tip is spent (technically if there are any output transactions associated with the tip address) without a rotation op_return, all keys are revoked associated that DID. All claims issued thus should be considered revoked.

```json
{
  "@context": [
    "https://w3c.github.io/vc-data-model/vocab/context.jsonld",
    "http://schema.org/",
    "https://w3id.org/security/v1"
  ],
  "id": "did:btcr:xz35-jzv2-qqs2-9wjt",
  "type": [
    "VerifiableCredential"
  ],
  "claim": {
    "id": "did:btcr:xz35-jzv2-qqs2-9wjt/credential/0",
    "alternatename": "Test #2 - BTCR DID MVP Valid but REVOKED",
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
