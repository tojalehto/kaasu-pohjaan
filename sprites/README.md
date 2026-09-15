# Spritet

Tämän kansion PNG:t on leikattu AI-generoidusta sprite-arkista skriptillä
`tools/cut-sprites.py`. Jos generoit uuden arkin samalla asettelulla, aja:

    python3 -m venv .venv && .venv/bin/pip install pillow numpy scipy
    .venv/bin/python tools/cut-sprites.py ~/Downloads/uusi-arkki.png

Huom: arkin nimilaput player-left ja player-right ovat pelin kannalta
päinvastoin, joten skripti tallentaa ne ristiin. Jos uudessa arkissa
kallistukset ovat oikein päin, vaihda SPRITES-taulukon kaksi ensimmäistä nimeä.

Skootterin kolme kuvaa ovat samalla 157x160-kankaalla takarenkaan mukaan
kohdistettuina, jotta pyörä ei hypi kallistuksen vaihtuessa.

Erillinen taustakuva (esim. tarkempi siluetti) muunnetaan komennolla
`.venv/bin/python tools/cut-sprites.py --bg skyline kuva.png`.
Törmäysanimaation arkki leikataan komennolla `.venv/bin/python tools/cut-sprites.py --crash arkki.png`.

Yksittäisen spriten voi myös vain korvata: pudota PNG tähän oikealla nimellä.
Jos tiedosto puuttuu, peli piirtää koodilla tehdyn placeholderin.
Läpinäkyvä tausta, takaa päin kuvattuna.

Pikselikoko on vapaa. Sprite skaalataan `ww`-arvon (leveys maailman yksiköissä,
tien puolikas = 2000) mukaan, korkeus seuraa kuvan kuvasuhdetta. Arvot ovat
`src/assets.ts`-tiedoston SPRITE_WORLD_WIDTH-taulukossa.

| Tiedosto | Mitä | Nykyinen koko |
|---|---|---|
| player-straight.png | Mika ja David skootterilla, suoraan | 157x160 |
| player-left.png | sama, kallistus vasemmalle | 157x160 |
| player-right.png | sama, kallistus oikealle | 157x160 |
| car-0.png ... car-5.png | liikenneautot takaa | noin 95x60 |
| palm.png | palmu | 59x109 |
| lamp.png | lyhtypylväs | 35x102 |
| bush.png | pensas | 60x32 |
| gantry.png | opastegantry tien yli | 178x83 |
| billboard-0.png, billboard-1.png | mainostaulut | noin 60x50 |
| crash-bike-0..4.png | kaatuneen pyörän liuku, 5 ruutua yhteisellä kankaalla | 170x95 |
| crash-mika-0..2.png, crash-david-0..2.png | lentävät kuskit, 3 ruutua kumpikin | 140x126, 103x104 |
| logo.png | aloitusruudun logo, piirretään sellaisenaan 1:1 | 467x134 |
| sky.png | taivas, alareuna horisontissa, toistuu vaakasuunnassa (peilattu 1280 leveä) | 1280x200 |
| skyline.png | kaupungin siluetti, alareuna horisontissa, taivas läpinäkyvä | 1280x125 |
| skyline-sunset.png, skyline-dawn.png | siluetit pilvineen 1. ja 3. kierrokselle, taivaan yläosa piirretään koodissa | 1280x129, 1280x133 |
| near.png | lähimaisema horisontin edessä, yläosa läpinäkyvä | 1280x99 |

Osoitteessa `http://localhost:5173/#sprites` näet kaikki placeholderit ja voit
ladata ne PNG-pohjiksi.
