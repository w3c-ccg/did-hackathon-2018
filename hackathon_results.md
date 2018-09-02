Ryan and Dan:

- Dan and Ryan investigated BlockSci and libbitcoin as infrastructure for building a chain-tip-following method resolver in C++.  
- Dan made progress on the resolver code.
- Ryan spent some time investigating client-side diddoc patches, but security assumptions currently allow the resolver library to own this problem.  
- The group discussed the algorithm for following the tip and how the algorithm must evolve when p2sh is supported. Ryan is writing up this algorithm with examples.
- Digital Contract Design plans to put a BTCR resolver online for public use in the near future.

Yancy:

- Worked with bitcoind and libbitcoin to find the last transaction not containing an OP_RETURN which indicates a revoke.  This proved difficult due to the randomized nature of outputs and other edge cases.
- Submitted PR to parse VC from btcr service endpoint in btcr-did-tools-js and display as output in the playground. 
  
  
Anthony:


Kim:


Christopher:

Joe:
