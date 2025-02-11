# [Version 2.1.0 to 2.2.0](./docs/changes/2.2.0.md)

# [Version 2.2.0 to 2.3.0](./docs/changes/2.3.0.md)

# [Version 2.3.0 to 2.4.0](./docs/changes/2.4.0.md)

# [Version 2.4.0 to 2.5.0](./docs/changes/2.5.0.md)

# [Version 2.5.0 to 2.5.1](./docs/changes/2.5.1.md)

# [Version 2.5.1 to 2.6.0](./docs/changes/2.6.0.md)

# [Version 2.6.0 to 2.7.0](./docs/changes/2.7.0.md)

# [Version 2.7.0 to 2.8.0](./docs/changes/2.8.0.md)

# [Version 2.8.0 to 2.9.0](./docs/changes/2.9.0.md)

# [Version 2.9.0 to 2.9.1](./docs/changes/2.9.1.md)

# [Version 2.9.1 to 2.9.2](./docs/changes/2.9.2.md)

# [Version 2.9.2 to 2.10.0](./docs/changes/2.10.0.md)

# [Version 2.10.0 to 2.11.0](./docs/changes/2.11.0.md)

# [Version 2.11.0 to 2.12.0](./docs/changes/2.12.0.md)

# [Version 2.12.0 to 2.12.1](./docs/changes/2.12.1.md)

# Planned for next version

## Bug Fixes

* [GH-427](https://github.com/apache/mina-sshd/issues/427) SCP client: fix `DefaultScpClient.upload(InputStream, ...)`
* [GH-455](https://github.com/apache/mina-sshd/issues/455) Fix `BaseCipher`: make sure all bytes are processed
* [GH-470](https://github.com/apache/mina-sshd/issues/470) MontgomeryCurve: synchronize access to KeyPairGenerator
* [GH-489](https://github.com/apache/mina-sshd/issues/489) SFTP v3 client: better file type determination
* [GH-500](https://github.com/apache/mina-sshd/issues/500) SFTP file system: fix memory leak on exceptions

* [PR-472](https://github.com/apache/mina-sshd/pull/472) sshd-spring-sftp: fix client start
* [PR-476](https://github.com/apache/mina-sshd/pull/476) Fix Android detection
* [PR-486](https://github.com/apache/mina-sshd/pull/486) Add missing `equals` and `hashCode` to U2F key classes


* [SSHD-1237](https://issues.apache.org/jira/browse/SSHD-1237) Handle keep-alive _channel_ requests

## New Features

* The key exchange method sntrup761x25519-sha512@openssh.com is now available if the Bouncy Castle library is available.

This uses a post-quantum key encapsulation method (KEM) to make key exchange future-proof against quantum attacks.
More information can be found in IETF Memo [Secure Shell (SSH) Key Exchange Method Using Hybrid Streamlined
NTRU Prime sntrup761 and X25519 with SHA-512: sntrup761x25519-sha512](https://www.ietf.org/archive/id/draft-josefsson-ntruprime-ssh-02.html).


## Behavioral changes and enhancements

* [GH-468](https://github.com/apache/mina-sshd/issues/468) SFTP: validate length of data received: must not be more than requested

SFTP read operations now check the amount of data they get back. If it's more than
requested an exception is thrown. SFTP servers must never return more data than the
client requested, but it appears that there are some that do so. If property
`SftpModuleProperties.TOLERATE_EXCESS_DATA` is set to `true`, a warning is logged and
such excess data is silently discarded.

## Potential compatibility issues

## Major Code Re-factoring

