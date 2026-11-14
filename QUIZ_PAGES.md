# Quiz pages on inkmotion.art

Each quiz attempt is its own folder in the inkmotion-art repo, with one `index.html` and its image pieces.

| Page | Folder | Heading | Image files |
|------|--------|---------|-------------|
| inkmotion.art/image1, /image2 | `image1`, `image2` | Quiz 2 (original pages, leave alone) | `image.png` etc. |
| inkmotion.art/q3-1/ | `q3-1` | PMP Practice Quiz 3 Attempt 1 | `quiz3-1.webp` ... `quiz3-6.webp` |
| inkmotion.art/q3-2/ | `q3-2` | PMP Practice Quiz 3 Attempt 2 | `quiz3-1.webp` ... `quiz3-6.webp` |
| inkmotion.art/q4-1/ | `q4-1` | PMP Practice Quiz 4 Attempt 1 | `quiz4-1.webp` ... |
| inkmotion.art/q4-2/ | `q4-2` | PMP Practice Quiz 4 Attempt 2 | `quiz4-1.webp` ... |

## To publish a quiz attempt
1. Screenshot the quiz in pieces. Cut between questions, keep every piece the same width (1014 px), and keep each piece under 16,383 px tall (WebP's limit).
2. Save as WebP, named `quiz4-1.webp`, `quiz4-2.webp` ... in order.
3. Open the folder's `index.html` and edit the three lines under "THE ONLY PART YOU EDIT": `TITLE`, `PREFIX`, `PARTS` (the number of pieces).
4. In the GitHub repo, upload `index.html` and the images into the folder (`q4-1`, `q4-2`...).
5. Open the page and scroll through to check order and seams.

## New quiz (Quiz 5, etc.)
Copy `quiz-template/index.html` into a new folder (for example `q5-1`) and edit the same three lines.

Why separate pieces: one giant image can't be WebP (16,383 px limit) and is too heavy for phones. Stacked pieces scroll like one image.
