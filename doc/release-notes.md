0.19.1 Release Notes
===============================

Bitcoin Core version 0.19.1 is now available from:

  <https://bitcoincore.org/bin/bitcoin-core-0.19.1/>

This minor release includes various bug fixes and performance
improvements, as well as updated translations.

Please report bugs using the issue tracker at GitHub:

  <https://github.com/bitcoin/bitcoin/issues>

To receive security and update notifications, please subscribe to:

  <https://bitcoincore.org/en/list/announcements/join/>

How to Upgrade
==============

If you are running an older version, shut it down. Wait until it has completely
shut down (which might take a few minutes for older versions), then run the
installer (on Windows) or just copy over `/Applications/Bitcoin-Qt` (on Mac)
or `bitcoind`/`bitcoin-qt` (on Linux).

Upgrading directly from a version of Bitcoin Core that has reached its EOL is
possible, but it might take some time if the datadir needs to be migrated. Old
wallet versions of Bitcoin Core are generally supported.

Compatibility
==============

Bitcoin Core is supported and extensively tested on operating systems using
the Linux kernel, macOS 10.10+, and Windows 7 and newer. It is not recommended
to use Bitcoin Core on unsupported systems.

Bitcoin Core should also work on most other Unix-like systems but is not
as frequently tested on them.

From Bitcoin Core 0.17.0 onwards, macOS versions earlier than 10.10 are no
longer supported, as Bitcoin Core is now built using Qt 5.9.x which requires
macOS 10.10+. Additionally, Bitcoin Core does not yet change appearance when
macOS "dark mode" is activated.

In addition to previously supported CPU platforms, this release's pre-compiled
distribution provides binaries for the RISC-V platform.

0.19.1 change log
=================


### Consensus
- #16128 Delete error-prone CScript constructor only used with FindAndDelete (instagibbs)
- #16060 Bury bip9 deployments (jnewbery)

### Policy
- #15557 Enhance `bumpfee` to include inputs when targeting a feerate (instagibbs)
- #15846 Make sending to future native witness outputs standard (sipa)

### Block and transaction handling
- #15632 Remove ResendWalletTransactions from the Validation Interface (jnewbery)
- #14121 Index for BIP 157 block filters (jimpo)
- #15141 Rewrite DoS interface between validation and net_processing (sdaftuar)
- #15880 utils and libraries: Replace deprecated Boost Filesystem functions (hebasto)
- #15971 validation: Add compile-time checking for negative locking requirement in LimitValidationInterfaceQueue (practicalswift)
- #15999 init: Remove dead code in LoadChainTip (MarcoFalke)
- #16015 validation: Hold cs_main when reading chainActive in RewindBlockIndex (practicalswift)
- #16056 remove unused magic number from consistency check (instagibbs)
- #16171 Remove -mempoolreplacement to prevent needless block prop slowness (TheBlueMatt)
- #15894 Remove duplicated "Error: " prefix in logs (hebasto)
- #14193 validation: Add missing mempool locks (MarcoFalke)
- #15681 Allow one extra single-ancestor transaction per package (TheBlueMatt)
- #15305 [validation] Crash if disconnecting a block fails (sdaftuar)
- #16471 log correct messages when CPFP fails (jnewbery)
- #16433 txmempool: Remove unused default value MemPoolRemovalReason::UNKNOWN (MarcoFalke)
- #13868 Remove unused fScriptChecks parameter from CheckInputs (Empact)
- #16421 Conservatively accept RBF bumps bumping one tx at the package limits (TheBlueMatt)
- #16854 Prevent UpdateTip log message from being broken up (stevenroose)
- #16956 validation: Make GetWitnessCommitmentIndex public (MarcoFalke)
- #16713 Ignore old versionbit activations to avoid 'unknown softforks' warning (jnewbery)
- #17002 chainparams: Bump assumed chain params (MarcoFalke)
- #16849 Fix block index inconsistency in InvalidateBlock() (sdaftuar)

### P2P protocol and network code
- #15597 Generate log entry when blocks messages are received unexpectedly (pstratem)
- #15654 Remove unused unsanitized user agent string CNode::strSubVer (MarcoFalke)
- #15689 netaddress: Update CNetAddr for ORCHIDv2 (dongcarl)
- #15834 Fix transaction relay bugs introduced in #14897 and expire transactions from peer in-flight map (sdaftuar)
- #15651 torcontrol: Use the default/standard network port for Tor hidden services, even if the internal port is set differently (luke-jr)
- #16188 Document what happens to getdata of unknown type (MarcoFalke)
- #15649 Add ChaCha20Poly1305@Bitcoin AEAD (jonasschnelli)
- #16152 Disable bloom filtering by default (TheBlueMatt)
- #15993 Drop support of the insecure miniUPnPc versions (hebasto)
- #16197 Use mockable time for tx download (MarcoFalke)
- #16248 Make whitebind/whitelist permissions more flexible (NicolasDorier)
- #16618 [Fix] Allow connection of a noban banned peer (NicolasDorier)
- #16631 Restore default whitelistrelay to true (NicolasDorier)
- #15759 Add 2 outbound block-relay-only connections (sdaftuar)
- #15558 Don't query all DNS seeds at once (sipa)
- #16999 0.19 seeds update (laanwj)

=======
### Wallet
- #17643 Fix origfee return for bumpfee with feerate arg (instagibbs)
- #16963 Fix `unique_ptr` usage in boost::signals2 (promag)
- #17258 Fix issue with conflicted mempool tx in listsinceblock (adamjonas, mchrostowski)
- #17924 Bug: IsUsedDestination shouldn't use key id as script id for ScriptHash (instagibbs)
- #17621 IsUsedDestination should count any known single-key address (instagibbs)
- #17843 Reset reused transactions cache (fjahr)

### RPC and other APIs
- #17687 cli: Fix fatal leveldb error when specifying -blockfilterindex=basic twice (brakmic)
- #17728 require second argument only for scantxoutset start action (achow101)
- #17445 zmq: Fix due to invalid argument and multiple notifiers (promag)
- #17524 psbt: handle unspendable psbts (achow101)
- #17156 psbt: check that various indexes and amounts are within bounds (achow101)

### GUI
- #17427 Fix missing qRegisterMetaType for `size_t` (hebasto)
- #17695 disable File-\>CreateWallet during startup (fanquake)
- #17634 Fix comparison function signature (hebasto)
- #18062 Fix unintialized WalletView::progressDialog (promag)

### Tests and QA
- #17416 Appveyor improvement - text file for vcpkg package list (sipsorcery)
- #17488 fix "bitcoind already running" warnings on macOS (fanquake)
- #17980 add missing #include to fix compiler errors (kallewoof)

### Platform support
- #17736 Update msvc build for Visual Studio 2019 v16.4 (sipsorcery)
- #17364 Updates to appveyor config for VS2019 and Qt5.9.8 + msvc project fixes (sipsorcery)
- #17887 bug-fix macos: give free bytes to `F_PREALLOCATE` (kallewoof)

### Miscellaneous
- #17897 init: Stop indexes on shutdown after ChainStateFlushed callback (jimpo)
- #17450 util: Add missing headers to util/fees.cpp (hebasto)
- #17654 Unbreak build with Boost 1.72.0 (jbeich)
- #17857 scripts: Fix symbol-check & security-check argument passing (fanquake)
- #17762 Log to net category for exceptions in ProcessMessages (laanwj)
- #18100 Update univalue subtree (MarcoFalke)

Credits
=======

Thanks to everyone who directly contributed to this release:

- Aaron Clauson
- Adam Jonas
- Andrew Chow
- Fabian Jahr
- fanquake
- Gregory Sanders
- Harris
- Hennadii Stepanov
- Jan Beich
- Jim Posen
- João Barbosa
- Karl-Johan Alm
- Luke Dashjr
- MarcoFalke
- Michael Chrostowski
- Russell Yanofsky
- Wladimir J. van der Laan

As well as to everyone that helped with translations on
[Transifex](https://www.transifex.com/bitcoin/bitcoin/).
