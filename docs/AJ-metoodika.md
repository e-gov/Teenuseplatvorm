---
permalink: AJ-soovitused
---

<img src='img/VAPP.PNG' style='width: 300px; margin: 0 0 1rem 0;'>

# Soovitusi andmejälgija rakendamiseks
{: .no_toc}

_teabekiri AJ rakendajatele_

12.06.2018

- TOC
{:toc}

## Sissejuhatus

Andmejälgija (AJ) rakendamisel tõusetub küsimusi, mis vajavad vastust. Samuti koguneb asutustel kogemusi, mis väärivad levitamist. Käesolevas teabekirjas anname soovitusi AJ-ga pakutava teabe andmesubjektile informatiivsemaks tegemiseks.

Kuidas hõlpsamini vastata kodanikele, kes AJ-s isikuandmete töötluse logiga tutvumise järel soovivad täpsemaid selgitusi?
{:.adv }

AJ on automatiseeritud lahendus. Isikuandmete töötluse faktid (logikirjed) salvestatakse X-tee andmeliiklusest eraldusfiltri töötlusreeglite automatiseeritud rakendamisega. Logikirjed esitatakse andmesubjektile eesti.ee-s iseteeninduse põhimõttel.

Logikirjed peavad olema kodanikule arusaadavad, äraseletavad ja vastama kodaniku küsimustele. Kuidas  seletamist automatiseerida?

Seletuse andmise täielik automatiseerimine üldjuhul ei ole võimalik. Kuid siiski on mitmeid võimalusi teha teave kodanikule paremini mõistetavaks. 

## 1 Selgitusvajadus 

Andmesubjektil võib AJ logiga tutvumise järel tekkida terve kimp üksteisega seotud küsimusi:

- Miks minu andmeid töödeldi?
- Mis eesmärgiga minu andmeid töödeldi?
- Mille alusel? 
- Miks toiming, mille raames andmeid töödeldi oli vajalik?
- Miks just need andmed?
- Milleks üks või teine andmeelement oli vajalik?
- Kas edastati ainult minimaalselt vajalik andmete komplekt?
- Kas andmete edastamine oli põhjendatud?
- Mis andmetest edasi sai?
- Kas andmed edastati turvalisel viisil?
- Kas keegi teine võis veel andmetel ligi saada?
- jne.

Märgime, et AJ kasutamispraktika ei ole veel suur. Empiiriline andmestu kodanike seletussoovide kohta puudub. Siiski võib eeldada, et vähemalt osa ülalloetletud küsimusi praktikas tekib. Asutusi huvitab, et sagedased küsimused saaksid vastuse AJ-s ega nõuaks kodaniku täiendavaid pöördumisi asutuse poole ning nendele pöördumistele (inimtööga) vastamist.

### "Suurema pildi" vajadus

Kodanik võib tahta teada konkreetse andmebiti edastamise asjaolusid. Kuid terviklike, kodanikele mugavate e-teenuste osutamiseks, aga samuti avaliku halduse mitmesuguste teiste ülesannete täitmiseks on sageli vaja kombineerida andmeid erinevatest andmekogudest. Teenuse osutamiseks ja isegi selle taustal võidakse teha mitmeid päringuid. Atomaarse andmepäringu mõistmine on tihti võimalik ainult teenuseosutamise või avaliku ülesande täitmise laiemat konteksti omades. Teiste sõnadega, kodanikul on tema kohta käiva andmetöötluse mõistmiseks vaja "suuremat pilti".

## 2 Selgitusvajaduse rahuldamine

Kuidas kodaniku selgitusvajadust rahuldada? Asutusel on kasutada mitmeid võimalusi.

### 2.1 Menetluse/toimingu nimetus (väli `action`)

Standardne element AJ logikirjes menetluse või toimingu nimetamiseks on väli `action`. Välja `action` saab täita staatiliselt, dünaamiliselt või käsitsi.

### 2.2 Staatiline

X-tee andmevahetusest tekkiv logikirje moodustatakse eraldusfiltris. Eraldusfiltri seadistamisel määratakse töötlusreegel välja `actioncode` täitmiseks. Tehniliselt on töötlusreegel XPath avaldis, mis kombineerib ühest või mitmest X-tee sõnumi väljast kokku välja `actioncode` väärtuse. Väli `actioncode` esitatakse eesti.ee-s andmesubjektile.

Valida välja `actioncode` staatiline väärtus hoolikalt.
{:.note }

Eraldusfiltri seadistamisel saab seada igale X-tee teenusele vastava `actioncode` teksti.  

### 2.3 Dünaamiline

Staatiline (kõigi päringute jaoks sama) `action` väärtus töötab hästi ainult ühelaadsete päringute puhul. Kuid X-tee teenuses võidakse edastada mitmesuguseid andmeid. Sealjuures võib samade andmete edastamise eesmärk olla erinev. Sellisel juhul tuleks `action` väärtus moodustada dünaamiselt, s.o konkreetse päringu andmete põhjal.

Varieeruva eesmärgi või andmete korral moodustada välja `actioncode` väärtus dünaamiliselt.
{:.note }

XPath avaldises saab kasutada nii:
- X-tee standardseid päiseelemente
- sõnumi keha (SOAP-sõnum) elemente
- kui ka X-tee täiendavaid päiseelemente.

Vaatleme nimetatud võimalusi lähemalt.

X-tee standardsetest päistest pakub suurimat huvi `issue`. Päis `issue` on mõeldud menetluse, juhtumi või toimingu masinloetava identifikaatori (numbri) edastamiseks. Sõltuvalt menetluste nummerdamise praktikast võib päis `issue` olla täidetud või tühi. Märgime, et menetlusnumbri esitamine kodanikule ei lahenda iseenesest seletamisprobleemi. Menetlusnumbri kõrval tuleks anda viide asutuse menetlussüsteemi avalikule liidesele, kust kodanik saaks menetlusega lähemalt tutvuda.

Sõnumi keha on SOAP standardile vastava XML-andmestruktuur. XPath töötlusreegliga saab sealt vajaliku teavet eraldada ja logikirjesse (välja ´action` kanda). Sõnumi keha võib seletuse koostamisel olla väga oluline teabeallikas. Abiks on X-tee levinud praktika peegeldada päringsõnumi sisu vastussõnumis. 

X-teel andmeid vahetavad asutused võivad kasutada täiendavaid, oma valitud päiseelemente (selles allpool, jaotises `requestreason`).

### 2.4 Käsitsi sisestatav

See moodus on mõeldav juhul, kui logikirje salvestatakse Andmesalvestajasse otse (vt skeemil - "mitte-X-tee andmekasutuste logimine") ja töötleja on asutuse töötaja. Asutuse töötaja sisestab iga  andmekasutustoimingu kohta seletuse, mis salvestatakse Andmesalvestajasse (välja `action`). Selline käsitsitöö on praktiline tõenäoliselt vaid siis, kui seletuse koostamine on tööprotsessi osa.

### 2.5 Eraldi selgitustekst

Iga andmetöötlusfakti eraldi seletamine ja põhjendamine AJ logikirjes võib olla ebapraktiline. Kirjeldus võib minna pikaks ja selle kordamine eesti.ee esitusteenuses ei ole UI seisukohalt hea. 

Soovitame asutustel kaaluda eraldi selgitusteksti koostamist.
{:.note } 

See tekst võib olla pikem ja anda andmekogus toimuvast isikuandmete töötlusest laiema pildi.

Eraldi selgitusteksti saab üles panna AJ esitusteenuses eesti.ee-s.

### 2.6 Andmetöötluspoliitika

Konteksti loomiseks ja kodaniku rahustamiseks võib suureks abiks olla hästi koostatud isikuandmete töötluse poliitika.

Kui andmekogul või infosüsteemil on avalik kasutajaliides, siis saab andmetöötluspoliitika dokumendi avaldada seal.

Andmetöötluspoliitika dokumendi saab avaldada ka RIHAs, [https://www.riha.ee](https://www.riha.ee).

### 2.7 Isikuandmete töötluse mõjuanalüüs

Kodanik võib soovida kindlust andvat teavet selle kohta, et tema isikuandmete töötlus on põhjendatud, minimaalne ja asjakohased kaitsemeetmed on rakendatud. Vastust võib pakkuda isikuandmete töötluse m
mõjuanalüüs (ühtse andmekaitsemääruse valguses). 

Hea koht mõjuanalüüsi ja rakendatud kaitsemeetmete kohta teabe avaldamiseks on RIHA.

### 2.8 Protsessikirjeldus

Kasutuskonteksti kirjeldus. Kodanik võib soovida täiendavat teavet menetlusprotsessidest jm avaliku sektori infotöötluse äriloogikast, mis tingisid vajaduse tema andmete töötluse järele.

Seda teabevajadust on otstarbekas rahuldada kodaniku juhatamisega RIHA-s avaldatud andmekogu arhitektuuri- ja protsessikirjelduste ning andmemudelite juurde. 

## 3 Standardimine

### 3.1 Vajadus

Kas X-teel ja/või AJ-s tuleks standardida täiendavaid kirjelduselemente, mis aitaksid selgitusvajadusi rahuldada? 
{:.adv}

Selliseks elemendiks võiks olla 'PÄRINGU PÕHJUS' (`requestreason`). Esitame järgnevalt kirjelduselemendi 'PÄRINGU PÕHJUS' standardimisettepaneku.

Ootame ettepaneku kohta arvamusi. Ettepanekut saab eksperimentaalselt kohe praktikas kasutada. Elemendi `requestreason` kohustuslikuks muutmist peame otstarbekaks alles konsensuse ja eksperimentaalse kasutuspraktika tekkimise järel.

Märgime, et üldise kohustuse panemisega (`requestreason` nõutav igas X-tee päringus) peab olema ettevaatlik. Kohustuse panemine iseenesest ei taga paremat andmekvaliteeti. Kirjelduselemendist oleks pigem kahju, kui seda hakatakse täitma formaalselt. Järelevalveks, arvestades tuhandeid X-tee teenuseid, ei ole kerge ressurssi leida. Seetõttu standard saab välja kasvada asutuste endi kujundatavast praktikast. 

### 3.2 Kirjelduselement `requestreason`

Kirjelduselement `requestreason`:
- esitatakse X-tee päringsõnumi päises
- või sõnumi kehas
- ja peegeldatakse X-tee vastussõnumis
- ei ole kohustuslik
- sisaldab inimloetavas keeles, andmesubjektile mõistetavat vastust küsimusele "Miks andmeid edastati?"
- on tekstiväli
- on kasutatav AJ välja `action` koostamiseks AJ eraldufiltri automatiseeritud töötlusreegli abil.

## LISA 1. AJ ülevaade

Andmejälgija, [https://github.com/e-gov/AJ](https://github.com/e-gov/AJ), (AJ), on standardne protokoll ja tarkvara, mille paigaldamisega saab asutus kodanikule pakkuda ülevaadet (logi) kodaniku isikuandmete kasutamisest.

<img src='img/AJ.PNG' style='width:750px;'>

## LISA 2. AJ logikirje

AJ protokoll näeb ette iga isikuandmete töötlemise fakti salvestamist 13 andmeväljast koosneva logikirjena.

Andmeväljad jagunevad andmesubjektile esitatavateks ja asutuse sisekasutuseks mõeldud, tehnilisteks andmeväljadeks. Lähemalt on andmeväljadest juttu AJ [tehnilises dokumentatsioonis](https://github.com/e-gov/AJ/blob/master/doc/spetsifikatsioonid/Tehniline_kontseptsioon.md) ja [paigaldusjuhendis](https://github.com/e-gov/AJ/blob/master/doc/Paigaldamine.md#h%C3%A4%C3%A4lestamine)).

### Andmesubjektile esitatavad andmeväljad

Logikirjed kuvatakse andmesubjektile (s.t kodanikule) eesti.ee AJ kuvamisteenuses. Avalikud andmeväljad on järgmised:

nr | nimetus    | tüüp       | kohustuslik | semantika
---|------------|------------|-------------|------------
1  | `personcode` | tekst | ei          | Isikukood: kelle andmeid töödeldi. Peab algama riigi prefiksiga EE.
2  | `logtime` | datetime   | jah         | Logikirje salvestamise aeg. Eeldatakse, et tegelik andmete kasutamise aeg on lähestikku.
3  | `action` | tekst  | jah | Menetluse/toimingu inimloetav nimetus. Tuletatakse kas X-tee päringu nimest ja/või seatakse andmetöötleja poolt. Võib, aga ei pruugi langeda kokku väljaga `actioncode` s.o sisekasutuseks ettenähtud nimetusega. 
4  | `receiver` | tekst | ei | Asutus, kellele andmed väljastati. Täidetakse andmete väljastamisel andmekogust teisele asutusele X-tee kaudu. Anda asutuse inimloetav nimi.
5  | `sender` | tekst | Asutus, kellelt andmed saadi. Täidetakse andmete saamisel teisest asutusest X-tee kaudu. Anda asutuse, vajadusel ka andmekogu inimloetav nimi.

### Sisekasutuseks mõeldud andmeväljad

nr | nimetus    | tüüp       | kohustuslik | semantika
---|------------|------------|-------------|------------
6  | `id`         | integer    | jah         | Logikirje identifikaator
7  | `restrictions` | char | ei | Kui väärtus ei ole `A`, siis logikirjet eesti.ee-s ei kuvata.
8  | `receivercode` | tekst | ei | Asutuse või andmekogu registrikood/sisekasutuse nimi, kellele andmeid edastatakse.
9  | `sendercode` | tekst | ei | Asutuse või andmekogu registrikood/sisekasutuse nimi, kellelt andmed saadi. 
10 | `actioncode` | tekst | ei | Menetluse/tegevuse sisekasutuseks ettenähtud nimi. Võib olla X-tee päringu nimi, andmeteenuse või andmekogu nimi vms.
11 | `xroadrequestid` | tekst | ei | X-tee päringu identifikaator.
12 | `xroadservice` | tekst | ei | Andmeid edastava X-tee teenuse nimi
13 | `usercode` | tekst | ei | X-tee kaudu andmeid pärinud isiku või asutusesisese töötleva isiku isikukood.
