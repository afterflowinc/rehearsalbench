# Pre-registration hashes

Every stage of RehearsalBench was frozen before its results existed: the rules, the organisation specifications, the
harness, and the scoring code were written down, hashed with SHA-256, and committed before any model ran or any score
was computed. This page lists the hash of each freeze manifest. Each manifest in turn lists the hash of every file it
covers.

The frozen code is private. A reviewer who is given access can check any file against these hashes with
`shasum -a 256 <file>`.

| Freeze | Manifest last committed (AEDT) | SHA-256 of the manifest |
|---|---|---|
| Organisation set 2 (specifications) | 25 Oct 2026 | `5a87b8d9a86071098ecaefedf492d23ad3ca86eb2055acf9f71997bbb30a4b54` |
| Organisation set 2 (rules) | 26 Oct 2026, 15:46 | `bb0541aacbe24f0d3e2c6e837dd05f44881e4b7079947687e617bf1b4fd036b6` |
| Real-outcome backtest | 28 Oct 2026, 00:00 | `0003f872a67578b70b3a510916d94d76c6d4c0727b8be7a55beb772ae7809201` |
| Real-world test plan (stage A) | 29 Oct 2026, 11:30 | `0b0bf6d3493d5b19741f5ba947bcbdb3beba439cf5be0b031f815dd2bbbc7aa5` |
| Organisation set 3 (specifications) | 29 Oct 2026, 13:10 | `99219ea525f40fbc37afca9aecb989f3d6ba156508ae32f6fa8a9edb85e02c2d` |
| Re-disguise round (33-event set) | 29 Oct 2026, 16:38 | `977f8ea77f35f1830846ae21883901d64441f432656945ed1230bae390bbbcfd` |
| Organisation set 3 (rules) | 29 Oct 2026, 19:59 | `b9f02f6632d34ff2358fd3aab723ddbf0fb901fa789159a59554cd516ab8433f` |
| Round 3: models, routes, harness, and scoring | 30 Oct 2026, 14:31 | `cfdc390b166e709786df2a5d4e2768bca6269277b73833b6a4832e29b37954b5` |
| Final real-world test (stage C) | 2 Nov 2026, 10:34 | `3c6cb050f8ae70e6db029f398b91ff2e2071e17b81a3a23df5cfcc3ee5de5203` |

The scoring was later reproduced from the frozen code: one randomly drawn round 3 run per organisation (14 runs)
re-scored to identical results, and the stage C score files were byte-identical.
