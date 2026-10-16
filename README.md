# MapSaber

**An AI that makes Beat Saber maps for the songs you love that nobody has mapped yet.**

You bring a song, MapSaber listens to it and writes a map you can play. Everything runs on your
own PC.

> **Status: in development, not released yet.** There is nothing to download here so far.
> This page explains what MapSaber is and how it's being built. Code and releases will come when
> it's ready to share.

---

## What it does

- **Maps any song you own** (mp3, ogg, wav, flac) into Expert and Expert+ charts.
- **Lets you pick a style:** Speed, Mid-Speed, Acc, Tech, or Auto (it decides from the music).
- **Lets you aim for a density** in notes per second, with an optional hard lock, so a calm song
  can stay calm and a fast one can go fast without turning into jumble.
- **Can make named charts.** One song can get several styles (for example Speed, Tech and
  Mid-Speed), sorted into the difficulty slots from hardest to easiest.
- **Lets you set the song name, cover image and mapper credit,** and puts the map straight into
  your game.

## How it works

MapSaber is a transformer model that listens to about 16 seconds of music at a time, as a
spectrogram, and writes notes the way a mapper does: when, which hand, where, and which cut
direction. Because it hears a whole stretch of music at once, it can leave pauses where the song
breathes and add bursts where it picks up.

A few things around the model keep maps playable:

- **Beat grid:** notes are snapped to the song's tempo, and the tempo is checked against the notes
  themselves.
- **Flow:** while it writes, each hand's swings are kept in parity, so it doesn't ask for
  backwards swings.
- **Picking the best try:** each section is generated a few times, and the cleanest version is
  kept.

On 12 test songs it had never seen, about 83% of the notes MapSaber placed landed on the same beats
a human mapper chose.

## Honest limitations

- **Notes only for now.** No bombs, walls or lightshows yet.
- **Expert and Expert+ only** so far.
- **It still makes mistakes.** It sometimes gets a song's BPM wrong, and it has more resets than a
  well-made human map.
- **It isn't a replacement for human mappers.** A great human map has intent and care that an AI
  doesn't. MapSaber is for songs that would otherwise have no map at all.

## Where it learned, and respect for mappers

MapSaber learned from publicly available, **human-made** maps on
[BeatSaver](https://beatsaver.com): ranked and curated maps by around a thousand mappers. AI-made
maps were left out. The training maps and songs stay private and are never redistributed. Only
the tool will be shared, and people use it with their own songs.

MapSaber only exists because of the work of the mapping community, so thank you. If you're a mapper
and you'd prefer your maps not be used in future training, open an issue and they'll be left out.

## If you share a MapSaber map

- **Mark it as AI-generated** when you upload it. BeatSaver's rules require that, and it's the
  honest thing to do.
- **Don't submit AI maps for ranking.**
- **Give it a playtest first.** You know what feels good to play better than any AI does.

## A personal project

MapSaber is a personal project, made in my spare time because I wanted to play the songs I like.
**There are no promises of fixes, updates or release dates.** Issues and ideas are welcome, but I
may not get to them, and things can change or stop at any time.

## Plans

These are hopes, not promises:

- Free to use.
- An easy app, so you don't need a terminal.
- Bombs, walls, lower difficulties, and fewer resets.

## Credits

- The model's recipe follows [Mapperatorinator](https://github.com/OliBomby/Mapperatorinator)
  by OliBomby (MIT), the osu! AI mapper that showed this approach works.
- The maps it learned from come from the BeatSaver community, with ranking by the ScoreSaber and
  BeatLeader teams and curation by BeatSaver's curators.
- Made by critz.

*MapSaber is a fan project. It is not affiliated with or endorsed by Beat Games, Meta, BeatSaver,
ScoreSaber or BeatLeader. Beat Saber is a trademark of Beat Games.*
