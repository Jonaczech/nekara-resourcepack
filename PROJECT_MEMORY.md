# Nekara resource pack project memory

- This repository publishes only the final verified server ZIP and integration documentation.
- Minecraft target is `26.1.2`; current pack format is 84.
- Dokucraft is the visual base, FA+Player provides player animations and Nekara custom assets have highest priority.
- `nekararpg` and `nekarammo` are separate namespaces and stable item-model keys must not cross between them.
- Mystic staff uses separate inventory and in-hand models and must visually follow spear length and grip.
- Armor leggings use `assets/minecraft/textures/entity/equipment/humanoid_leggings`; legacy layer-only paths are insufficient in 26.1.2.
- Exclude legacy `optifine/cem/bed.jem` from every build.
- Use SHA-1 for `resource-pack-sha1`; use SHA-256 for artifact integrity and release verification.
- Release publication and live-server configuration are separate operations.
