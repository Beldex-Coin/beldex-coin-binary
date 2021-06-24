# Beldex

Copyright (c) 2018 The Beldex Project.   
Copyright (c) 2014-2018 The Monero Project.   
Portions Copyright (c) 2012-2013 The Cryptonote developers.

## Introduction

Beldex is a private, secure, untraceable, decentralised digital currency. You are your bank, you control your funds, and nobody can trace your transfers unless you allow them to do so.

**Privacy:** Beldex uses a cryptographically sound system to allow you to send and receive funds without your transactions being easily revealed on the blockchain (the ledger of transactions that everyone has). This ensures that your purchases, receipts, and all transfers remain absolutely private by default.

**Security:** Using the power of a distributed peer-to-peer consensus network, every transaction on the network is cryptographically secured. Individual wallets have a 25 word mnemonic seed that is only displayed once, and can be written down to backup the wallet. Wallet files are encrypted with a passphrase to ensure they are useless if stolen.

**Untraceability:** By taking advantage of ring signatures, a special property of a certain type of cryptography, Beldex is able to ensure that transactions are not only untraceable, but have an optional measure of ambiguity that ensures that transactions cannot easily be tied back to an individual user or computer.

## About this project

This is the core implementation of Beldex. It is open source and completely free to use without restrictions, except for those specified in the license agreement below. There are no restrictions on anyone creating an alternative implementation of Beldex that uses the protocol and network in a compatible manner.

As with many development projects, the repository on Github is considered to be the "staging" area for the latest changes. Before changes are merged into that branch on the main repository, they are tested by individual developers in their own branches, submitted as a pull request, and then subsequently tested by contributors who focus on testing and code reviews. That having been said, the repository should be carefully considered before using it in a production environment, unless there is a patch in the repository for a particular show-stopping issue you are experiencing. It is generally a better idea to use a tagged release for stability.

## Running beldexd

The build places the binary in `bin/` sub-directory within the `build` directory
from which cmake was invoked (repository root by default). To run in
foreground:

    ./bin/beldexd

To list all available options, run `./bin/beldexd --help`.  Options can be
specified either on the command line or in a configuration file passed by the
`--config-file` argument.  To specify an option in the configuration file, add
a line with the syntax `argumentname=value`, where `argumentname` is the name
of the argument without the leading dashes, for example `log-level=1`.

To run in background:

    ./bin/beldexd --log-file beldexd.log --detach

To run as a systemd service, copy
[beldexd.service](utils/systemd/beldexd.service) to `/etc/systemd/system/` and
[beldexd.conf](utils/conf/beldexd.conf) to `/etc/`. The [example
service](utils/systemd/beldexd.service) assumes that the user `beldex` exists
and its home is the data directory specified in the [example
config](utils/conf/beldexd.conf).

For running the testnet daemon mention `--testnet` while starting the daemon

If you're on Mac, you may need to add the `--max-concurrency 1` option to
beldex-wallet-cli, and possibly beldexd, if you get crashes refreshing.

## Running beldex wallet
You can run the beldex wallet from the `bin/` sub-directory inside `build` directory

        ./bin/beldex-wallet-cli
The above command will ask you for the new wallet file and password, if you wish to create the wallet using your own electrum seed you can do it using the below command

        ./bin/beldex-wallet-cli --generate-new-wallet my_wallet_file  --electrum-seed="my mnemonic seed" --password "my password" --log-file my_wallet_log_file;    

## Running wallet RPC
The wallet rpc can also be run from the `bin/` sub-directory inside `build` directory

        ./bin/beldex-wallet-rpc --wallet-file my-wallet-file --prompt-for-password --rpc-bind-port 16969    



