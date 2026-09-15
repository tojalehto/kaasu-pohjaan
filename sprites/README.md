# Spritet

Tämän kansion PNG:t on leikattu AI-generoidusta sprite-arkista skriptillä
`tools/cut-sprites.py`. Jos generoit uuden arkin samalla asettelulla, aja:

    python3 -m venv .venv && .venv/bin/pip install pillow numpy scipy
    .venv/bin/python tools/cut-sprites.py ~/Downloads/uusi-arkki.png

Huom: arkin nimilaput player-left ja player-right ovat pelin kannalta
päinvastoin, joten skripti tallentaa ne ristiin. Jos uudessa arkissa
kallistukset ovat oikein päin, vaihda SPRITES-taulukon kaksi ensimmäistä nimeä.

Skootterin kolme kuvaa ovat samalla 105x107-kankaalla takarenkaan mukaan
kohdistettuina, jotta pyörä ei hypi kallistuksen vaihtuessa.

Yksittäisen spriten voi myös vain korvata: pudota PNG tähän oikealla nimellä.
Jos tiedosto puuttuu, peli piirtää koodilla tehdyn placeholderin.
Läpinäkyvä tausta, takaa päin kuvattuna.

Pikselikoko on vapaa. Sprite skaalataan `ww`-arvon (leveys maailman yksiköissä,
tien puolikas = 2000) mukaan, korkeus seuraa kuvan kuvasuhdetta. Arvot ovat
`src/assets.ts`-tiedoston SPRITE_WORLD_WIDTH-taulukossa.

| Tiedosto | Mitä | Nykyinen koko |
|---|---|---|
| player-straight.png | Mika ja David skootterilla, suoraan | 105x107 |
| player-left.png | sama, kallistus vasemmalle | 105x107 |
| player-right.png | sama, kallistus oikealle | 105x107 |
| car-0.png ... car-5.png | liikenneautot takaa | noin 60x40 |
| palm.png | palmu | 59x109 |
| lamp.png | lyhtypylväs | 35x102 |
| bush.png | pensas | 60x32 |
| gantry.png | opastegantry tien yli | 178x83 |
| billboard-0.png, billboard-1.png | mainostaulut | noin 60x50 |
| logo.png | aloitusruudun logo, piirretään sellaisenaan 1:1 | 280x80 |
| sky.png | taivas, alareuna horisontissa, toistuu vaakasuunnassa (peilattu 768 leveä) | 768x120 |
| skyline.png | kaupungin siluetti, alareuna horisontissa, taivas läpinäkyvä | 768x74 |
| near.png | lähimaisema horisontin edessä, yläosa läpinäkyvä | 768x59 |

Osoitteessa `http://localhost:5173/#sprites` näet kaikki placeholderit ja voit
ladata ne PNG-pohjiksi.
