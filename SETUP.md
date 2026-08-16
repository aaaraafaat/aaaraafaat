# Setup and maintenance notes

This file is for you, not for visitors. Delete it before pushing if you would rather it not be public, or keep it — nobody reads a SETUP.md on a profile repo.

---

## 1. What this repo is

This is your **GitHub profile repository**. For the README to appear on your profile page at `github.com/aaaraafaat`, the repository must be named **exactly the same as your username**:

```
Repository name:  aaaraafaat
Visibility:       Public
Initialise with:  nothing (this repo already has the files)
```

If the name does not match the username exactly, the README will not render on your profile. That is the single most common way this goes wrong.

---

## 2. Pushing it

From the folder containing this file:

```bash
git init
git add .
git commit -m "Profile README"
git branch -M main
git remote add origin https://github.com/aaaraafaat/aaaraafaat.git
git push -u origin main
```

If the repo already exists with content, use `git push -u origin main --force` — but only if you are certain you are not overwriting something you want.

---

## 3. Replacing the placeholder images

Eight placeholders are in `images/`. Each one names what belongs there and states the target size.

| File | Shows |
|---|---|
| `pcatd-01.png` | PC-based training device, exterior |
| `pcatd-02.png` | PC-based training device, cockpit interior |
| `vr-01.png` | VR combat simulator rig |
| `vr-02.png` | VR combat simulator in use |
| `ops-01.png` | Flying operations app — daily schedule builder |
| `ops-02.png` | Flying operations app — trainee progress monitor |
| `ops-03.png` | Flying operations app — syllabus and sortie tracking |
| `mission-planner.png` | Flight planning tool output |

**Keep the filenames identical.** Drop your image in, keep the name, and the README needs no edit at all.

### Target specification

- **1200 × 750 pixels.** This is 16:10, and it is what the placeholders are, so every card in a row stays the same height. Mixed aspect ratios are the thing that makes a README look untidy.
- **Under 250 KB each.** Your current files are camera originals at several megabytes. GitHub serves them at full size and the page crawls on a slow connection — which is exactly the connection a professor in Europe will not be on, but a reviewer on a train will.
- **Screenshots → PNG. Photographs → JPEG, quality 80.** PNG on a photograph is what makes a 4 MB file.

### Resizing

ImageMagick, one command per file:

```bash
# photographs
magick input.JPG -resize 1200x750^ -gravity center -extent 1200x750 -quality 80 images/pcatd-01.jpg

# screenshots
magick input.png -resize 1200x750^ -gravity center -extent 1200x750 -strip images/ops-01.png
```

The `^` and `-extent` pair crops to fill rather than squashing. If you change a file's extension from `.png` to `.jpg`, update the matching `<img src="...">` line in the README.

Or use squoosh.app in a browser if you would rather not install anything.

---

## 4. Two things in the README that still need you

**The thesis repository link.** Line reads:

```
https://github.com/aaaraafaat/PLACEHOLDER-THESIS-REPO
```

Create the repo, then replace that string. Suggested name: `perception-difficulty-dve`. What that repo needs, in order of how much it matters:

1. The feature-extraction script that actually runs
2. The data-cleaning pipeline
3. Three or four figures — cue distributions, the failure case, the night-subset inversion
4. A README stating the method, the dataset, and how to reproduce a single result

It does not need to be finished. It needs to exist. A reviewer forms a judgement about whether you write code within about forty seconds of landing there, and an empty profile answers that question badly.

**The quantitative result.** There is an HTML comment in the Research section marking where it goes. One number — a correlation, an effect size, the size of the night-subset failure. Right now every line says what the method does and none says what you found. Delete the comment once the number is in.

---

## 5. The CV

`cv/Arafat_CV_Academic_2026.pdf` is linked from the README. Replace that file whenever the CV changes and the link keeps working.

---

## 6. Before you make the images public

Your own standing rule: Air Force project media requires frame-by-frame vetting before anything goes public. That applies to the simulator, VR and mission-planner images and not to thesis figures. You have said you want professors to see them, which is the right call — but check each frame for unit markings, serial numbers, screen content and anything visible through a window before it goes up. Once it is on a public repo it is in someone's cache.
