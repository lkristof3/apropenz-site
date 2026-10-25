# aprópénz – nyilvános tájékoztató oldalak

A mobilalkalmazásból hivatkozott oldalak:

- [Adatkezelési tájékoztató](privacy.md) → `/apropenz-site/privacy`
- [Felhasználási feltételek](aszf.md) → `/apropenz-site/aszf`
- [Támogatás és fióktörlés](support.md) → `/apropenz-site/support`

## A 2026. október 24-i frissítés állapota

**Helyi tervezet; közzététel előtt az alábbi nyitott pontokat rendezni kell.** A dokumentumok frissítési dátuma nem igazolja, hogy azok már hatályba léptek vagy megjelentek az élő webhelyen.

A szövegek az alkalmazás aktuális forráskódjával összevetve készültek. A felülvizsgálat nem jelent teljes jogi megfelelőségi igazolást, és nem ellenőrizte az éles szolgáltatói konzolok beállításait vagy a telepített backend verzióját.

### Közzététel előtt tisztázandó adatok

1. **Az üzemeltető és adatkezelő személye:** a `privacy.md` 1. és az `aszf.md` 1. pontjába a tényleges jogi név és megfelelő elérhetőségi/címadatok kerüljenek. Vállalkozás esetén a jogállásnak megfelelő nyilvántartási, adózási és egyéb kötelező szolgáltatói adatok is szükségesek lehetnek. A jelenlegi e-mail-cím nem azonosítja önmagában az adatkezelőt. Firebase általában adatfeldolgozó; nem helyettesíti az alkalmazás üzemeltetőjét.
2. **Szolgáltatói szerződések és adattovábbítás:** ellenőrizni kell a tényleges szerződő Google-, OpenAI-, RevenueCat- és Sentry-entitásokat, az adatfeldolgozási megállapodásokat, az EGT-n kívüli továbbítás tényleges garanciáit és a projekt régiós beállításait. A Functions `europe-west3` régiója nem bizonyítja az összes adat EU-n belüli kezelését.
3. **OpenAI-hangfeldolgozás:** a helyi alkalmazásforrás a hangbevitelhez is OpenAI-t használ (`gpt-transcribe`, majd `gpt-6-luna`). Közzététel előtt ellenőrizni kell az éles backend átállását és a tényleges fiók-, régiós és megőrzési beállításokat. A helyi módosítás nem igazolja az éles átállást.
4. **Megőrzési szabályok:** meg kell határozni és a tájékoztatóban pontosítani a tényleges Sentry-, Cloud Logging-, RevenueCat-, ügyfélszolgálati és mentési megőrzési időket, illetve az alkalmazandó jogi kivételeket. Az ismeretlen konzolbeállítások helyére nem került kitalált nap- vagy évszám.
5. **Jogos érdek és használati attribútumok:** dokumentálni kell az érdekmérlegelést a RevenueCat-attribútumokra és a hibakövetésre. Ellenőrizni kell, hogy az alkalmazott SDK-k és helyi hozzáférések miatt szükséges-e külön hozzájárulás vagy további választási lehetőség. A tájékoztató megfogalmazása önmagában nem pótolja ezt.
6. **Kiskorúak és fogyasztói tájékoztatás:** a korábbi 13 éves termékkorhatár nem helyettesíti a cselekvőképességi, hozzájárulási és az AI-szolgáltatói korhatárfeltételek vizsgálatát. Az értékesítési modell alapján ellenőrizni kell az ÁSZF szolgáltatói adatait, az elállás/felmondás részletes tájékoztatását, panaszkezelési határidőit és az illetékes békéltető testület adatait. Az áruházi vásárlási felületet is össze kell vetni ezekkel.
7. **Éles működés és áruházi adatlapok:** az éles backend és az App Store adatvédelmi / Google Play Data Safety nyilatkozatok legyenek összhangban a végleges szövegekkel. A tájékoztató használati jelzésekre, pénzügyi adatokra és hangfeldolgozásra is kiterjed.

### Forráskóddal igazolt, külön figyelmet igénylő működés

- A fióktörlő backend törli a felsorolt saját Firebase-rekordokat, de nem hív külön RevenueCat- vagy Sentry-törlési API-t. Ne ígérjünk automatikus, azonnali törlést minden szolgáltatónál.
- A helyi gyorsrögzítések felhasználónként AsyncStorage-ban maradhatnak. A kijelentkezés nem teljes helyi adattörlés.
- A hangbeviteli hook helyi hangfájlt hoz létre, és nem minden kimeneti ágon törli azt kifejezetten. Az adatbázisban nyers hangot nem tároló backend nem bizonyít helyi fájltörlést.
- A widget szerveroldali `_quickCaptures` rekordjai nyers szöveget és eredménymezőket tartalmazhatnak. A helyi tétel eltávolítása nem törli ezeket; a fióktörlés kezeli őket.
- A háztartás törlése eltávolítja a háztartást, meghívókat és tagsági kapcsolatokat; nem az összes közös pénzügyi dokumentum törlése. A fióktörlés a `userId` szerinti saját rekordokat célozza.
- A Google- és Apple-bejelentkezés látható a jelenlegi belépési felületen. Facebook-segédfüggvény maradt a forrásban, de nincs hozzá felhasználói belépési lehetőség; ezért nem szerepel kínált funkcióként.
- Az OpenAI szövegkinyerési kérés `store: false` beállítással fut. Ez nem tiltja le a szolgáltatói visszaélés-figyelési naplókat.

### Ellenőrzéshez használt alkalmazásforrások

A szülő alkalmazás-repozitóriumban:

- `src/features/auth/components/authentication-options.tsx`, `src/features/auth/api/authService.ts`, `src/shared/models/User.ts`
- `functions/src/completeOnboarding.ts`, `functions/src/appAccess.ts`, `src/features/subscription/models/app-access.ts`
- `src/features/subscription/constants/customer-attribute-policy.ts`, `src/features/subscription/components/customer-attribute-sync.tsx`, `src/features/subscription/lib/revenueCat.ts`
- `functions/src/textToTransactions.ts`, `functions/src/expenseResponses.ts`, `functions/src/expenseUnderstanding.ts`, `functions/src/categorizeQuickCapture.ts`
- `functions/src/voiceToTransactions.ts`, `src/features/transactions/hooks/use-expense-voice-input.ts`
- `functions/src/quickCapture.ts`, `src/features/transactions/api/quick-capture-storage.ts`, `src/features/transactions/components/widget-capture-processor.tsx`
- `functions/src/deleteAccount.ts`, `functions/src/householdFunctions.ts`
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
