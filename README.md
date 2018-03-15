# visualiseerimisplatvorm-EXAMPLES

## Andmestiku/andmebaasi struktuur

| Andmevälja nimetus  | Kirjeldus |
| ------------- | ------------- |
| CATEGORY  |  Skaneeringu tulemuste põhjal leitud veebiteenus või seade tuleb liigitada ja lisada vastavasse kategooriasse, mis seda kõige paremini kirjeldab. Kategooriateks võivad näiteks olla: iot, ics jne. Andmetüübist tulenevalt tuleb kasutada ainult väiketähelisi stringe  |
| DESCRIPTION| Vabas vormis veebiseadme või teenuse kirjeldus, mis annab kokkuvõtliku ja lühida ülevaate sündmusest. Näiteks: „turvanõrkus XXX versioon X.X.X“ Kasutada tuleb kokkulepitud kirjeldusi |
| IP | Skaneeritud veebiseadme või teenuse IP-aadress | 
| PORT | Teenuse/seadme port |
| ASN | Autonoomsüsteemi (AS) number, kelle halduses IP-aadress skaneeringu ajal oli |
| TIME | Ajatempel, millal veebiseade või teenus skaneeriti |
| GEOIP | Skaneeritud IP-aadressi maakood |
| FQDN | Kui skaneeringu tulemused sisaldavad domeene, tuleb need märkida täisdomeeninimega (FQDN) |
| TAGS | Informatsioon, mida ei saa väljendada eelkirjeldatud andmeväljadega |

Hetkel oleme CERTis selliselt kokku leppinud, et hakkame tulevikus skaneeringu tulemusi sellisele struktuurile viima.
Selline stuktuur põhineb IntelMQ nromaliseerimise nõuetele ning üritasime valida andmevälju, et kõik baasid kaetud, kui peaks aga midagi tähtsat puudu olema ning IntelMQ toetab seda, saab andmevälju juurde lisada.
Isegi kui ei anna juurde lisada andmevälju siis TAGS andmeväli võimaldab rikastada andmestike märksõnade jms, mis võimaldaksid siis andmeid paremini kirjeldada ja hilisemaid otsinguid lihtsustada.

## Dashboard e koondpaneel

Toon piltidega välja mõned funktsionaalsused, mis võiksid huvi pakkuda. Andmed, mida olen näidete loomiseks kasutanud ei vasta reaalsusle ning kuna ma ise ka visuaali koha pealt väga kogenund ei ole siis ei ole ka mingeid uhkeid/kasulike graafikuid aga järgenvad näited võiksid andma aimu, mida on võimalik teha.

Milline oleks üks ülilihtne/basic koondpaneel e dashboard

![dashboard_kibana](https://user-images.githubusercontent.com/34548027/37480049-e57761d0-2886-11e8-9b48-8626159524ff.png)

**Time Range**

Väga lihtne on valida ajavhemik ja keskenduda ainult soovitavale ajavahemikule. 

![time_range](https://user-images.githubusercontent.com/34548027/37480460-fa452966-2887-11e8-86c4-0e29189b7a41.png)


**Otsingud**

Väga hea tööriist on otsinguriba, mis töötab peaaegu, et samadel põhimõtetel nagu Google otsingud.
Ehk kasutajal ei ole vaja teada süva teadmisi andmestikust endast vaid märksõnade abil on otsngumootor võimeline tagastama kasutajale relevantsuse järgi tulemusi. Kui tulemus ei ole rahuldav saab otsingutulemust täpsustada ning kasutada operaatoreid nagu AND; OR; NOT jne

Tulevikus on lootust tagasi saada automaatjätkamine (autocompletion) featuur, mis tooks antud funktsionaalsuse veelgi lähemale kõigile tuntavale Google-le

![otsingud](https://user-images.githubusercontent.com/34548027/37480831-e364e06e-2888-11e8-8f35-32edf312b317.png)

## Discover

Dashboard on kindlasti hea tööriist kui õigesti kasutada aga, et andmeid korralikult käsitleda pakub Kibana siis **Discover** funktsionaalsust

![dicover](https://user-images.githubusercontent.com/34548027/37481465-7edff3f2-288a-11e8-8761-becd16414725.png)

Antud funktsionaalsus on tõenäoliselt esimene asi, mida kasutaja kasutab ning annab väga head võimalused aru saada täpselt, mis andmetegea on tegu. Siin isegi rohkem kui Dashboadis tuleb kasuks samamoodi otsinguriba, mis annab võimaluse otsida huvipakkuvat infot.

Näiteks otsingu päring
```
iot AND PORT:36
```
annab andmestiku põhjal vastuseks kõik skaneeringu tulemused, mis sisaldavad siis **iot** ja kasutavad porti 36

![result](https://user-images.githubusercontent.com/34548027/37482057-00dac21e-288c-11e8-9f1c-9bc189265096.png)

Pildilt on näha siis, et vastuseks tuli 7 tulemuset, näidatakse nende skaneeringu tulemuste täpne sisu, mida on siis kasutajal veel võimalik edasi käsitleda. Kas eemaldades andmevälju, mis teda ei huvita, valides täpsema ajavahemiku või kui vaadates vasakule on võimalik luua kiire arusaam kui suure osakaalu mingid andmeväärtused kogu andmestikust moodustavad (vaata IP vasakul).

Kahjuks baaspakett ei sisalda raporti loomise võimalust aga väikese vaevaga saaks ka selle funktsionaalsuse. Vastavalt kasutaja otsingutele ja soovidele oleks siis võimalik tulemuseks saadud andmestik Exceli kujule viia.

## Kokkvõttes

Erinevaid funktsionaalsusi on veel kõvasti ja tegemist on väga interaktiivse tööriistaga ehk piltidega raske näiata aga loodetavasti põhi funktsioonidest antud kirjeldused andsid arusaama.
