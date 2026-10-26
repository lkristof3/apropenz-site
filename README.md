# aprópénz – nyilvános tájékoztató oldalak

> Belső munkajegyzet. A `_config.yml` kizárja a GitHub Pages-buildből, így a nyilvános oldalon nem jelenik meg; a nyitóoldal az `index.md`.

A mobilalkalmazásból hivatkozott oldalak:

- [Adatkezelési tájékoztató](privacy.md) → `/apropenz-site/privacy`
- [Felhasználási feltételek](aszf.md) → `/apropenz-site/aszf`
- [Támogatás és fióktörlés](support.md) → `/apropenz-site/support`

## A 2026. október 26-i frissítés állapota

**Helyi tervezet.** A dokumentumok frissítési dátuma nem igazolja, hogy azok már hatályba léptek vagy megjelentek az élő webhelyen.

A szövegek az alkalmazás aktuális forráskódjával összevetve készültek. A felülvizsgálat nem jelent teljes jogi megfelelőségi igazolást.

### Rendezett pontok (2026. október 26.)

- **Üzemeltető:** Ladányi Kristóf egyéni vállalkozó; a szolgáltatói adatok a `privacy.md` és az `aszf.md` 1. pontjában szerepelnek. Az adóazonosító jel szándékosan nem nyilvános.
- **Adatfeldolgozói szerződések:** az üzemeltető közlése szerint a Google/Firebase, OpenAI, RevenueCat és Sentry feltételei elfogadva.
- **Tárolási hely:** a Firestore éles adatbázisa `eur3` (EU többrégiós), a Functions régiója `europe-west3`, a Sentry EU-s fogadóponton (`ingest.de.sentry.io`) kap adatot. Ütemezett Firestore-mentés és időpontra visszaállítás nincs bekapcsolva (2026. október 26-án ellenőrizve).
- **Megőrzés:** szolgáltatói alapértékek – Sentry legfeljebb 90 nap (csomagtól függően 30 vagy 90), Cloud Logging `_Default` 30 nap és `_Required` 400 nap, OpenAI legfeljebb 30 nap; ügyfélszolgálati panasz 3 év (Fgy. tv. 17/A. §), egyéb levelezés 1 év.
- **Korhatár:** az alkalmazás 18 év felettieknek szól; a Google Play célközönsége is 18+.
- **Békéltető testület:** Budapesti Békéltető Testület (székhely szerint).
- **Áruházi adatlapok:** a javasolt App Privacy és Data safety válaszok a szülő repozitórium `docs/store-privacy-declarations.md` fájljában.

### Közzététel előtt még szükséges

1. **Éles backend telepítése:** 2026. október 26-án az éles `voiceToTransactions` még Geminit használt (`GEMINI_API_KEY`), a widgetfeldolgozó függvények (`submitQuickCapture`, `processWidgetCapture`) és a visszaélés-védelmi korlátok nem voltak élesítve. A tájékoztató az OpenAI-alapú hangfeldolgozást írja le, ezért csak a Functions éles telepítése után tehető közzé.
2. **Áruházi adatlapok kitöltése** a fenti dokumentum szerint, a közzétett szöveggel összhangban.

### Jogos érdek – rövid érdekmérlegelés

- **Hibakövetés (Sentry):** cél a hibák feltárása és a szolgáltatás biztonsága. Csak technikai adat és a Firebase-azonosító kerül át, `sendDefaultPii: false`, naplók kikapcsolva, EU-s fogadópont, legfeljebb 90 napos megőrzés. A felhasználó észszerűen számíthat rá egy előfizetéses alkalmazásnál; a hatás csekély.
- **RevenueCat-használati attribútumok:** cél az előfizetési ajánlatok és az aktiválás értékelése. Csak igen/nem jelzések és tranzakciószám-tartomány; összeg, leírás, kategória vagy hang nem. Hirdetési vagy alkalmazásokon átívelő követés nincs. A felhasználó a kapcsolattartási címen tiltakozhat; ehhez jelenleg nincs alkalmazáson belüli kapcsoló, a kérelmet egyedileg kezeljük.

### Forráskóddal igazolt, külön figyelmet igénylő működés

- A fióktörlő backend törli a felsorolt saját Firebase-rekordokat, de nem hív külön RevenueCat- vagy Sentry-törlési API-t. Ne ígérjünk automatikus, azonnali törlést minden szolgáltatónál.
- A helyi gyorsrögzítések felhasználónként AsyncStorage-ban maradhatnak. A kijelentkezés nem teljes helyi adattörlés.
- A hangbeviteli hook helyi hangfájlt hoz létre, és nem minden kimeneti ágon törli azt kifejezetten. Az adatbázisban nyers hangot nem tároló backend nem bizonyít helyi fájltörlést.
- A widget szerveroldali `_quickCaptures` rekordjai nyers szöveget és eredménymezőket tartalmazhatnak. A helyi tétel eltávolítása nem törli ezeket; a fióktörlés kezeli őket.
- A háztartás törlése eltávolítja a háztartást, meghívókat és tagsági kapcsolatokat; nem az összes közös pénzügyi dokumentum törlése. A fióktörlés a `userId` szerinti saját rekordokat célozza.
- A Google- és Apple-bejelentkezés látható a jelenlegi belépési felületen. Facebook-segédfüggvény maradt a forrásban, de nincs hozzá felhasználói belépési lehetőség; ezért nem szerepel kínált funkcióként.
- A hangfelvételt a szerver átmeneti fájlban dekódolja és normalizálja (`functions/src/voiceAudio.ts`), majd a fájlt sikeres és sikertelen ágon is törli. A kliens 55 másodpercnél leállítja a felvételt, a szerver 60 másodperc felett elutasítja.
- Háztartási meghívó csak ellenőrzött (`email_verified`) e-mail-címmel fogadható el.
- Az OpenAI szövegkinyerési kérés `store: false` beállítással fut. Ez nem tiltja le a szolgáltatói visszaélés-figyelési naplókat.

### Ellenőrzéshez használt alkalmazásforrások

A szülő alkalmazás-repozitóriumban:

- `src/features/auth/components/authentication-options.tsx`, `src/features/auth/api/authService.ts`, `src/shared/models/User.ts`
- `functions/src/completeOnboarding.ts`, `functions/src/appAccess.ts`, `src/features/subscription/models/app-access.ts`
- `src/features/subscription/constants/customer-attribute-policy.ts`, `src/features/subscription/components/customer-attribute-sync.tsx`, `src/features/subscription/lib/revenueCat.ts`
- `functions/src/textToTransactions.ts`, `functions/src/expenseResponses.ts`, `functions/src/expenseUnderstanding.ts`, `functions/src/categorizeQuickCapture.ts`
- `functions/src/voiceToTransactions.ts`, `functions/src/voiceAudio.ts`, `functions/src/voiceExpenseUnderstanding.ts`, `src/features/transactions/hooks/use-expense-voice-input.ts`
- `functions/src/quickCapture.ts`, `src/features/transactions/api/quick-capture-storage.ts`, `src/features/transactions/components/widget-capture-processor.tsx`
- `functions/src/deleteAccount.ts`, `functions/src/householdFunctions.ts`, `functions/src/creationLimits.ts`, `functions/src/subscriptionSyncLimit.ts`
- `src/app/_layout.tsx`, `src/features/account/screens/settings-screen.tsx`

### Hivatalos háttérforrások

- [GDPR, különösen a 12–14. és 15–22. cikk](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32016R0679)
- [Firebase adatvédelem, adatkezelő/adatfeldolgozó szerepek és Authentication-megőrzés](https://firebase.google.com/support/privacy)
- [OpenAI API adatkezelés](https://developers.openai.com/api/docs/guides/your-data)
- [RevenueCat adatvédelem](https://www.revenuecat.com/privacy)
- [Sentry adatvédelem](https://sentry.io/privacy/)
- [Apple előfizetés és visszatérítés](https://support.apple.com/billing)
- [Google Play lemondás](https://support.google.com/googleplay/answer/7018481?hl=hu)
- [Google Play visszatérítési szabályok](https://support.google.com/googleplay/answer/15574908?hl=hu)
- [NAIH elérhetőség és benyújtási módok](https://naih.hu/ugyfelszolgalat-kapcsolat)

## Git és közzététel

Ez külön Git-repozitórium. A mobilalkalmazás `.gitmodules` fájlja hivatkozik rá, de a vizsgálatkor az alkalmazás Git-indexében nem volt hozzá submodule-bejegyzés. A helyi klónozás nem állította vissza automatikusan a gitlinket.

A változtatásokat ebben a repozitóriumban kell áttekinteni és később commitolni. A közzététel külön lépés; a helyi dokumentumok szerkesztése nem frissíti automatikusan az élő oldalakat.
