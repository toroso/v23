# v23 – planlösning

Interaktiv planritning över lägenheten (undervåning och ovanvåning) med lager för ombyggnadsidéer.

Öppna `index.html` i en webbläsare. Allt ligger i den filen: planens text finns i blocket
`<script type="text/plain" id="plandata">`, och resten är ritmotorn.

- **Lager**: Undervåning och Ovanvåning är våningar. Ändringar (WC2, Sovrum3_Stor, Sovrum3_90, Sovrum3_WC1, Sovrum3_Ruff, WC1, Kök, FastGarderobNere, TaBortGU) slås på och av var för sig; Sovrum3_Stor, Sovrum3_90, Sovrum3_WC1 och Sovrum3_Ruff är alternativ, bara en av dem kan vara på.
- **Visa**: dörrar/fönster/öppningar, inredning, möbler, rumsnamn, mått och rutnät.
- **Redigera plan**: ändra texten direkt i sidan. Ändringar sparas lokalt i webbläsaren.
- **Skriv ut**: skriver ut allt som är valt under Lager och Visa på A4, i största skalan av 1:50, 1:100 och 1:200 som får plats, med skalstock.
- **Kopiera bild**: lägger planen som PNG på urklipp.
- **Bilder** (väljs i rubriken): originalplanen per våning; klicka på ett rum för att bläddra bland bilderna i `bilder/` (annonsens i `bilder/notar/`, egna i `bilder/egna/`).
- **Dokument**: mäklarens bostadsbeskrivning, mätbevis och planritningar samt föreningens årsredovisning, stadgar, energideklaration och underhållsplan. Filerna ligger i `dokument/`.

Formatet beskrivs överst i plantexten.
