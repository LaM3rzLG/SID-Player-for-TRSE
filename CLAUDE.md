# SID Player for TRSE — projekt-memória (indulás: 2026-11-04)

**NYILVÁNOS repó: https://github.com/LaM3rzLG/SID-Player-for-TRSE** (MIT). A SIDSoftEMU lejátszója TRSE-unitként
(`SID.tru`, `Unit SID`) játékok háttérzenéjéhez + minta (`SIDPelda.ras`) + demózene + `tools/stc2bin.py`.
Commit a felhasználó nevében: `LaM3rzLG <lorinczg77@gmail.com>`; a felhasználó nem gitel. Magyarul, tömören.
**.sid fájl NEM kerülhet ide** (jogdíj; a felhasználó döntése 2026-11-04) - csak az átalakított demó (1 perc).

- API: `SID::Init(Dal, Paletta, Lap)`, `Start`, `Sync` (képkocka-szinkron, a GE::WaitForSync helyett), `Play`
  (léptetés, a lemaradást behozza), `Stop`. A `Step`/`Wait` foglalt szó a TRSE-ben. Asm: SdStartK/SdWaitK/SdStepK/SdStopK.
- Hang-IT: 391 T / 624 (63% CPU); BC'DE'HL'AF' az övé, IX/IY szabad. Dal bárhol (`stc2bin.py -c CÍM` áthelyezi).
- Mac fordítás (a mappában): `/Applications/trse.app/Contents/MacOS/trse -cli op=project
  settings=../TVC_Kozos/mac/trse_mac.ini project=$PWD/SIDPelda.trse input_file=$PWD/SIDPelda.ras assemble=yes`;
  lemezkép: `pwsh ../SIDSoftEMU/resources/make_dsk.ps1 -Out SIDPelda.dsk -Template ../TVC_Kozos/mac/dsk_sablon.dsk
  -Files @('SIDPelda.cas=SIDPELDA.CAS')`. A kód vége (EndBlock19ef a .sym-ben) < $5000 (a minta palettája).
- Kipróbálva freeTVC-ben (2026-11-04): a négyzet 50 Hz-en mozog, a hang egyezik a sid2tvc WAV-jával.
- Előzmény: SIDSoftEMU repó `SIDLEJATSZO/` (2026-11-04), onnan költözött ide.
