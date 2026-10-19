# Portfolio site

A four-page portfolio built from `CV_DataScientist_v4 (1).docx` and the notebooks in
[Data-Analysis](https://github.com/WondosenAm/Data-Analysis) and
[Machine-Learning](https://github.com/WondosenAm/Machine-Learning), plus the
[CVSLR](https://github.com/WondosenAm/CVSLR) sign language app and its training notebook. The layout follows the
AcademicPages style: a top menu, a profile sidebar and one column of plain text.
It is plain HTML and CSS, so there is no build step and nothing to install.

| File | Purpose |
| --- | --- |
| `index.html` | About: at-a-glance summary, short bio, featured projects |
| `projects.html` | Data science projects with code, then work projects |
| `cv.html` | Full CV with a print button |
| `contact.html` | Email, LinkedIn, GitHub and location |
| `styles.css` | Layout, light and dark themes, print styles |
| `favicon.svg` | Browser tab icon |
| `sitemap.xml`, `robots.txt` | Help search engines find the four pages |
| `404.html` | Not-found page served by GitHub Pages |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are, without Jekyll |
| `.gitignore` | Keeps the source `.docx` CV out of the public repository |

The header and sidebar are repeated in each of the four HTML files. If you change one,
change all four.

## Before publishing: fill in the placeholders

The CV is a template, so several details were not available. They appear on the pages
highlighted in yellow (class `todo`). Replace each one, then remove the `<span class="todo">`
wrapper around it. Find-and-replace across all files works well for these.

| Placeholder | Where |
| --- | --- |
| `[FULL NAME]` | Page titles, meta tags, header, sidebar, footer, photo alt text |
| `name@email.com` | Email links in the sidebar and the contact section |
| `your-handle` | LinkedIn links |
| `[City, Country]` | Sidebar and CV |
| `[ORGANIZATION NAME]`, `[COMPANY NAME]`, `[BANK NAME]` | CV |
| `[Information Network Logic]` | About page and CV. Bracketed in the CV, so confirm the name |
| `[UNIVERSITY NAME]` | CV, BSc entry |
| `Universiti Malaya` | CV, MSc entry. Inferred from your GitHub projects, so confirm it |
| `[Describe your role in the group]` | Projects page, sign language project |
| Profile photo | Optional. Save as `images/profile.jpg` and uncomment the `<img>` in each page |

To find anything left over:

```bash
grep -nE '\[|todo|your-handle|name@email' *.html
```

## Preview locally

Open `index.html` in a browser, or serve the folder so the 404 page works too:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Publish on GitHub Pages

The pages assume the site lives at `https://wondosenam.github.io/`, the address for the
GitHub account `WondosenAm`. If you publish from another account, replace that address
in the `canonical` and `og:url` tags of each page, the structured data in `index.html`,
`sitemap.xml` and `robots.txt`.

1. Create a public repository named exactly `WondosenAm.github.io`.
2. Push these files to the `main` branch:

   ```bash
   git init
   git add .
   git commit -m "Add portfolio site"
   git branch -M main
   git remote add origin https://github.com/WondosenAm/WondosenAm.github.io.git
   git push -u origin main
   ```

3. On GitHub, open **Settings → Pages**. Under **Build and deployment**, set
   **Source** to *Deploy from a branch*, then pick `main` and `/ (root)`.
4. After a minute or two the site is live at `https://wondosenam.github.io/`.

If you use a different repository name, the site is served from
`https://wondosenam.github.io/REPO/`. The main page still works, but change the
absolute paths in `404.html` to start with `/REPO/`
and update the canonical URLs.

## Adding a project

Copy one `<article class="project">` block in `projects.html` and give it a new `id`.
Keep the same four labels: The question, Data, What I did, Result. Then add a line
for it in the project index at the top of `projects.html`, and in the project list
in `cv.html`. Add it to the featured list in `index.html` only if it is one of your best.

## Printing

The CV page has print styles. Printing it, or saving it as PDF from the browser, gives a clean
single-column document without the menu.
