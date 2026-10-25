# Adatkezelési tájékoztató

**Frissítve:** 2026. október 24.

Ez a tájékoztató az **aprópénz** mobilalkalmazásban kezelt személyes adatokról, azok felhasználásáról és az Ön jogairól szól. A tájékoztató megismerése nem jelent általános hozzájárulást minden adatkezeléshez: az egyes célok jogalapját külön ismertetjük.

## 1. Adatkezelő és kapcsolat

Az alkalmazás üzemeltetője határozza meg az adatkezelés célját és módját. A Firebase az alkalmazás felhasználói adatainak kezelésében általában az üzemeltető adatfeldolgozójaként jár el.

**Adatvédelmi kapcsolat:** [apropenzapp@gmail.com](mailto:apropenzapp@gmail.com).

## 2. Milyen adatokat kezelünk?

| Adatkör                    | Tartalom és forrás                                                                                                                                                                                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Fiók és profil             | Firebase-felhasználói azonosító, vendégfiók jelzése, létrehozási idő, bevezető lépések teljesítése; Google- vagy Apple-bejelentkezésnél az elérhető név, e-mail-cím és profilkép. Vendégként nem szükséges nevet vagy e-mail-címet megadni.                      |
| Pénzügyi nyilvántartás     | Ön által megadott kiadások és bevételek, forintösszegek, dátumok, megjegyzések, kategóriák és kategórialeírások, sablonok, ismétlődési beállítások, költségkeretek.                                                                                              |
| Háztartás                  | Háztartás neve, tulajdonosa, tagsági kapcsolatok, meghívott e-mail-címe, meghívó és meghívási állapot, közös nézethez rendelt pénzügyi adatok.                                                                                                                   |
| Szöveges bevitel és widget | Beírt szöveg, rögzítési idő, választott személyes vagy közös nézet, felismert és javított mezők, piszkozatok, feldolgozási állapotok és bizonylatok.                                                                                                             |
| Hangbevitel                | Az Ön által indított hangfelvétel, az abból felismert kiadási adatok és a feldolgozáshoz szükséges kategóriák.                                                                                                                                                   |
| Hozzáférés és vásárlás     | Próbaidő kezdete és vége, előfizetési jogosultság és lejárat, vásárlási és megújítási információk, áruházi tranzakcióazonosítók. Bankkártyaszámot az alkalmazás nem kap meg.                                                                                     |
| Használati jelzések        | Bevezető lépések és legalább három tranzakció alapján számított aktiválási jelzés, személyes tranzakciószám-tartomány, valamint a költségkeret és a hangbevitel használatának igen/nem jelzése.                                                                  |
| Működés és biztonság       | Hibajelentések, hibaüzenetek, technikai környezet és alkalmazásverzió, felhasználói azonosító, API-használati számlálók, időbélyegek, biztonsági és hitelesítési adatok. A szolgáltatók a kérések fogadásakor IP-címet és más technikai adatokat is kezelhetnek. |
| Ügyfélszolgálat            | Az elküldött e-mail-cím, üzenet és az Ön által csatolt információk.                                                                                                                                                                                              |

Ne írjon jelszót, bankkártyaadatot vagy szükségtelenül érzékeny személyes adatot a megjegyzésekbe, kategórialeírásokba vagy AI-nak küldött szövegbe; más személy hangját és adatait csak megfelelő jogosultsággal adja meg.

## 3. Célok és jogalapok

| Cél                                                                                                                               | Jogalap                                                                                                                                                    |
| --------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Fiók, pénzügyi nyilvántartás, szinkronizálás, költségkeretek, sablonok és az Ön által választott háztartási megosztás működtetése | Szerződés teljesítése, GDPR 6. cikk (1) b).                                                                                                                |
| Ön által igénybe vett szöveges vagy hangos feldolgozás, widgetrögzítés                                                            | A kért szolgáltatás teljesítése, GDPR 6. cikk (1) b). A mikrofonhoz külön készülékengedély szükséges; ez önmagában nem általános adatvédelmi hozzájárulás. |
| Próbaidő és előfizetési jogosultság ellenőrzése                                                                                   | Szerződés teljesítése, GDPR 6. cikk (1) b).                                                                                                                |
| Visszaélések megelőzése, szolgáltatásbiztonság, hibafeltárás és használati korlátok                                               | Jogos érdek, GDPR 6. cikk (1) f): a szolgáltatás és a felhasználói adatok védelme, megbízható működés.                                                     |
| Korlátozott használati jelzések alapján az előfizetési ajánlatok és az aktiválás értékelése                                       | Jogos érdek, GDPR 6. cikk (1) f): a szolgáltatás használatának és az előfizetési ajánlatok eredményességének megértése. Ezzel szemben tiltakozhat.         |
| Ügyfélszolgálat és adatvédelmi kérelmek                                                                                           | Szerződés teljesítése, illetve jogi kötelezettség teljesítése, GDPR 6. cikk (1) b) és c), a megkeresés jellegétől függően.                                 |

A fiók és az adott funkció működéséhez szükséges adatok nélkül az érintett szolgáltatás nem nyújtható. A hangbevitel és a háztartási megosztás választható; kiadást kézi űrlapon is rögzíthet.

## 4. AI-funkciók és hangfelvétel

### Szöveges értelmezés és kategorizálás – OpenAI

A szöveges bevitel egy része helyben értelmezhető. Amikor AI-feldolgozás történik, a szerver az értelmezendő szöveget, a kapcsolódó kiadási mezőket, a kategóriák azonosítóit, neveit és leírásait, valamint az értelmezéshez szükséges dátumot továbbítja az OpenAI API-nak. A kategórialeírásokba írt személyes információk is részei lehetnek ennek az adatátadásnak. Az AI-kérés összeállításához nem szükséges a felhasználó neve vagy e-mail-címe.

Az OpenAI API adatait alapértelmezés szerint nem használja modelljei tanítására. A szövegkinyerési kérésben a válasz tárolását letiltjuk (`store: false`); ez nem jelenti a szolgáltatói biztonsági naplók kizárását. Az OpenAI alapértelmezett visszaélés-figyelési naplói legfeljebb 30 napig őrizhetők meg, jogi vagy biztonsági kivételekkel. Részletek: [OpenAI adatkezelési beállítások](https://developers.openai.com/api/docs/guides/your-data).

### Hangbevitel – OpenAI

A mikrofon csak az Ön által indított felvételhez szükséges. A feldolgozás indításakor a hangfelvétel a Firebase szerverén keresztül az OpenAI átíró API-jához kerül. Az elkészült átiratot egy második OpenAI-kérés értelmezi, a kiadási kategóriák nevével, leírásával és a dátumértelmezéshez szükséges információval együtt. A válaszban felismert összegek, dátumok, kategóriák és megjegyzések jelennek meg.

Az alkalmazás backendje nem menti a nyers hangot a pénzügyi adatbázisba. A készüléken átmeneti hangfájl keletkezik, amelyet a jelenlegi megvalósítás nem minden esetben töröl kifejezetten a feldolgozás után. Az átiratot sem mentjük a pénzügyi adatbázisba. Az értelmezési kérés `store: false` beállítással fut. A szolgáltatói adatkezelésre az OpenAI fent hivatkozott feltételei és a tényleges fiókbeállítások irányadók. Az alkalmazás nem végez háttérben folyamatos hangrögzítést.

### Eredmények és automatikus rögzítés

A normál szöveges és hangos bevitel eredményeit mentés előtt ellenőrizheti és javíthatja. A widgetből indított gyorsrögzítés megfelelően felismerhető kiadást automatikusan elmenthet; a bizonytalan tételek ellenőrzésre várnak. Az AI tévedhet, ezért a mentett tételeket is érdemes ellenőrizni. Ezek a funkciók nem hoznak hitelbírálati vagy más, Önre joghatással járó pénzügyi döntést.

## 5. Kik férhetnek hozzá az adatokhoz?

- **Google Firebase / Google Cloud:** hitelesítés, Firestore-adattárolás, szerveroldali feldolgozás, technikai naplók és App Check biztonsági ellenőrzések. [Firebase adatvédelem](https://firebase.google.com/support/privacy).
- **OpenAI:** a 4. pont szerinti szöveges értelmezés, kategorizálás és hangfeldolgozás.
- **RevenueCat:** felhasználói azonosító, előfizetési és vásárlási információk, technikai adatok, valamint az aktiválás, tranzakciószám-tartomány (`0`, `1–2`, `3–9`, `10–49`, `50+`), költségkeret- és hangbevitel-használat jelzése. Az alkalmazás ezekben az egyéni attribútumokban nem küld konkrét összegeket, tranzakcióleírásokat, kategórianeveket vagy hangot. [RevenueCat adatvédelem](https://www.revenuecat.com/privacy).
- **Sentry:** hibakövetés, technikai hibajelentések és a Firebase-felhasználói azonosító. Az alapértelmezett személyesadat-küldés és a Sentry Logs ki van kapcsolva; ez nem zárja ki, hogy egy hibaüzenet személyes adatot tartalmazzon. [Sentry adatvédelem](https://sentry.io/privacy/).
- **Google és Apple bejelentkezési szolgáltatás:** a választott bejelentkezéshez szükséges adatok. [Google adatvédelem](https://policies.google.com/privacy), [Apple adatvédelem](https://www.apple.com/legal/privacy/).
- **Apple App Store / Google Play:** vásárlás és fizetés, saját feltételeik szerint. A fizetési adatokat az áruház kezeli.
- **Háztartás tagjai:** a közös nézethez rendelt adatok és a tagság kezeléséhez szükséges profiladatok. A személyes és a közös nézet közötti választás előtt ellenőrizze, kivel kívánja megosztani a tételt.

A Google és az Apple például a saját fiók- és fizetési szolgáltatásukhoz önálló adatkezelőként is eljárhatnak. A külső szolgáltatók igénybevétele nem szünteti meg az alkalmazás üzemeltetőjének adatkezelői felelősségét.

## 6. Tárolás, biztonság és nemzetközi adattovábbítás

A felhőadatokat Firebase-ben tároljuk, a szerverfunkciók konfigurált régiója `europe-west3`. Ez önmagában nem jelenti, hogy valamennyi szolgáltató minden adatot kizárólag az EU-ban kezel. Az AI-, hitelesítési, előfizetési és hibakövetési szolgáltatások az EGT-n kívül, például az Egyesült Államokban is végezhetnek adatkezelést.

Az ilyen továbbításokhoz az alkalmazandó szolgáltatói szerződések szerinti GDPR-garanciák szükségesek, például megfelelőségi határozat vagy általános szerződési feltételek. A ténylegesen alkalmazott garanciákról és azok másolatáról a kapcsolattartási címen kérhet tájékoztatást.

A hálózati adatátvitel titkosított. A hozzáférést hitelesítés, adatbázis-jogosultságok és a támogatott kéréseknél alkalmazás-ellenőrzés védi. Teljes kockázatmentességet nem lehet garantálni.

A készülék helyi tárhelyén bejelentkezési állapot, beállítások és gyorsrögzítési piszkozatok is maradhatnak. Ezek nem mind azonosak a szerveren tárolt adatokkal; a kijelentkezés nem jelent minden helyi adatot érintő törlést.

## 7. Megőrzés és törlés

- A profil és a pénzügyi nyilvántartás adatait a fiók fennállásáig, illetve az adott adat törléséig kezeljük. A próbaidő vagy előfizetés lejárata önmagában nem törli a korábbi adatokat.
- A widget szerveroldali feldolgozási rekordjai és használati számlálói megmaradhatnak a fiók törléséig; a helyi piszkozat eltávolítása nem feltétlenül törli a szerver feldolgozási rekordját.
- A fióktörlés a **Továbbiak → Fiók és beállítások → Fiók törlése** útvonalon indítható, vagy e-mailben kérhető. Az e-mailes kérelemnél a jogosultságot ellenőrizzük.
- A fióktörlés eltávolítja a Firebase-fiókot és a hozzá tartozó, az alkalmazás törlési folyamatával kezelt profilt, saját pénzügyi rekordokat, hozzáférési és használati adatokat, valamint az érintett meghívókat. A saját tulajdonú háztartás megszűnik, tagjainál a tagsági kapcsolat törlődik. Más tagok által létrehozott rekordok nem válnak ettől automatikusan az Ön törlendő adataivá.
- A törlés nem vonható vissza. Az alkalmazás nem ígér minden rendszerre és biztonsági másolatra kiterjedő azonnali törlést: a szolgáltatói naplók, biztonsági másolatok, áruházi bizonylatok és jogszabály alapján megőrzendő adatok külön megőrzés alá eshetnek. A Firebase Authentication tájékoztatója szerint a törlés kezdeményezése után a hitelesítési adatok eltávolítása az éles és mentési rendszerekből legfeljebb 180 napot vehet igénybe.
- A jelenlegi fióktörlési folyamat nem indít külön RevenueCat- vagy Sentry-adattörlést. Az ezekhez kapcsolódó kérelmekkel is írhat az adatvédelmi címre; a kérelem terjedelméről és a megőrzés indokairól tájékoztatást adunk.
- A készüléken maradt adatok eltávolításához az alkalmazás helyi adatainak törlése is szükséges lehet. A készülék és az operációs rendszer mentései külön kezelendők.

**A fiók vagy az alkalmazás törlése nem mondja le az áruházi előfizetést.** A megújítást külön kell leállítani az Apple vagy a Google előfizetési beállításaiban.

## 8. Jogok és kérelmek

Az alkalmazandó feltételek szerint kérheti a hozzáférést, helyesbítést, törlést, az adatkezelés korlátozását és a szerződésen vagy hozzájáruláson alapuló, automatizáltan kezelt adatok hordozhatóságát. Jogos érdeken alapuló adatkezeléssel szemben saját helyzetére tekintettel tiltakozhat. Hozzájáruláson alapuló adatkezelésnél a hozzájárulást bármikor visszavonhatja, a korábbi kezelés jogszerűségének érintése nélkül.

Kérelmét az [apropenzapp@gmail.com](mailto:apropenzapp@gmail.com) címre küldheti. Az adatok védelmében szükség lehet személyazonossága arányos ellenőrzésére. Indokolatlan késedelem nélkül, főszabály szerint egy hónapon belül válaszolunk; indokolt hosszabbításról és annak okáról ezen belül tájékoztatjuk. Az adathordozhatósági kérelmet e-mailben lehet előterjeszteni; nem állítjuk, hogy az alkalmazásban külön exportgomb érhető el.

Panaszt tehet az illetékes felügyeleti hatóságnál, Magyarországon a **Nemzeti Adatvédelmi és Információszabadság Hatóságnál (NAIH)**, és bírósághoz fordulhat:

- [NAIH ügyfélszolgálat és hivatalos ügyintézési lehetőségek](https://naih.hu/ugyfelszolgalat-kapcsolat)
- Cím: 1055 Budapest, Falk Miksa utca 9–11.
- Levelezési cím: 1363 Budapest, Pf. 9.
- E-mail: ugyfelszolgalat@naih.hu. A NAIH tájékoztatása szerint eljárás egyszerű e-mailben nem kezdeményezhető; a hivatalos benyújtási módokat a hivatkozott oldalon találja.

## 9. Gyermekek, hirdetések és használati elemzés

Az alkalmazást nem 13 év alatti gyermekeknek szánjuk. Kiskorú használatánál a jogszabályok szerinti törvényes képviselői közreműködés szükséges lehet; a korhatár önmagában nem helyettesíti ezt. Ha gyermek jogosulatlan adatközléséről tud, jelezze a kapcsolattartási címen.

Az alkalmazás nem jelenít meg hirdetéseket. A „nem használunk analitikát” állítás helyett a tényleges működést ismertetjük: RevenueCat használati attribútumokat és előfizetési adatokat, Sentry technikai hibajelentéseket kezel az 5. pont szerint. Ezek a fiókhoz kapcsolhatók, ezért nem tekintjük őket anonim adatoknak.

## 10. Változások és kapcsolódó oldalak

A tájékoztatót a működés változásakor frissítjük, és feltüntetjük a frissítés dátumát. Ahol jogszabály külön tájékoztatást vagy hozzájárulást követel meg, azt a szöveg közzététele vagy az alkalmazás további használata nem helyettesíti.

[Felhasználási feltételek](aszf) · [Támogatás és fióktörlés](support)
