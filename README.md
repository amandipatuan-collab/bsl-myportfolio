## Project Description

Personal portfolio landing page for CCC181 (Application Development and Emerging Tech),
exploring modern serverless web delivery over traditional hosting,
I'm serving it through the **Bonezegei Scripting Language
(BSL) v1.3.3** HTTP framework, which is the whole point of the exercise.

The server side is a single file — `app.bzg` — that listens on port 8000. When
someone visits `/`, it reads `public/index.html` off disk and sends it back to the
browser; any other path falls through to `public/404.html`. All of that routing
happens inside a few lines of the `server.get` handler, which I liked: the entire
HTTP layer is small enough to read top to bottom and actually understand.

The page itself is intentionally plain HTML and CSS — no framework, no build step,
no JavaScript. For a portfolio about working close to the metal, a page with nothing
hiding between it and the browser felt like the right call.

**Tech stack**

- **Server** — Bonezegei Scripting Language (BSL) v1.3.3
- **Front end** — HTML5, CSS3
- **Editor** — Visual Studio Code with the Bonezegei Formatter extension
- **Version control** — Git / GitHub

## Setup & Execution Steps

**Prerequisites:** Bonezegei Scripting Language v1.3.3 and the Bonezegei VS Code
extension. Confirm the install before anything else:

```bash
bonezegei -v
# expected: v1.3.3
```

**1. Clone the repository**

```bash
git clone https://github.com/Mahather11/bsl-myportfolio.git
cd bsl-myportfolio
```

**2. Open the project folder in VS Code**

Use *File → Open Folder* and select the folder that directly contains `app.bzg` and
`package.json`. This matters more than it sounds: the integrated terminal (`Ctrl + \``)
inherits whatever folder you opened, and `bzg install` will fail with
`package.json not found in current directory` if you happen to be sitting in a parent
folder instead. If you see `app.bzg` when you list the directory, you're in the right
place.

**3. Install dependencies**

```bash
bzg install
```

This step is required, not optional. `app.bzg` begins with `include("lib/http.bzg")`,
but the `lib/` folder isn't checked into the repository — `bzg install` is what
downloads it. Skipping it means the server can't start.

**4. Start the web server**

```bash
bzg run
```

There's no startup banner; the process simply begins listening on port 8000. Each
time a page is requested it prints a line like:

```
get loc:/
```

Leave that terminal open — closing it stops the server.

**5. View the page**

Open a browser and go to:

```
http://localhost:8000
```

