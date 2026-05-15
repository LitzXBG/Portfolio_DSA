# Portfolio Page — Step by Step Build Instructions

### Using Plain HTML + Tailwind CSS (No Framework)

---

## Setup

### What We'll Build

A single page portfolio with:

- A navbar
- A hero section (name + tagline + button)
- A projects section (responsive grid of cards)
- A skills section (grouped tag cloud)
- An achievements section (vertical timeline)
- A contact section
- A footer

### Project Structure

```
portfolio/
  index.html
```

Just one file.

---

### Base HTML — Tailwind via CDN

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My Portfolio</title>

    <!-- Google Fonts -->
    <link
      href="https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Inter:wght@400;500&display=swap"
      rel="stylesheet"
    />

    <!-- Tailwind CDN -->
    <script src="https://cdn.tailwindcss.com"></script>

    <!-- Tailwind Config — fonts + accent color -->
    <script>
      tailwind.config = {
        theme: {
          extend: {
            fontFamily: {
              display: ["Syne", "sans-serif"],
              body: ["Inter", "sans-serif"],
            },
            colors: {
              accent: "#6EE7B7",
            },
          },
        },
      };
    </script>
  </head>

  <body class="bg-gray-950 text-white font-body">
    <!-- Ambient Glow -->
    <div class="fixed inset-0 pointer-events-none">
      <div
        class="absolute top-0 left-1/4 w-96 h-96 bg-accent opacity-5 rounded-full blur-3xl"
      ></div>
      <div
        class="absolute bottom-1/4 right-1/4 w-72 h-72 bg-blue-500 opacity-5 rounded-full blur-3xl"
      ></div>
    </div>

    <!-- sections go here -->
  </body>
</html>
```

---

## Section 1 — Navbar

### Step 1 — Raw HTML, no styling

Start with just the content. No classes yet.

```html
<nav>
  <span>Arjun S.</span>
  <ul>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#achievements">Achievements</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>
```

> Why `ul` and `li`? Because a navbar is semantically a list of links. Screen readers and search engines understand this.

---

### Step 2 — Make the navbar a horizontal row

Add `flex` and `justify-between` to the `<nav>`:

```html
<nav class="flex justify-between"></nav>
```

- `flex` — makes children (span and ul) sit side by side
- `justify-between` — pushes logo to the left, ul to the right

---

### Step 3 — Make the nav links horizontal

Add `flex` to the `<ul>`:

```html
<ul class="flex"></ul>
```

---

### Step 4 — Add spacing between links

```html
<ul class="flex gap-6"></ul>
```

- `gap-6` — adds 24px of space between each `<li>` item

---

### Step 5 — Add padding to the navbar

```html
<nav class="flex justify-between px-8 py-4"></nav>
```

- `px-8` — 32px padding left and right
- `py-4` — 16px padding top and bottom

---

### Step 6 — Add background and shadow

```html
<nav class="flex justify-between px-8 py-4 bg-gray-950 shadow-sm"></nav>
```

- `bg-gray-950` — dark background
- `shadow-sm` — subtle drop shadow

---

### Step 7 — Style the logo text

```html
<span class="text-xl font-bold font-display">Arjun S.</span>
```

- `text-xl` — larger font size
- `font-bold` — heavy weight
- `font-display` — uses the Syne display font from our config

---

### Step 8 — Style the nav links

```html
<ul class="flex gap-6 text-sm text-gray-400">
  <li>
    <a href="#projects" class="hover:text-white transition-colors">Projects</a>
  </li>
  <li>
    <a href="#skills" class="hover:text-white transition-colors">Skills</a>
  </li>
  <li>
    <a href="#achievements" class="hover:text-white transition-colors"
      >Achievements</a
    >
  </li>
  <li>
    <a href="#contact" class="hover:text-white transition-colors">Contact</a>
  </li>
</ul>
```

- `text-sm` — slightly smaller than body text
- `text-gray-400` — muted color
- `hover:text-white` — brightens on hover
- `transition-colors` — smooth color animation

---

### Step 9 — Vertically center logo and links

```html
<nav
  class="flex justify-between items-center px-8 py-4 bg-gray-950 shadow-sm"
></nav>
```

- `items-center` — vertically centers all flex children

---

### Final Navbar

```html
<nav class="flex justify-between items-center px-8 py-4 bg-gray-950 shadow-sm">
  <span class="text-xl font-bold font-display">Arjun S.</span>

  <ul class="flex gap-6 text-sm text-gray-400">
    <li>
      <a href="#projects" class="hover:text-white transition-colors"
        >Projects</a
      >
    </li>
    <li>
      <a href="#skills" class="hover:text-white transition-colors">Skills</a>
    </li>
    <li>
      <a href="#achievements" class="hover:text-white transition-colors"
        >Achievements</a
      >
    </li>
    <li>
      <a href="#contact" class="hover:text-white transition-colors">Contact</a>
    </li>
  </ul>
</nav>
```

---

## Section 2 — Hero

### Step 1 — Raw HTML, no styling

```html
<section>
  <p>Full Stack Developer</p>
  <h1>Building things that matter.</h1>
  <p>
    I'm Arjun — a high schooler who builds real web apps, experiments with AI,
    and ships things.
  </p>
  <a href="#projects">See My Projects</a>
</section>
```

> `<h1>` — there should be exactly one h1 per page, and it lives in the hero.

---

### Step 2 — Constrain width and add padding

```html
<section class="max-w-5xl mx-auto py-32 px-6"></section>
```

- `max-w-5xl` — limits width
- `mx-auto` — centers the section
- `py-32` — generous vertical padding (128px) — hero needs to feel spacious
- `px-6` — side padding for mobile safety

---

### Step 3 — Style the eyebrow label

```html
<p class="text-accent text-sm font-medium tracking-widest uppercase mb-4">
  Full Stack Developer
</p>
```

- `text-accent` — uses our config accent color
- `uppercase tracking-widest` — eyebrow label style, sophisticated and readable
- `mb-4` — 16px below before the heading

---

### Step 4 — Style the h1

```html
<h1 class="font-display text-7xl md:text-8xl font-bold leading-none mb-6">
  Building<br />things that<br /><span class="text-accent">matter.</span>
</h1>
```

- `font-display` — uses the Syne display font
- `text-7xl md:text-8xl` — massive on desktop, slightly smaller on mobile
- `leading-none` — tight line height on big text looks designed, not accidental
- `<span class="text-accent">` — accent color on one word for punch
- `mb-6` — 24px below heading

---

### Step 5 — Style the tagline

```html
<p class="text-gray-400 text-xl max-w-lg mb-10">
  I'm Arjun — a high schooler who builds real web apps, experiments with AI, and
  ships things.
</p>
```

- `text-gray-400` — muted, secondary to the heading
- `text-xl` — readable, not competing with the h1
- `max-w-lg` — constrains the paragraph width for readability
- `mb-10` — 40px before the button

---

### Step 6 — Style the button

```html
<a
  href="#projects"
  class="inline-block bg-accent text-gray-950 px-8 py-4 rounded-full font-semibold hover:opacity-90 transition-opacity"
>
  See My Projects
</a>
```

- `inline-block` — lets padding and sizing work correctly
- `bg-accent text-gray-950` — accent background, dark text for contrast
- `px-8 py-4` — generous padding inside the button
- `rounded-full` — pill shape
- `font-semibold` — medium-heavy weight
- `hover:opacity-90 transition-opacity` — subtle fade on hover

---

### Final Hero Section

```html
<section class="max-w-5xl mx-auto py-32 px-6">
  <p class="text-accent text-sm font-medium tracking-widest uppercase mb-4">
    Full Stack Developer
  </p>

  <h1 class="font-display text-7xl md:text-8xl font-bold leading-none mb-6">
    Building<br />things that<br /><span class="text-accent">matter.</span>
  </h1>

  <p class="text-gray-400 text-xl max-w-lg mb-10">
    I'm Arjun — a high schooler who builds real web apps, experiments with AI,
    and ships things.
  </p>

  <a
    href="#projects"
    class="inline-block bg-accent text-gray-950 px-8 py-4 rounded-full font-semibold hover:opacity-90 transition-opacity"
  >
    See My Projects
  </a>
</section>
```

---

## Section 3 — Projects

### Step 1 — Raw HTML, no styling

```html
<section id="projects">
  <h2>Projects</h2>

  <div>
    <div>
      <div>🌦️</div>
      <h3>Weather App</h3>
      <p>
        Fetches real-time weather using an API. Built with HTML, CSS and
        JavaScript.
      </p>
      <a href="#">View Project</a>
    </div>

    <div>
      <div>📝</div>
      <h3>To-Do List</h3>
      <p>A clean task manager with local storage. First JavaScript project.</p>
      <a href="#">View Project</a>
    </div>

    <div>
      <div>🤖</div>
      <h3>Chatbot</h3>
      <p>A simple chatbot built using Python and basic NLP concepts.</p>
      <a href="#">View Project</a>
    </div>
  </div>
</section>
```

> Structure: one `<section>` wrapper, one `<h2>`, one grid container `<div>`, three card `<div>` blocks.

---

### Step 2 — Section background and padding

```html
<section id="projects" class="bg-gray-900 py-16 px-6"></section>
```

- `bg-gray-900` — slightly lighter than the body (gray-950), creates contrast
- `py-16` — 64px top and bottom
- `px-6` — side padding

---

### Step 3 — Constrain and center inner content

```html
<section id="projects" class="bg-gray-900 py-16 px-6">
  <div class="max-w-5xl mx-auto">...</div>
</section>
```

> The two-layer pattern: `<section>` handles background + outer padding. Inner `<div>` handles max-width + centering. This repeats in every section.

---

### Step 4 — Style the section heading

```html
<h2 class="text-3xl font-display font-bold text-center mb-10">Projects</h2>
```

- `text-3xl` — 30px, prominent but smaller than the h1 (hierarchy preserved)
- `text-center` — centered above the grid
- `mb-10` — 40px below before the cards

---

### Step 5 — Make the card container a responsive grid

```html
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6"></div>
```

- `grid` — turns this div into a CSS grid container
- `grid-cols-1` — one column on mobile (cards stack)
- `md:grid-cols-2` — two columns on tablet (≥768px)
- `lg:grid-cols-3` — three columns on desktop (≥1024px)
- `gap-6` — 24px gap between every card

> Resize the browser window after adding this — cards reflow live.

---

### Step 6 — Add gradient border card wrapper

```html
<div
  class="relative p-px rounded-2xl bg-gradient-to-br from-gray-700 to-gray-900"
>
  <div class="bg-gray-900 rounded-2xl p-6 h-full flex flex-col">
    <!-- card content -->
  </div>
</div>
```

- Outer div has a gradient — this becomes the "border"
- `p-px` — 1px padding, just enough to show the gradient
- Inner div fills the card with background color
- `h-full` — makes inner div fill the outer div completely
- `flex flex-col` — sets up vertical layout for the card content

---

### Step 7 — Style the icon

```html
<div class="text-4xl mb-4">🌦️</div>
```

- `text-4xl` — makes the emoji large, acts as a visual anchor
- `mb-4` — 16px space below before the title

---

### Step 8 — Style the card title

```html
<h3 class="font-semibold text-lg mb-2">Weather App</h3>
```

- `font-semibold` — not as heavy as bold, appropriate for a card title
- `text-lg` — 18px
- `mb-2` — 8px below, description is closely related

---

### Step 9 — Style the description

```html
<p class="text-gray-400 text-sm mb-4 flex-grow">
  Fetches real-time weather using an API. Built with HTML, CSS and JavaScript.
</p>
```

- `text-gray-400` — muted, secondary information
- `text-sm` — 14px
- `flex-grow` — expands to fill available space, pushing the link to the bottom

---

### Step 10 — Style the link

```html
<a
  href="#"
  class="text-sm font-medium text-accent hover:opacity-70 transition-opacity"
>
  View Project →
</a>
```

---

### Step 11 — Add hover effect to the card

```html
<div
  class="bg-gray-900 rounded-2xl p-6 h-full flex flex-col hover:shadow-lg transition-shadow"
></div>
```

- `hover:shadow-lg` — card lifts on hover
- `transition-shadow` — animates smoothly

---

### Final Projects Section

```html
<section id="projects" class="bg-gray-900 py-16 px-6">
  <div class="max-w-5xl mx-auto">
    <h2 class="text-3xl font-display font-bold text-center mb-10">Projects</h2>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <!-- Card 1 -->
      <div
        class="relative p-px rounded-2xl bg-gradient-to-br from-gray-700 to-gray-900"
      >
        <div
          class="bg-gray-900 rounded-2xl p-6 h-full flex flex-col hover:shadow-lg transition-shadow"
        >
          <div class="text-4xl mb-4">🌦️</div>
          <h3 class="font-semibold text-lg mb-2">Weather App</h3>
          <p class="text-gray-400 text-sm mb-4 flex-grow">
            Fetches real-time weather using an API. Built with HTML, CSS and
            JavaScript.
          </p>
          <a
            href="#"
            class="text-sm font-medium text-accent hover:opacity-70 transition-opacity"
          >
            View Project →
          </a>
        </div>
      </div>

      <!-- Card 2 -->
      <div
        class="relative p-px rounded-2xl bg-gradient-to-br from-gray-700 to-gray-900"
      >
        <div
          class="bg-gray-900 rounded-2xl p-6 h-full flex flex-col hover:shadow-lg transition-shadow"
        >
          <div class="text-4xl mb-4">📝</div>
          <h3 class="font-semibold text-lg mb-2">To-Do List</h3>
          <p class="text-gray-400 text-sm mb-4 flex-grow">
            A clean task manager with local storage. First JavaScript project.
          </p>
          <a
            href="#"
            class="text-sm font-medium text-accent hover:opacity-70 transition-opacity"
          >
            View Project →
          </a>
        </div>
      </div>

      <!-- Card 3 -->
      <div
        class="relative p-px rounded-2xl bg-gradient-to-br from-gray-700 to-gray-900"
      >
        <div
          class="bg-gray-900 rounded-2xl p-6 h-full flex flex-col hover:shadow-lg transition-shadow"
        >
          <div class="text-4xl mb-4">🤖</div>
          <h3 class="font-semibold text-lg mb-2">Chatbot</h3>
          <p class="text-gray-400 text-sm mb-4 flex-grow">
            A simple chatbot built using Python and basic NLP concepts.
          </p>
          <a
            href="#"
            class="text-sm font-medium text-accent hover:opacity-70 transition-opacity"
          >
            View Project →
          </a>
        </div>
      </div>
    </div>
  </div>
</section>
```

---

## Section 4 — Skills

### Step 1 — Raw HTML, no styling

```html
<section id="skills">
  <h2>Skills</h2>

  <div>
    <div>
      <h3>Languages</h3>
      <div>
        <span>Python</span>
        <span>JavaScript</span>
        <span>HTML</span>
        <span>CSS</span>
      </div>
    </div>

    <div>
      <h3>Tools</h3>
      <div>
        <span>Git</span>
        <span>VS Code</span>
        <span>Figma</span>
      </div>
    </div>

    <div>
      <h3>Platforms</h3>
      <div>
        <span>GitHub</span>
        <span>Vercel</span>
        <span>Replit</span>
      </div>
    </div>
  </div>
</section>
```

---

### Step 2 — Section background and padding

```html
<section id="skills" class="bg-gray-950 py-16 px-6"></section>
```

Alternates back to gray-950, creating contrast with the gray-900 projects section.

---

### Step 3 — Constrain and center inner content

```html
<section id="skills" class="bg-gray-950 py-16 px-6">
  <div class="max-w-5xl mx-auto">...</div>
</section>
```

---

### Step 4 — Style the section heading

```html
<h2 class="text-3xl font-display font-bold text-center mb-10">Skills</h2>
```

---

### Step 5 — Make groups sit side by side

```html
<div class="grid grid-cols-1 md:grid-cols-3 gap-10"></div>
```

- `grid-cols-1` — stacked on mobile
- `md:grid-cols-3` — three columns on tablet and above
- `gap-10` — generous space between groups

---

### Step 6 — Style each group heading

```html
<h3 class="text-sm font-medium text-gray-400 uppercase tracking-widest mb-4">
  Languages
</h3>
```

- `text-sm uppercase tracking-widest` — eyebrow label style
- `text-gray-400` — muted, it's a label not a heading
- `mb-4` — space before the tags

---

### Step 7 — Make tags wrap and flow

```html
<div class="flex flex-wrap gap-2"></div>
```

- `flex flex-wrap` — tags sit inline but wrap to next line if they overflow
- `gap-2` — 8px between tags

---

### Step 8 — Style each tag

```html
<span
  class="px-4 py-2 rounded-full border border-gray-700 text-gray-300 text-sm"
>
  Python
</span>
```

- `px-4 py-2` — padding inside the pill
- `rounded-full` — pill shape
- `border border-gray-700` — subtle border defines the tag
- `text-gray-300 text-sm` — readable but not loud

---

### Step 9 — Add hover state to tags

```html
<span
  class="px-4 py-2 rounded-full border border-gray-700 text-gray-300 text-sm hover:border-accent hover:text-accent transition-colors cursor-default"
>
  Python
</span>
```

- `hover:border-accent hover:text-accent` — tag lights up in accent color on hover
- `transition-colors` — smooth animation
- `cursor-default` — tags aren't links, keep the cursor as an arrow

---

### Final Skills Section

```html
<section id="skills" class="bg-gray-950 py-16 px-6">
  <div class="max-w-5xl mx-auto">
    <h2 class="text-3xl font-display font-bold text-center mb-10">Skills</h2>

    <div class="grid grid-cols-1 md:grid-cols-3 gap-10">
      <!-- Languages -->
      <div>
        <h3
          class="text-sm font-medium text-gray-400 uppercase tracking-widest mb-4"
        >
          Languages
        </h3>
        <div class="flex flex-wrap gap-2">
          <span
            class="px-4 py-2 rounded-full border border-gray-700 text-gray-300 text-sm hover:border-accent hover:text-accent transition-colors cursor-default"
            >Python</span
          >
          <span
            class="px-4 py-2 rounded-full border border-gray-700 text-gray-300 text-sm hover:border-accent hover:text-accent transition-colors cursor-default"
            >JavaScript</span
          >
          <span
            class="px-4 py-2 rounded-full border border-gray-700 text-gray-300 text-sm hover:border-accent hover:text-accent transition-colors cursor-default"
            >HTML</span
          >
          <span
            class="px-4 py-2 rounded-full border border-gray-700 text-gray-300 text-sm hover:border-accent hover:text-accent transition-colors cursor-default"
            >CSS</span
          >
        </div>
      </div>

      <!-- Tools -->
      <div>
        <h3
          class="text-sm font-medium text-gray-400 uppercase tracking-widest mb-4"
        >
          Tools
        </h3>
        <div class="flex flex-wrap gap-2">
          <span
            class="px-4 py-2 rounded-full border border-gray-700 text-gray-300 text-sm hover:border-accent hover:text-accent transition-colors cursor-default"
            >Git</span
          >
          <span
            class="px-4 py-2 rounded-full border border-gray-700 text-gray-300 text-sm hover:border-accent hover:text-accent transition-colors cursor-default"
            >VS Code</span
          >
          <span
            class="px-4 py-2 rounded-full border border-gray-700 text-gray-300 text-sm hover:border-accent hover:text-accent transition-colors cursor-default"
            >Figma</span
          >
        </div>
      </div>

      <!-- Platforms -->
      <div>
        <h3
          class="text-sm font-medium text-gray-400 uppercase tracking-widest mb-4"
        >
          Platforms
        </h3>
        <div class="flex flex-wrap gap-2">
          <span
            class="px-4 py-2 rounded-full border border-gray-700 text-gray-300 text-sm hover:border-accent hover:text-accent transition-colors cursor-default"
            >GitHub</span
          >
          <span
            class="px-4 py-2 rounded-full border border-gray-700 text-gray-300 text-sm hover:border-accent hover:text-accent transition-colors cursor-default"
            >Vercel</span
          >
          <span
            class="px-4 py-2 rounded-full border border-gray-700 text-gray-300 text-sm hover:border-accent hover:text-accent transition-colors cursor-default"
            >Replit</span
          >
        </div>
      </div>
    </div>
  </div>
</section>
```

---

## Section 5 — Achievements

### Step 1 — Raw HTML, no styling

```html
<section id="achievements">
  <h2>Achievements</h2>

  <div>
    <div>
      <span>2024</span>
      <h3>1st Place — School Hackathon</h3>
      <p>
        Built a waste management app in 24 hours. Judged on impact and
        execution.
      </p>
    </div>

    <div>
      <span>2024</span>
      <h3>Python Certificate — CS50P</h3>
      <p>Completed Harvard's CS50 Python course with distinction.</p>
    </div>

    <div>
      <span>2023</span>
      <h3>Top 10% — ZCO Qualifier</h3>
      <p>Qualified for the Zonal Computing Olympiad regional round.</p>
    </div>
  </div>
</section>
```

---

### Step 2 — Section wrapper

```html
<section id="achievements" class="bg-gray-900 py-16 px-6">
  <div class="max-w-3xl mx-auto"></div>
</section>
```

- `max-w-3xl` — narrower than projects, achievements read better in a single focused column

---

### Step 3 — Section heading

```html
<h2 class="text-3xl font-display font-bold text-center mb-10">Achievements</h2>
```

---

### Step 4 — Make it a vertical timeline

```html
<div class="border-l border-gray-700 ml-4 flex flex-col"></div>
```

- `border-l border-gray-700` — left border becomes the timeline line
- `ml-4` — pushes the whole list slightly right

---

### Step 5 — Style each achievement item

```html
<div class="relative pl-8 pb-10"></div>
```

- `relative` — needed to position the dot absolutely inside
- `pl-8` — 32px padding left, pushes content away from the border line
- `pb-10` — 40px bottom padding, space between items

---

### Step 6 — Add the timeline dot

Place this as the first element inside each achievement div:

```html
<div
  class="absolute -left-2 top-1 w-4 h-4 rounded-full bg-accent border-2 border-gray-900"
></div>
```

- `absolute -left-2` — positions the dot on the left border line precisely
- `top-1` — aligns with the first line of text
- `w-4 h-4 rounded-full` — small circle
- `bg-accent` — accent colored dot pops on the gray line
- `border-2 border-gray-900` — ring effect that makes the dot look clean

---

### Step 7 — Style the year label

```html
<span class="text-xs text-accent font-medium uppercase tracking-widest">
  2024
</span>
```

- `text-xs` — very small, it's metadata
- `text-accent` — accent color ties it to the dot
- `uppercase tracking-widest` — eyebrow label style, consistent with skills

---

### Step 8 — Style the title and description

```html
<h3 class="text-lg font-semibold text-white mt-1 mb-1">
  1st Place — School Hackathon
</h3>
<p class="text-gray-400 text-sm">
  Built a waste management app in 24 hours. Judged on impact and execution.
</p>
```

---

### Final Achievements Section

```html
<section id="achievements" class="bg-gray-900 py-16 px-6">
  <div class="max-w-3xl mx-auto">
    <h2 class="text-3xl font-display font-bold text-center mb-10">
      Achievements
    </h2>

    <div class="border-l border-gray-700 ml-4 flex flex-col">
      <!-- Item 1 -->
      <div class="relative pl-8 pb-10">
        <div
          class="absolute -left-2 top-1 w-4 h-4 rounded-full bg-accent border-2 border-gray-900"
        ></div>
        <span class="text-xs text-accent font-medium uppercase tracking-widest"
          >2024</span
        >
        <h3 class="text-lg font-semibold text-white mt-1 mb-1">
          1st Place — School Hackathon
        </h3>
        <p class="text-gray-400 text-sm">
          Built a waste management app in 24 hours. Judged on impact and
          execution.
        </p>
      </div>

      <!-- Item 2 -->
      <div class="relative pl-8 pb-10">
        <div
          class="absolute -left-2 top-1 w-4 h-4 rounded-full bg-accent border-2 border-gray-900"
        ></div>
        <span class="text-xs text-accent font-medium uppercase tracking-widest"
          >2024</span
        >
        <h3 class="text-lg font-semibold text-white mt-1 mb-1">
          Python Certificate — CS50P
        </h3>
        <p class="text-gray-400 text-sm">
          Completed Harvard's CS50 Python course with distinction.
        </p>
      </div>

      <!-- Item 3 -->
      <div class="relative pl-8 pb-10">
        <div
          class="absolute -left-2 top-1 w-4 h-4 rounded-full bg-accent border-2 border-gray-900"
        ></div>
        <span class="text-xs text-accent font-medium uppercase tracking-widest"
          >2023</span
        >
        <h3 class="text-lg font-semibold text-white mt-1 mb-1">
          Top 10% — ZCO Qualifier
        </h3>
        <p class="text-gray-400 text-sm">
          Qualified for the Zonal Computing Olympiad regional round.
        </p>
      </div>
    </div>
  </div>
</section>
```

---

## Section 6 — Contact

### Step 1 — Raw HTML, no styling

```html
<section id="contact">
  <h2>Get In Touch</h2>
  <p>
    I'm always open to new opportunities, collaborations, or just a
    conversation.
  </p>
  <a href="mailto:arjun@email.com">Send me an email</a>
  <div>
    <a href="https://github.com">GitHub</a>
    <a href="https://linkedin.com">LinkedIn</a>
  </div>
</section>
```

---

### Step 2 — Section wrapper and centering

```html
<section id="contact" class="bg-gray-950 py-24 px-6 text-center">
  <div class="max-w-xl mx-auto"></div>
</section>
```

- `py-24` — more generous than other sections (96px), creates a sense of arrival
- `text-center` — everything centered, this is a closing statement
- `max-w-xl` — narrow, intimate feel

---

### Step 3 — Style the heading

```html
<h2 class="text-4xl font-display font-bold mb-4">Get In Touch</h2>
```

Slightly larger than other section headings — this is the final call to action.

---

### Step 4 — Style the subtext

```html
<p class="text-gray-400 text-lg mb-10">
  I'm always open to new opportunities, collaborations, or just a conversation.
</p>
```

---

### Step 5 — Style the primary email button

```html
<a
  href="mailto:arjun@email.com"
  class="inline-block bg-accent text-gray-950 font-semibold px-8 py-4 rounded-full hover:opacity-90 transition-opacity mb-8"
>
  Send me an email
</a>
```

- `bg-accent text-gray-950` — accent background, dark text for contrast
- `px-8 py-4` — bigger than the hero button, this is the final CTA
- `font-semibold` — heavier weight, reads as important
- `mb-8` — space below before the social links

---

### Step 6 — Style the social links

```html
<div class="flex justify-center gap-6">
  <a
    href="https://github.com"
    class="text-gray-400 text-sm hover:text-accent transition-colors"
  >
    GitHub ↗
  </a>
  <a
    href="https://linkedin.com"
    class="text-gray-400 text-sm hover:text-accent transition-colors"
  >
    LinkedIn ↗
  </a>
</div>
```

- `↗` — diagonal arrow is a modern convention for external links
- Muted by default, accent on hover — secondary to the email button

---

### Final Contact Section

```html
<section id="contact" class="bg-gray-950 py-24 px-6 text-center">
  <div class="max-w-xl mx-auto">
    <h2 class="text-4xl font-display font-bold mb-4">Get In Touch</h2>

    <p class="text-gray-400 text-lg mb-10">
      I'm always open to new opportunities, collaborations, or just a
      conversation.
    </p>

    <a
      href="mailto:arjun@email.com"
      class="inline-block bg-accent text-gray-950 font-semibold px-8 py-4 rounded-full hover:opacity-90 transition-opacity mb-8"
    >
      Send me an email
    </a>

    <div class="flex justify-center gap-6">
      <a
        href="https://github.com"
        class="text-gray-400 text-sm hover:text-accent transition-colors"
      >
        GitHub ↗
      </a>
      <a
        href="https://linkedin.com"
        class="text-gray-400 text-sm hover:text-accent transition-colors"
      >
        LinkedIn ↗
      </a>
    </div>
  </div>
</section>
```

---

## Section 7 — Footer

### Step 1 — Raw HTML, no styling

```html
<footer>
  <p>Designed and built by Arjun S.</p>
  <p>© 2024</p>
</footer>
```

---

### Step 2 — Style it

```html
<footer class="bg-gray-900 border-t border-gray-800 py-8 px-6">
  <div
    class="max-w-5xl mx-auto flex justify-between items-center text-sm text-gray-500"
  >
    <p>Designed and built by <span class="text-accent">Arjun S.</span></p>
    <p>© 2024</p>
  </div>
</footer>
```

- `border-t border-gray-800` — thin top border separates footer from contact
- `text-gray-500` — very muted, footer is credit territory
- `flex justify-between` — name on left, year on right
- `text-accent` on the name — small but warm personal touch

---

## The Universal Pattern

Every section follows the same sequence:

```
1. Write raw HTML with correct semantic tags (no classes)
2. Add flex/grid to control layout direction
3. Add justify/align to control positioning
4. Add gap/padding for spacing
5. Add colors and backgrounds
6. Add typography (size, weight, color)
7. Add hover states and transitions
```

And every section uses the same two-layer structure:

```html
<section class="bg-[color] py-[space] px-6">
  <!-- full width background -->
  <div class="max-w-[size] mx-auto">
    <!-- constrained, centered content -->
    ...
  </div>
</section>
```

---

## Key Tailwind Classes Reference

| Class                       | What it does                            |
| --------------------------- | --------------------------------------- |
| `flex`                      | Makes children sit side by side         |
| `justify-between`           | Pushes children to opposite ends        |
| `items-center`              | Vertically centers flex children        |
| `gap-6`                     | 24px space between flex/grid children   |
| `grid grid-cols-3`          | 3-column CSS grid                       |
| `md:grid-cols-2`            | 2 columns at ≥768px                     |
| `lg:grid-cols-3`            | 3 columns at ≥1024px                    |
| `max-w-5xl mx-auto`         | Constrain width and center              |
| `px-6 py-16`                | Horizontal and vertical padding         |
| `text-gray-400`             | Muted secondary text                    |
| `text-accent`               | Accent color from config                |
| `rounded-full`              | Pill / fully rounded shape              |
| `rounded-2xl`               | Softly rounded card corners             |
| `hover:text-accent`         | Color change on hover                   |
| `transition-colors`         | Smooth color animation                  |
| `flex-grow`                 | Fills remaining space in flex container |
| `absolute` / `relative`     | Precise positioning (timeline dot)      |
| `uppercase tracking-widest` | Eyebrow label style                     |
| `leading-none`              | Tight line height for big headings      |
| `blur-3xl`                  | Extreme blur for ambient glow effect    |
| `pointer-events-none`       | Decorative element, ignores clicks      |
