# Suggestions — the playground list

What's done, what's yours to do, and ideas waiting their turn.
Last updated: 2026-09-25.

---

## ✅ Done

- **Library:** *The Myth of Sisyphus* moved to "Reading now", *Antifragile* to "Finished" (37 volumes).
- **Three voices section** (`/#voices`): Wilde's mirror (hover shows the "reality" side), Camus's boulder (animated, with a push counter), Dostoevsky's underground (read by candlelight).
- **Gallery** is now an exhibition in 11 rooms: Sketchbook · Chitlang · Jhapa · Ilam · Cafés · Robotics · Classroom · Stages (*The Hackathon Herald*) · Portraits · Travel · Moving pictures.
- **Home page:** sketchbook teaser linking into the gallery, plus a Boudha stupa that draws itself as you scroll (under Principles).
- **Performance:** heavy photos and videos compressed (about 100 MB less to download), PNG/HEIC/MOV converted to web formats.
- **Fixes:** touch-scroll "yank" on the gallery room menu; unused photos now hang in the gallery; orphan `explore.html` now redirects to the gallery; `.idea/` untracked.

---

## ✍️ Your part (needs your hand)

1. **Handwritten margin notes:** scan or photograph real notes from your books and place them beside the quotes in `/marginalia/`. Typed text can't fake this one.
2. **Sketch ↔ reality slider:** for any drawing made on location, take two photos:
   - the drawing alone, flat on a table, shot from straight above
   - the same view without the drawing
   
   Send the pair and the slider gets built: drag a handle to wipe between your pencil version and the real scene. The resort drawing is the perfect first candidate if you still have the view photo.
3. **Captions for Travel and Stages:** 40+ frames have generic alt text. A place name or event name per photo is enough ("Rara, 2024", "ICT Award night").
4. **Confirm names:** guest artists are credited as "Nistha" and "Biddya". Add "didi" or surnames if you prefer.
5. **Portraits room:** check that `me05.jpeg` (pencil portrait) belongs there. If it's your drawing, move it to the Sketchbook room.

---

## 💡 Ideas for later

| Idea | Why it fits | Effort |
|---|---|---|
| **Dorian hero:** the home photo slowly shifts to a pencil-sketch look the longer someone stays | Ties the Wilde mirror to *you* | Small |
| **"Play the room":** an optional soft soundscape per gallery room (off by default). `audio/song.mp3` is already in the repo, unused | Makes the gallery feel like a walk | Medium |
| **Studio log:** a tiny "last drawn · last read · last run" line in the footer | The site feels lived-in, not finished | Small |
| **Reading timeline:** books on a timeline by the year you read them, with the marginalia linked | The library becomes a story | Medium |
| **Sketch of the month:** one drawing featured on the home page, rotated monthly | Keeps the art side visible | Small |
| **Dark room mode:** a "lights off" toggle for the gallery (dark walls, warm spotlights on frames) | Exhibition feel at night | Medium |

---

## 🛠 How to add things yourself

**New drawing or photo:** keep the original in `arts/` or `gallery/` (both are git-ignored), then make a web copy:

```bash
convert arts/my_new_art.jpeg -auto-orient -resize '1600x1600>' -strip \
  -interlace Plane -sampling-factor 4:2:0 -quality 80 images/art/my-new-art.jpg
```

Then copy any `<figure class="pin">` block in `gallery/index.html` (Sketchbook room) and change the `src`, the caption and `--r` (tilt).

**New video:**

```bash
ffmpeg -i clip.mov -vf "scale=720:-2" -c:v libx264 -crf 27 -preset slow \
  -pix_fmt yuv420p -c:a aac -b:a 96k -movflags +faststart images/gallery/clip.mp4
```

**New book:**
1. Put the cover (about 320×500) in `images/books/`.
2. Copy a `<figure class="book">` in the `#library` section of `index.html`.
3. Update the volume count in the library intro.

**Keep images under ~400 KB and videos under ~5 MB.** Most visitors are on mobile data.
