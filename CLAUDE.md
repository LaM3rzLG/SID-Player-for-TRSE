# SID Player for TRSE — projekt-memória (indulás: 2026-11-04)

**NYILVÁNOS repó: https://github.com/LaM3rzLG/SID-Player-for-TRSE** (MIT). A SIDSoftEMU lejátszója TRSE-unitként
(`SID.tru`, `Unit SID`) játékok háttérzenéjéhez + minta (`SIDPelda.ras`) + demózene (BIN). A kiadás: TVC-Programok/SID2TVC_TRSE_Unit.
Commit a felhasználó nevében: `LaM3rzLG <lorinczg77@gmail.com>`; a felhasználó nem gitel. Magyarul, tömören.
**.sid fájl NEM kerülhet ide** (jogdíj; a felhasználó döntése 2026-11-04) - csak az átalakított demó (1 perc).

- API (2026-11-04, BIN-es változat): `SID::Init(Dal, Lap, KozosLap)` (a kotta címe, a táblák lapja, a közös 512 byte
  lapja; `SID::Hiba` 0/1/2), `Start`, `Sync`, `Play`, `Stop`. A `Step`/`Wait` foglalt szó a TRSE-ben.
  A zene: `sid2tvc -b` (1.4) -> `SONGn_TAB.BIN` (csak a használt táblák, laphatárra) + `SONGn_DAL.BIN` (áthelyezhető kotta:
  9 byte fejléc = 3 hang eltolása, hossz, táblák száma; a REF/ugrás címe a kotta elejéhez képest, a unit adja hozzá a
  betöltési címet). A zaj- és a szintlapot az Init készíti a KozosLap-ra (több dal közösen). A felhasználó elve:
  **a PC dolgozzon, a TVC-n a legkisebb memória** (0 byte többlet, nincs másolás).
- Hang-IT: 391 T / 624 (63% CPU); BC'DE'HL'AF' az övé, IX/IY szabad (az Init sem használja az IX-et).
- Mac fordítás (a mappában): `/Applications/trse.app/Contents/MacOS/trse -cli op=project
  settings=../TVC_Kozos/mac/trse_mac.ini project=$PWD/SIDPelda.trse input_file=$PWD/SIDPelda.ras assemble=yes`;
  lemezkép: `pwsh ../SIDSoftEMU/resources/make_dsk.ps1 -Out SIDPelda.dsk -Template ../TVC_Kozos/mac/dsk_sablon.dsk
  -Files @('SIDPelda.cas=SIDPELDA.CAS')`. A minta: közös $4E00, táblák $5000, kotta $5E00; a kód vége (EndBlock19ef) < $4E00.
- Kipróbálva freeTVC-ben (2026-11-04): a négyzet 50 Hz-en mozog, a hang egyezik a sid2tvc WAV-jával.
- Előzmény: SIDSoftEMU repó `SIDLEJATSZO/` (2026-11-04), onnan költözött ide.
