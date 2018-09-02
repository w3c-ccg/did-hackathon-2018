# did-hackathon-2018


* [BTCR-DID-Tests](./BTCR-DID-Tests.md) — A number of testnet registered DIDs, along with sample valid DID Documents, some unrevoked, others rotated, others revoked, along with signed verifiable claims using those DIDs.
* Playgrounds
    * [btcr-tx-playground](https://weboftrustinfo.github.io/btcr-tx-playground.github.io/) - HTML/JS playground using the [btcr-did-tools-js](https://github.com/WebOfTrustInfo/btcr-did-tools-js) library
        * [Source](https://github.com/WebOfTrustInfo/btcr-tx-playground.github.io)
    * [BTCR-Electron](https://github.com/AnthonyRonning/btcr-electron) - Electron playground for the btcr-did-js library.
* Libraries
    * TXREF Conversion Libraries
        * [txref-conversion-js](https://github.com/WebOfTrustInfo/txref-conversion-js) - Node.js txref conversion library; supports txref-ext
        * [txref-conversion-java](https://github.com/WebOfTrustInfo/txref-conversion-java) - Java txref conversion library; supports txref-ext
        * [txref-conversion-golang](https://github.com/kulpreet/txref) - Golang txref conversion library
        * [txref-conversion-python](https://github.com/WebOfTrustInfo/txref-conversion-python) - Golang txref conversion library
    * BTCR Creation/Resolution Libraries
        * [btcr-did-tools-js](https://github.com/WebOfTrustInfo/btcr-did-tools-js) - Node.js library for creating/resolving BTCR DIDs. Has browserify scripts for running in browser
        * [btcr-service](https://github.com/kulpreet/btcr-service) - A service in Go for encoding/decoding TxRefs and searching all transactions related to an address (/addr/<addr>/spends endpoint). Also, DID resolution for the simplest case of unrevoked, unrotated keys is currently in progress (/txref/<txref>/resolve). The service is live at [https://btcr-service.opdup.com/txref/txtest1:x705-jzv2-qqaz-7vuz/txid](https://btcr-service.opdup.com/txref/txtest1:x705-jzv2-qqaz-7vuz/txid). Repo [README](https://github.com/kulpreet/btcr-service/blob/master/README.md) describes the service endpoints.
        * [universal-resolver](https://github.com/decentralized-identity/universal-resolver/tree/master/implementations/java) includes [driver-did-btcr](https://github.com/decentralized-identity/universal-resolver/tree/master/implementations/java/driver-did-btcr), sample deployment is [here](https://uniresolver.io/).
* About BTCR DIDs (previous writings and presentations; sorted by most recent to least)
    * [BTCR Resolver](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust-spring2018/blob/master/final-documents/btcr-resolver.md)
    * [Visualization of how BTCR works](https://www.icloud.com/keynote/0Bcwqiyw6RGvMZgDyFt-prI_g#BTCR)
    * [BTCR DIDs and DDOs - may be out of date](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust-fall2017/blob/master/topics-and-advance-readings/btcr-dids-ddos.md)
* [Hackathon results](results.md)