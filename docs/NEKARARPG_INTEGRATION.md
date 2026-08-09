# NekaraRPG resource-pack contract

Tento dokument je společný kontrakt mezi `NekaraRPG` a `nekara-resourcepack`. Nezavádí
neexistující custom itemy ani nemění serverovou logiku; určuje pravidla, podle kterých
budou budoucí custom itemy přidávány.

## Namespace a názvy

- Pluginové assety patří výhradně do namespace `nekararpg`.
- Stabilní ID používá malé znaky, číslice, lomítka, podtržítka a pomlčky, například
  `nekararpg:mounts/whistle` nebo `nekararpg:fishing/ancient_lure`.
- ID se po vydání nikdy nepřejmenovává. Změna vzhledu znamená změnu textury/modelu,
  nikoli změnu ID.
- Cesta modelu je `assets/nekararpg/models/item/<path>.json` a textura
  `assets/nekararpg/textures/item/<path>.png`.
- Vlastní zvuk má odpovídající namespaced ID, například `nekararpg:fishing.hit`,
  deklarované v `assets/nekararpg/sounds.json`.

## Custom item registry

Před implementací itemu se do tohoto dokumentu přidá řádek do tabulky. Je to jediný
zdroj pravdy pro serverovou konfiguraci, pluginový persistent tag a resource-pack model.

| Stable item ID | Base material | Custom model data | Status | Poznámka |
| --- | --- | ---: | --- | --- |
| `nekararpg:mounts/whistle` | `GOAT_HORN` | `260102` | reserved | Hodnota je aktuálně v `mounts/config.yml`; viz níže. |

Hodnota `custom-model-data` se nesmí znovu použít pro jiný základní materiál bez
výslovného zápisu do registru. Nové hodnoty se přidělují monotónně v rozsahu
`260100–260999`, dokud nebude zaveden jiný verzovaný registr.

## Vlastní zbraně v 0.7

NekaraRPG 2.7.0 používá pro vlastní dýky, obouruční meče a kladiva přímo stabilní
item-model ID v namespace `nekararpg`, například `nekararpg:weapons/greatsword/diamond`.
Nejde o nové `custom-model-data`: plugin nastavuje item model přímo a pack zachovává
vanilla fallback pro všechny běžné předměty. Modely obouručních mečů obsahují
samostatnou variantu pro držení v ruce.

`Dračí pouto` nepřidává vlastní asset entity. Drak je serverem synchronizovaný vanilla
Ender Dragon, takže jej klient vykreslí i bez Fabricu nebo dalšího modelu v packu.

## Současný mount whistle

NekaraRPG již vytváří GOAT_HORN s `custom-model-data: 260102` v konfiguraci
`src/main/resources/mounts/config.yml`. Tento release pouze rezervuje jeho ID;
nevydává náhradní texturu ani model. Až bude schválený vzhled, změna musí obsahovat
v jednom vydání:

1. definici modelu/textury v namespace `nekararpg`;
2. selektor pro `minecraft:custom_model_data` v `assets/minecraft/items/goat_horn.json`;
3. zachovaný vanilla fallback pro nepoužívaný GOAT_HORN a pro stav `minecraft:using_item`;
4. aktualizovaný řádek registru zde a ověřenou konfiguraci NekaraRPG.

Přepsat `goat_horn.json` jednoduchým modelem není bezpečné: vanilla 26.1.2 v něm rozlišuje
stav používání itemu. Selektor proto musí tento fallback zachovat.

## Kontrolní postup při přidání itemu

1. Rezervuj stabilní ID a `custom-model-data` v této tabulce.
2. Přidej assety do `nekararpg` namespace a testuj jejich cesty v samostatném packu.
3. Zachovej vanilla fallback při změně definice základního materiálu.
4. V NekaraRPG nastav stejný materiál, persistent item ID a model-data.
5. Ověř nový item v inventáři, v ruce, při používání a po reconnectu.
6. Vydaný ZIP validuj proti klientskému JARu 26.1.2 a zveřejni jeho SHA-256 i SHA-1.

Server neumí ověřit, zda klient skutečně obsahuje lokální custom texturu nebo zvuk.
Proto musí být pluginová konfigurace a resource-pack release publikovány koordinovaně.
