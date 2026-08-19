# Nekara Resourcepack

Oficiální serverový resource pack pro **Minecraft 26.1.2** a ekosystém Nekara.
Distribuovaný soubor je [Nekara-ResourcePack-26.1.2.zip](Nekara-ResourcePack-26.1.2.zip).
Každý GitHub Release obsahuje tentýž ověřený ZIP jako asset, aby šel bezpečně použít
v `server.properties` nebo distribuovat launcherem.

## Release 0.8

Release 0.8 obsahuje znovu sestavený pack se 14 753 položkami pro Minecraft 26.1.2.
Jádrem je Dokucraft, nad ním jsou animace FA+Player a nejvyšší prioritu mají vlastní
asset-y Nekary. Přidává namespace `nekarammo` pro dýky, rapíry, kladiva a Hůl mystika;
hůl má samostatný model v ruce a používá délku i držení kopí. Opravené cesty
`textures/entity/equipment/humanoid_leggings` zajišťují správné vykreslení kalhot.
Dračí mount je
serverový vanilla Ender Dragon, proto pro něj pack nepřidává klientský mod ani vlastní
model entity.

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

## Integrace pluginů

Resource pack poskytuje pluginové GUI a modely v namespace `nekararpg`. Kontrakt pro budoucí
vlastní itemy, zvuky a stabilní ID je v [docs/NEKARARPG_INTEGRATION.md](docs/NEKARARPG_INTEGRATION.md).
Zatím neexistuje obecný registr custom itemů; dokument definuje bezpečný postup,
aby se ID ani model-data nekřížily ve chvíli, kdy budou itemy do NekaraRPG přidány.

Aktuální zbraně NekaraMMO používají přímé item-model klíče v namespace `nekarammo`.
Měděné custom zbraně nejsou součástí vydání; podporované modelové tiery začínají Ironem
a pokračují přes Golden, Diamond a Netherite podle konkrétní rodiny.

## Ověření před nasazením

- Použij pouze ZIP z tohoto repozitáře nebo odpovídající release asset.
- Ověř SHA-256 zveřejněný v poznámkách releasu.
- Po výměně packu úplně restartuj klienta nebo proveď resource reload.
- Pro serverový pack aktualizuj URL, SHA-1 a UUID v `server.properties`.

Lokální zdrojové archivy zůstávají mimo tento repozitář; do GitHubu je publikován
výsledný ověřený serverový pack a dokumentace.
