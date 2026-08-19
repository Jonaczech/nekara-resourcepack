# Nekara resource pack handoff

## Current release

- Version: `0.8`
- Minecraft: `26.1.2`
- Pack format: `84` (`min_format` 68, `max_format` 84)
- Artifact: `Nekara-ResourcePack-26.1.2.zip`
- Entries: 14,753
- SHA-256: `694ed0c7c2b0a410f2406c9413edf3409f07e734a419d91b0133ec6934f47ab3`
- Server SHA-1: `7a29a945eee118c009088d1741052e34fb3af222`

The pack is layered in this order: Dokucraft base, FA+Player animation assets, then
Nekara custom weapons. It contains no legacy `bed.jem`. NekaraMMO assets live in the
`nekarammo` namespace and NekaraRPG assets remain in `nekararpg`.

## Runtime acceptance

Verify leggings on a player and armor stand, the Mystic staff in inventory and both
hands, spear-like third-person placement, every signed weapon tier, player animations,
placed beds and a full client resource reload. GitHub publication does not update
`server.properties`; deploy the release URL and SHA-1 separately.
