# fbip-ledger-anchors

Public anchors for the tamper-evident prediction ledger of Afisa Ubashiri (afisa.pamuiafrika.com).

Every prediction, result, settlement and void is an entry in a hash chain: each entry's SHA-256 covers its own canonical content and the previous entry's hash. After each daily run the platform commits the hashes added since the last anchor here, under `anchors/YYYY/MM/DD/<last seq>.json`, and `latest.json` points to the newest one. Because each hash covers all earlier ones, an anchored hash fixes everything before it: a prediction cannot be changed or backdated afterwards without breaking the chain against this repository.

To check a prediction, read its canonical form and hash from `GET https://afisa.pamuiafrika.com/v1/predictions/{id}/verify`, recompute the SHA-256, and find the hash in the anchor that covers its sequence number.

Anchors up to sequence 330 (10 to 12 October 2026) were first written to a staging repository before launch; they are included here with their original commits, which the platform's records name.
