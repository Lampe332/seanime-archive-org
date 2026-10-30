<div align="center">

<img src="icon.png" width="96" alt="Internet Archive logo">

# Internet Archive for Seanime

Find anime uploads on [archive.org](https://archive.org) and download or stream them as torrents in [Seanime](https://github.com/5rahim/seanime).

![type](https://img.shields.io/badge/Seanime-anime%20torrent%20provider-6d28d9)
![version](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2FLampe332%2Fseanime-archive-org%2Fmain%2Fmanifest.json&query=%24.version&label=version&color=6d28d9)
![seeding](https://img.shields.io/badge/seeded%20by-archive.org-555)
![languages](https://img.shields.io/badge/languages-whatever%20people%20uploaded-555)

</div>

## Install

In Seanime go to **Extensions** → **Add extension**, paste this URL and confirm:

```
https://raw.githubusercontent.com/Lampe332/seanime-archive-org/main/manifest.json
```

Open any anime, hit **Download** (or use torrent streaming) and pick **Internet Archive** from the provider dropdown. Updates come through the same URL, so later on a click on **Check for updates** is enough.

## Why archive.org

archive.org has a torrent for every item and seeds all of them itself over plain HTTP (a web seed). The magnet links this extension hands to Seanime carry the `.torrent` URL and the web seed, so a download starts even when nobody else is seeding. That's also why every result shows exactly 1 seeder: archive.org is always there, and the site doesn't report anyone else.

What's on there is whatever people uploaded: fansub batches, BD rips, old TV recordings, Latin American and Brazilian dubs, Hindi and Turkish broadcasts, DiC-era English dubs. Quality and language are all over the place, so read the title before you pick something.

## Filtering

Searching archive.org for an anime title mostly turns up things that aren't the anime: AMVs, reviews, reaction videos, YouTube and TikTok mirrors, cosplay, openings, music videos, manga scans, game footage, live-action films. Smart search throws those out and keeps an upload only if

- its title starts with the anime's name (after group tags like `[DB]`), so *Boruto: Naruto Next Generations* doesn't land under *Naruto*,
- whatever follows the name is a release word (episode, season, dub, 1080p, Latino, ...) and not a different subtitle, so *Death Note: New Generation* and *Kimetsu no Yaiba Yuukaku-hen* stay out of the first season,
- any season it names fits the AniList entry. Season numbers come from [ani.zip](https://api.ani.zip) (TVDB), and the parser reads "Season 2", "2nd Season", "S02", "S01&02", "Temporada 3" and Turkish "3. Sezon",
- any year in the title fits the anime, which keeps remakes and live-action films apart,
- the name isn't shared with a related anime. A bare "Fullmetal Alchemist" upload could be 2003 or *Brotherhood*, so it needs a season or year to count. The related titles come from AniList.

Searching for an episode returns single-episode uploads. Season packs only show up when archive.org has no single upload of that episode, or when you turn on **Batches**.

## Tested

All runs went through Seanime's extension playground and its real torrent search.

- 25 well-known titles, checked by hand: Cowboy Bebop, Death Note, Frieren, Naruto and Shippuden, Attack on Titan S1/S2, One Piece, FMA: Brotherhood, Demon Slayer S1 and Entertainment District, Solo Leveling S1/S2, Evangelion, DBZ, Spirited Away, Your Name, Mob Psycho 100, Jujutsu Kaisen, Hunter x Hunter 2011, Bocchi the Rock!, SPY x FAMILY, Chainsaw Man, Dandadan and Sailor Moon.
- The info hash from the search API matched the real `.torrent` file 16 out of 16 times.
- Magnets were opened with the same torrent library Seanime uses. Single episodes downloaded over the web seed within a few seconds, with no other peers around.

## Known gaps

- Many uploads have no clean title. Something called "Cowboy Bebop" could be the whole series or one episode, and those count as batches.
- Uploads that only carry a short name shared with another anime ("Fullmetal Alchemist" without a year) are left out on purpose.
- The *Evangelion* Rebuild films ("1.0", "2.22", "3.33") still show up as packs under the TV series.
- Archive.org's search can be slow, and Seanime may take a few seconds to show results.

## Notes

The extension only uses archive.org's public search and download URLs and hosts nothing. Please keep in mind that what you download is whatever someone uploaded there.
