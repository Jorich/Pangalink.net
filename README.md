# Pangalink.net

## Eeldused

  * [Node.js](http://nodejs.org/), vähemalt versioon 5.0.0
  * [MongoDB](http://www.mongodb.org/)
  * GIT (valikuline. Vajalik koodi alla laadimiseks ja uuendamiseks, kuid mitte rakenduse tööks)

## Install

    git clone git://github.com/andris9/Pangalink.net.git
    cd Pangalink.net
    npm install

## Windowsi kasutajatele

Pangalink.net genereerib sertifikaadid `openssl` käsu abil. *nix süsteemides on `openssl` reeglina vaikimisi installitud, kuid Windowsis ei ole. Seega Pangalink.net kasutamiseks kontrolli, et OpenSSL oleks installitud ja Node.js jaoks saadaval, vastasel korral ei ole võimalik genereerida serte ja teenus ei hakka korralikult tööle.

## Konfiguratsioon

Muuda faili `config/default.js` väärtusi või või lisa NODE_ENV väärtuse nimega täiendav fail. Lisakonfiguratsioonifailid täiendavad, mitte ei asenda vaikimisi seadeid.

Näiteks kui tahad, et konfiguratsioon laetaks failidest *default.js* + *production.js*, käivita rakendus järgmiselt:

    NODE_ENV=production node index.js

## Käivitamine

    node index.js

Juhul kui veebiliides kasutab porti 80 või 443, pead käivitama rakenduse juurkasutaja õigustes.

## Docker

### Rakenduse ehitamine lähtekoodist

```sh
docker build -t bitweb/banklink-testing-tool .
```

### MongoDB käivitamine

```sh
docker run --name banklink_mongo -d mongo
```

### Rakenduse käivitamine

```sh
docker run -d --name="banklink" -p 80:80 --link banklink_mongo:db bitweb/banklink-testing-tool
```

## Litsents

**MIT**
