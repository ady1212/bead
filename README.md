#Dokumentáció

#Alkalmazások fejlesztése beadandó

Készítette: Szabó Ádám - PSFKRI

#1.1 Követelményanalízis

    A projekt célja a szerveroldali technológiák megismerése és ezek használatával egy egyszerű feladat megoldása.
    Az alkalmazást a Tantárgyak felvétele példát valósítaná meg. Az alkalmazás alapja egy olyan weblap, ahol egy listába megtalálható a felhasználó által felvett tantárgyak.
    A felhasználó regisztráció után bejelentkezhet, bejelentkezés után tárgyakat vehet fel,  és a meglévőeket szerkeszteni és le is tudja adni.

I. Funkcionális követelmények:

    1. felhasználóként szeretnék felvenni egy tárgyat -> tárgy felvétele,
    2. felhasználóként szeretnék visszajelzést kapni, hogy a felvett tárgyak milyen státuszban vannak -> tárgyak listázása,
    3. felhasználóként szeretnék egy tárgyat szerkeszteni -> tárgy szerkesztése,
    4. felhasználóként szeretnék egy tárgyat törölni -> tárgy törlése,
    5. a felhasználók bejelentkezés után használhatják a funkciókat,

II. Nem funkcionális követelmények:

    1. felhasználóbarát,
    2. gyors működés,
    3. biztonságos működés: jelszavak kódolt tárolása, funkciókhoz való hozzáférés.

#1.2.Szakterületi fogalomjegyzék

    anonymus - azonosítatlan felhasználó
    student - azonosított felhasználó

#1.3. Használatieset-modell

I. Szerepkörök:

    1. anonymus: azonosítatlan felhasználó, aki megtekintheti a főoldalt, a regisztrációs felületet és a bejelentkezési felületet.
    2. student: bejelentkezett felhasználó, aki mindent elér, amit az azonosítatlan felhasználó, valamint felvehet tárgyakat, szerkesztheti annak tulajdonságait, hozzáfér a tárgyak listájához,
            leadhat egy-egy tárgyat,és még ki is tud jelentkezni.

II. Használati eset diagram:

    /docs/images/hasznalati_eset_diagram.png

III. Egy folyamat kifejtése

    1. Megjelenik a főoldalt
    2. Bejelentkezés
    3. Megjelenik a lista a tárgyakról
    4. Egy új tárgy felvétele

#Tervezés

#2.1. Architektúra terv

I. Oldaltérkép

    Anonymus:   - Főoldal
                - Regisztráció
                - Bejelentkezés

    Student:    - Főoldal
                - Regisztráció
                - Be- és kijelentkezés
                - Tárgyak listája
                - Új tárgy felvétele

II. Végpontok

    - GET / : főoldal
    - GET /login/signup : bejelentkező oldal
    - POST /login/signup : bejelentkezési adatok felküldése
    - GET /login/login : regisztrációs oldal
    - POST /login/login : regisztrációs adatok felküldése
    - GET /subjects/list : tárgyak listájának oldala
    - GET /subjects/new : új tárgy felvétele
    - POST /subjects/new : új tárgy felvétele, adatok küldése
    - GET /subjects/edit/:id: tárgy adatai
    - GET /subjects/delete/:id: tárgy törlése

#2.2. Felhasználóifelület-modell

    I. Oldalvázlatok, Designterv
        
        - Főoldal : /docs/images/home.png
        - Bejelntkezés : /docs/images/login.png
        - Regisztráció : /docs/images/signup.png
        - Tárgyak Listája : /docs/images/list.png
        
#2.3 Osztálymodell
    
    I. Adatmodell
   
        /docs/images/adatmodell.png
   
    II. Adatbázisterv
   
        /docs/images/adatbazis.png
   
    
Implementáció

#3.1. Fejlesztői környezet bemutatása

    A program fejlesztése során az alábbi fejlesztői környezeteket használtam:
    - gitHub - a gitHub biztosítja a tárhelyet az alkalmazásnak
    - cloud9 IDE - a kódolás törtönt itt


#3.2. Könyvtárstruktúrában lévő mappák funkciójának bemutatása

    A "config" mappa a waterline ORM konfigurációs fájlját tartalmazza.
    A "models", a "views" és a "controllers" mappák az MVC architektúrát valósítják meg.
    A "views" mappa almappái az oldal egyes részeinek megjelenítéséhez szükséges .hbs fájlokatt tartalmazzák.
    A "docs" mappa "images" mappájában tárolom a képeket amelyek a dokumentációhoz tartoznak.
    A "public" mappa "libs" mappája a tartalom megjelenítéséhez szükséges bootstrap, bootswatch és jquery mappákat tartalmazza.
    A ".tmp" mappa az adatbázist tárolja.

#Tesztelés

A tesztelés során a mocha és chai, a funcionális teszteléshez a zombie tesztrendszert használtam.
A tesztfájlok:

    - models/user.test.js
         felhasználó létrehozása
         felhasználó keresése

    - controllers/index.test.js
        felhasználó megtekinti a főoldalt


#Felhasználói dokumentáció

    A program futtatásához egy böngésző és a cloud9 rendszer szükséges.
    A program funcióinai az eléréséhez először regisztrálni kell, majd a regisztráció után be lehet jelentkezni, belépés után elérhetővé válnak különböző lehetőségek.
    Ilyenek a tárgyak listája, és az új tárgyak felvételét szolgáló aloldalak. A tárgyak listájában megtekinthetjük a felvett tárgyak tudnivalóit: neve, státusza, kurzuskódja és az időpontja.
    Az új tárgy felvétele oldal egy űrlap: ki kell tölteni adatokkal a mezőket: tárgy neve, kódja és időpontja.
    Itt a "Submit" gombra kattintva küldhetjük fel az adatokat a szerverre, ami helytelen kitöltés esetén jelzi a hibát, helyes kitöltés esetén pedig megjeleníti az új tárgyat a listaoldalon.

