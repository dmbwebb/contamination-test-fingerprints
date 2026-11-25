# Freeze fingerprints

Timestamped fingerprints for a research project. Each `.txt` file holds hashes only, never code, file names or results:

- `git_commit`: a commit in a private git repository. It fixes that repository's full history up to that moment.
- `manifest_sha256`: the SHA-256 hash of a manifest that lists a hash for every file of one item of work, data included.

Items are identified by number only.

Next to each `.txt` file is a `.tsr` file of the same name. It is an RFC 3161 timestamp from [FreeTSA](https://freetsa.org) for that `.txt` file. It proves the fingerprint existed at the stated time, independently of git commit dates and of GitHub. The underlying files will be released later, and they must match these hashes.

## Checking a timestamp

```
openssl ts -verify -in <file>.tsr -data <file>.txt -CAfile freetsa_cacert.pem -untrusted freetsa_tsa.crt
openssl ts -reply -in <file>.tsr -text      # shows the time
```

`freetsa_cacert.pem` and `freetsa_tsa.crt` are FreeTSA's certificates, downloaded from freetsa.org on 25 November 2026.
