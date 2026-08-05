# Nekara Resourcepack

Oficiální serverový resource pack pro **Minecraft 26.1.2** a ekosystém Nekara.
Distribuovaný soubor je [Nekara-ResourcePack-26.1.2.zip](Nekara-ResourcePack-26.1.2.zip).
Každý GitHub Release obsahuje tentýž ověřený ZIP jako asset, aby šel bezpečně použít
v `server.properties` nebo distribuovat launcherem.

## Obsah a priority

Pack je sestaven pouze z lokálně dodaných zdrojů. Priority jsou pevné:

1. Basic resourcepack – bloky a efekty, nejnižší priorita.
2. Beds, Enchanted books a GUI.
3. Player animations.
4. Armor, weapons and tools.
5. Font.
6. NekaraRPG GUI – nejvyšší priorita pro pluginové rozhraní.

Kompatibilita postelí je záměrně konzervativní: legacy modely, blockstates, entity
textury a `optifine/cem/bed.jem` se do finálního ZIPu nevkládají. Minecraft 26.1.2
proto používá vlastní renderer umístěné postele a nemůže dojít ke svisle mapované
textuře ani k dvojité geometrii. Lokální ikony postelí zůstávají zachované.

## NekaraRPG

Resource pack poskytuje pluginové GUI v namespace `nekararpg`. Kontrakt pro budoucí
vlastní itemy, zvuky a stabilní ID je v [docs/NEKARARPG_INTEGRATION.md](docs/NEKARARPG_INTEGRATION.md).
Zatím neexistuje obecný registr custom itemů; dokument definuje bezpečný postup,
aby se ID ani model-data nekřížily ve chvíli, kdy budou itemy do NekaraRPG přidány.

## Ověření před nasazením

- Použij pouze ZIP z tohoto repozitáře nebo odpovídající release asset.
- Ověř SHA-256 zveřejněný v poznámkách releasu.
- Po výměně packu úplně restartuj klienta nebo proveď resource reload.
- Pro serverový pack aktualizuj URL, SHA-1 a UUID v `server.properties`.

Lokální zdrojové archivy zůstávají mimo tento repozitář; do GitHubu je publikován
výsledný ověřený serverový pack a dokumentace.
