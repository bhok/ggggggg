BitcoinCore-multichain
======================

This is a patched version of BitcoinCore which supports private blockchains created by MultiChain, where the blockchain is configured to behave like Bitcoin's.

Changes are:
- Disable block target verification
- Remove some hard-coded genesis block values related to Bitcoin and instead get from JVM system properties, so that a client such as BitcoinWallet can set them.

To use this version, a client should set the JVM properties:
multichain.genesis.blockhash
multichain.genesis.blocktime

For more information on these values, see a patched version of Scripter Ron's BitcoinWallet:
https://github.com/bitcartel/BitcoinWallet-multichain/tree/multichain


BitcoinCore
===========

BitcoinCore is a library of support routines for the Bitcoin protocol.  It handles elliptic curve signature operations and protocol message encoding/decoding.


Build
=====

I use the Netbeans IDE but any build environment with Maven and the Java compiler available should work.  The documentation is generated from the source code using javadoc.

Here are the steps for a manual build.  You will need to install Maven 3 and Java SE Development Kit 8 if you don't already have them.

  - Create the executable: mvn clean install
  - [Optional] Create the documentation: mvn javadoc:javadoc
  - [Optional] Copy target/BitcoinCore-v.r.jar and target/bcprov-jdk15on-v.r.jar to wherever you want to store the libraries for use with your Bitcoin applications.

  
Usage Notes
===========

You must call NetParams.configure() before you call any other BitcoinCore routine.  This initializes the library data areas for the specified network (production or test).

