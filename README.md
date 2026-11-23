# v23 – planlösning

Interaktiv planritning över lägenheten (undervåning och ovanvåning) med lager för ombyggnadsidéer.

Öppna `index.html` i en webbläsare. Allt ligger i den filen: planens text finns i blocket
`<script type="text/plain" id="plandata">`, och resten är ritmotorn.

- **Lager**: Undervåning och Ovanvåning är våningar. Ändringar (WC2, Sovrum3_Stor, Sovrum3_90, Sovrum3_WC1, Sovrum3_Ruff, WC1, Kök, FastGarderobNere, TaBortGU) slås på och av var för sig; Sovrum3_Stor, Sovrum3_90, Sovrum3_WC1 och Sovrum3_Ruff är alternativ, bara en av dem kan vara på.
- **Visa**: dörrar/fönster/öppningar, inredning, rumsnamn, mått och rutnät. Möbler ritas bara i Möblering.
- **Att göra** (kräver inloggning): tavla med kolumnerna Att göra, Pågår, Väntar och Klart. Lappar har rubrik (krav) och frivilligt emoji, vikt, brådska, deadline, ägare, rum, etiketter och beskrivning i Markdown. Dra lappar mellan kolumner; filtrera på rum, ägare och etikett. Ligger i Firestore-samlingen `lappar`; ägare väljs bland dem som får skriva.
- **Kalkyl**: poster, tillval och texter ligger i Firestore-dokumentet `kalkyl/data` och hämtas efter inloggning; sidan innehåller inga siffror. Valda tillval, buffert och ROT sparas i webbläsaren.
- **Behörighet**: Planlösning, Bilder och Dokument är öppna för alla. Övriga flikar (Möblering, Kalkyl och nya flikar) kräver inloggning med behörighet.
- **Länkar**: varje vy har en egen adress, t.ex. https://vasav23.web.app/todo. Vyerna heter `plan`, `furniture` (Möblering), `todo`, `budget` (Kalkyl), `images` och `documents`. Utan sökväg visas den vy som var vald senast. Adresserna fungerar bara på Firebase Hosting, inte när `index.html` öppnas lokalt.
- **Möblering** (väljs i rubriken, kräver inloggning): namngivna möbleringar per rum som kryssas i, gärna flera i samma rum. En möblering kan kräva att lager är på eller av. Redigera: lägg till möbler, dra dem, vrid 90°, Spara eller Spara som. Möbleringarna ligger i Firestore-samlingen `moblering` och delas; vilka som är ikryssade sparas i webbläsaren. Möbler i plantexten (`möbel …`) ritas inte. Krockar mellan möbler visas bara här.
- **Redigera plan**: ändra texten direkt i sidan. Ändringar sparas lokalt i webbläsaren.
- **Skriv ut**: skriver ut allt som är valt under Lager och Visa på A4, i största skalan av 1:50, 1:100 och 1:200 som får plats, med skalstock.
- **Kopiera bild**: lägger planen som PNG på urklipp.
- **Bilder** (väljs i rubriken): originalplanen per våning; klicka på ett rum för att bläddra bland bilderna i `bilder/` (annonsens i `bilder/notar/`, egna i `bilder/egna/`).
- **Dokument**: mäklarens bostadsbeskrivning, mätbevis och planritningar samt föreningens årsredovisning, stadgar, energideklaration och underhållsplan. Filerna ligger i `dokument/`.

Formatet beskrivs överst i plantexten.

## Firebase

Sidan ligger på https://vasav23.web.app (Firebase Hosting, projekt `vasav23`). Publicera med `firebase deploy`.

- **Logga in** (i sidomenyn): Google-inloggning. Behörigheten styrs av `firestore.rules`: ägaren står i reglerna,
  övriga i Firestore-dokumentet `config/roller` som `{ skriv: [...], las: [...] }` med e-post i små bokstäver.
  Den som inte står med kommer inte åt något i databasen.
- **Planen i databasen**: inloggad med läsrätt hämtas planen från Firestore-dokumentet `planer/plan` och följs, så
  ändringar från andra ritas direkt. Med skrivrätt sparar **Spara** i Redigera plan. Finns inget dokument skapas det
  av planen i sidan. Ändras planen i `index.html` läses den in med "Återställ till inbyggd plan" och sedan Spara.
