# Vaatimusmäärittely

## Case EV-metalli Ky

EV-metalli Ky/Erkki Vihinen tarvitsisi tuntiseuranta/työnhallinta-ohjelmaa.
Tarkoituksena olisi, että yrityksen työntekijät kirjaisivat itse työaikojaan/mitä töitä ovat
tehneet kellekin asiakkaalle. Ohjelmasta saisi sitten kerättyä asiakas/työnumero-kohtaisesti tunnit.
(palkanlaskentaan)

Järjestelmän pitäisi tietysti olla helposti käytettävä ja muokattavissa jälkeenpäin,
esim. että voisi muuttaa/lisätä/poistaa asioita(työntekijät, työtehtävä ym.) ohjelmasta.

Tietokanta pitäisi olla jossain palvelimella, että tietoihin pääsisi kotoa, töistä tai vaikka työmaalta.

## Palvelukuvaus

Työstetään asiakkaalle yllämainittu järjestelmä. Järjestelmä koostuu kolmesta osasta: Tietokanta, Webserveri ja erillinen ohjelma backendille. Tietokantaan tallennetaan työntekijät, asiakkaat, tilaukset ja työmääräykset, sekä kirjautumistiedot. Webserverillä hostataan yksinkertaisia kotisivuja, jonne työntekijä kirjautuu kirjaamaan tunnit. Tehdään joko C# tai Javalla backend ohjelma, jolla voidaan muokata tietokannassa olevaa dataa.

## Sidosryhmät

![](/Kuvat/Sidosryhmat.png)

## Käyttötapaukset (Toimii myös testitapauksena)

### Työnantaja
[Työnantaja lisää työntekijän](ta_lisaa_tt.md)  
[Työnantaja lisää asiakkaan](ta_lisaa_as.md)  
[Työnantaja lisää tilauksen](ta_lisaa_til.md)  
[Työnantaja lisää työmääräyksen](ta_lisaa_tyo.md)

[Työnantaja poistaa työntekijän](ta_poistaa_tt.md)  
[Työnantaja poistaa asiakkaan](ta_poistaa_as.md)  
[Työnantaja poistaa tilauksen](ta_poistaa_til.md)  
[Työnantaja poistaa työmääräyksen](ta_poistaa_tyo.md)  

[Työnantaja muokkaa työntekijän](ta_muokkaa_tt.md)  
[Työnantaja muokkaa asiakkaan](ta_muokkaa_as.md)  
[Työnantaja muokkaa tilauksen](ta_muokkaa_til.md)  
[Työnantaja muokkaa työmääräyksen](ta_muokkaa_tyo.md)

### Työntekijä
[Työntekijä ilmoittaa tunnit](tt_ilmoittaa_tunnit.md)  
[Työntekijä muokkaa tunteja](tt_muokkaa_tunnit.md)  

## Toiminnalliset vaatimukset
| Id | Vaatimus|
|:-:|:-:|
|TV001| Ohjelmasta saa kerättyä asiakas tai työnumero-kohtaisesti tunnit palkanlaskentaan |
|TV002| Työntekijät voivat itse lisätä ja päivitellä työtuntejaan |
|TV003| Työnantaja voi poistaa Asiakkaita, Työntekijöitä, Tilauksia ja Työmääräyksiä |
|TV004| Työnantaja voi lisätä Asiakkaita, Työntekijöitä, Tilauksia ja Työmääräyksiä |
|TV005| Työnantaja voi muokata Asiakkaita, Työntekijöitä, Tilauksia ja Työmääräyksiä |
|TV006| Työnantaja voi luoda uuden salasanan unohtuneen tilalle työntekijälle |


## Ei-toiminnalliset vaatimukset
| Id | Vaatimus|
|:-:|:-:|
|ETV001| Palvelu pitää olla saatavilla kotona, töissä ja työmaalla |
|ETV002| MySQL tietokannan backupit pilveen joka päivä |
|ETV003| Ohjelma luo uusille työntekijöille uudet tunnukset ja antaa tiedot tulostettavaksi VAIN KERRAN |
|ETV004| Salasanoja ei pääse näkemään uudestaan ensimmäisen näytökerran jälkeen |
|ETV005| Ei saa löytyä hakukoneista |

## Palvelun/ohjelmiston arkkitehtuuri
MySQL tietokanta, Websivu HTML-CSS-Java, Sovellus C# tai Java. Työntekijä lisää tunnit websivulta. Työnantaja muokkaa tietokantaa sille suunnitellulla sovelluksella.

### Laitteisto
[Raspberry Pi Zero W](https://www.raspberrypi.org/blog/raspberry-pi-zero-w-joins-family/) pitäisi pystyä hoitamaan ei julkista palvelua yhdestä neljälle henkilölle, joka sisältää MySQL tietokannan ja kevyet websivut. Websivuilla työntekijät voivat lisätä, kun taas työnantajan sovellus pyörii itsenäisesti työnantajan koneella käskyttäen zeron tietokantaa.
