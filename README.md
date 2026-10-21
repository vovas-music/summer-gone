# Лето прошло (Summer Is Gone)

Track 2 of 7 on «Ностальгия» (_Nostalgiya_, “Nostalgia”), the album by Полуживые (_Poluzhivye_), on poems by Arseny Tarkovsky. Track 1, «Приглашение в путешествие», runs into it; it lives in `vovas-music/nostalgia`.

On the site: https://vovazakharov.com/music/summer-gone

## Files

- `summer-gone_mix.mp3` — the mix, unmastered, cut from the album file at 68.24 s.
- `summer-gone.mp3` — the master, cut at the same point (V0).
- `mastering/` — the script that made the master: `master.py`, the `spectrum.py` it imports, and their `requirements.txt`.

## How it was mastered

```sh
pip install -r mastering/requirements.txt
curl -LO https://github.com/vzakharov/vovazakharov.com/releases/download/music-sources/nostalgia-01-02-invitation-summer-gone.mp3
python mastering/master.py nostalgia-01-02-invitation-summer-gone.mp3 ref.flac invitation-summer-gone.flac
ffmpeg -i invitation-summer-gone.flac -ss 68.24 -c:a libmp3lame -q:a 0 summer-gone.mp3
```

Tracks 1 and 2 are one piece of music — the recitative of track 1 is laid over the
ambient opening of track 2 — so they were mastered as one file, the album's
first 311 s, and cut at the guitar's first onset, 68.24 s in. Mastered apart,
each half would get its own gain and EQ and the segue would jump.

with `ffmpeg` on `PATH` and the reference below saved as `ref.flac`. Half
strength (`master.py`'s default): Matchering matches the mix to the reference,
half of the EQ difference goes onto the mix, and a limiter keeps the decoded
file under -1 dBTP. `master.py`'s docstring has the whole chain.

## The reference

«Каприс Каркасси» (_Kapris Karkassi_, “Carcassi Caprice”), Полуживые, from «Папа-море», at [vovas-music/caprice@38f145e](https://github.com/vovas-music/caprice/blob/38f145ed2c10378c013d4f60d12396214291f754/Poluzhivye%20-%20Kapris%20Karkassi.flac) — raw download:
https://raw.githubusercontent.com/vovas-music/caprice/38f145ed2c10378c013d4f60d12396214291f754/Poluzhivye%20-%20Kapris%20Karkassi.flac

It was picked blind: three catalogue masters each mastered the mix, and the
operator ranked them unlabelled, loudness-matched, before learning which was
which. It is linked rather than copied here, since it already lives in this
organization.
