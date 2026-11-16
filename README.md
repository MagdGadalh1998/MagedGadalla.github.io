# Maged Gadalla — Unity & XR Portfolio

A dark, responsive, data-driven portfolio designed for GitHub Pages, with a GitHub-backed admin dashboard.

## Architecture
- `index.html` + `css/` + `js/`: public portfolio.
- `data/*.json`: all editable portfolio content.
- `admin/`: browser-based dashboard that reads and writes JSON through the GitHub Contents API.
- `assets/`: images and downloadable documents.

## Publish on GitHub Pages
1. Create a repository named exactly `<your-github-username>.github.io` (recommended for a root URL).
2. Upload the contents of this project to the repository root (not the containing folder).
3. In GitHub: **Settings → Pages → Build and deployment → Deploy from a branch**.
4. Select branch `main`, folder `/ (root)`, then Save.
5. Wait for the Pages URL to become available.

## Connect the admin dashboard
1. Open `https://<your-github-username>.github.io/admin/`.
2. Create a **Fine-grained personal access token** at https://github.com/settings/personal-access-tokens/new.
3. Select only this portfolio repository and grant **Contents: Read and write**. Metadata read access is normally selected automatically.
4. Set an expiration date. Keep the token private.
5. Enter your GitHub username, repository name, branch (`main`), and token in the dashboard.
6. Save edits. The dashboard commits updated JSON files directly to the repository. GitHub Pages deploys the changes shortly afterward.

### Security notes
- The token is entered at runtime; it is not embedded in the website source or committed to Git.
- It is stored in `sessionStorage` for the current browser tab/session and cleared when you sign out or the session ends.
- Use a fine-grained token restricted to this single repository with only Contents read/write. Never paste the token into chat, source files, screenshots, or public repositories.
- Anyone who can access the admin URL can see the login form, but cannot edit without a valid token. Keep the token private and sign out on shared devices.
- For a multi-user production CMS with managed logins, move to a hosted identity/OAuth solution; GitHub Pages itself does not provide server-side authentication.

## Editing content
Use `/admin/` to manage Profile, Experience, Projects, Skills, Education, Certificates, and Site settings. Lists support adding, editing, and deleting entries. Text lists use one item per line or comma-separated values as indicated.

## Add project media / CV
Upload project images to the repository using GitHub’s web interface (no coding required), then enter their relative path in the dashboard:
- CV: `assets/documents/Maged-Gadalla-CV.pdf`
- Project image example: `assets/images/project-name.webp`

## Important content note
Initial content is transcribed from the supplied CV. Project cards are starter descriptions based on the CV, not claims of independently verified shipped products. Replace them with approved project details, screenshots, videos, and public links before publishing.

## Local preview
Because the site fetches JSON files, run a local static server from the project root (for example `python -m http.server 8000`) and visit `http://localhost:8000`. Opening `index.html` directly as a `file://` URL may block JSON fetches.
