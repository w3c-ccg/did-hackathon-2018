
## Christopher Allen

[BTCR DID Resolver Test Cases](BTCR-DID-Tests.md)

## Joe Andrieu

[BTCR Playground Goals](playground-goals.md)

## Ryan Grant and Dan Pape

- Dan and Ryan investigated BlockSci and libbitcoin as infrastructure for building a chain-tip-following method resolver in C++.  
- Dan made progress on the resolver code.
- Ryan spent some time investigating client-side diddoc patches, but security assumptions currently allow the resolver library to own this problem.  
- The group discussed the algorithm for following the tip and how the algorithm must evolve when p2sh is supported. Ryan is writing up this algorithm with examples.
- Digital Contract Design plans to put a BTCR resolver online for public use in the near future.

## Kim Hamilton Duffy

Updates to BTCR playground and library dependencies

## Yancy Ribbens

- Worked with bitcoind and libbitcoin to find the last transaction not containing an OP_RETURN which indicates a revoke.  This proved difficult due to the randomized nature of outputs and other edge cases.
- Submitted PR to parse VC from btcr service endpoint in btcr-did-tools-js and display as output in the playground. 
  
## Anthony Ronning
 
- Created Electron BCTR implementation: https://github.com/AnthonyRonning/btcr-electron

## Kulpreet Singh

Created service that talks to btcd and provides some endpoints to help experiment with DID creation and resolution.

The service is at https://btcr-service.opdup.com (/ is a 404) and the repo is at https://github.com/kulpreet/btcr-service

### Current endpoints

All endpoints return JSON objects, content-type as application/json

1. `/txref/:query/decode`
Returns a decoded txref passed as query, e.g. https://btcr-service.opdup.com/txref/txtest1:x705-jzv2-qqaz-7vuz/decode

2. `/txref/:query/txid`
Returns a txid and the utxo index for txref passed as query, e.g. https://btcr-service.opdup.com/txref/txtest1:x705-jzv2-qqaz-7vuz/txid

3. `/tx/:query`
Returns the decoded transaction for the transaction hash passed as query, e.g. https://btcr-service.opdup.com/tx/80871cf043c1d96f3d716f5bc02daa15a5e534b2a00e81a530fb40aa07ceceb6

4. `/addr/:query/spends`
Returns all the transactions associated with the address (limited to 100 for now), in reverse chronological order, for example, https://btcr-service.opdup.com/addr/mqkvMtYfTufj3iEXjYHmnopZrsowMFxrKw/spends

The examples above use the Test #1 transaction/DID posted by Christopher here https://github.com/w3c-ccg/did-hackathon-2018/blob/master/BTCR-DID-Tests.md

I am debating build an endpoint to generate a DID based off a txref, and/or a resolver as next steps to see if we can actually follow the tip with the /addr/.*/spends endpoint.





