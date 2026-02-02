# Presentation Guidelines

These guidelines codify the visual style and design principles observed across Emery Berger's presentations, including *Performance Matters*, *Mesh* (CppCon 2019), *Cambrian Explosion*, *Powered by AI* (CppCon 2023), and *Python Performance Matters*.

---

## Core Philosophy

Every slide should be **instantly graspable**. The audience should understand the point within 2--3 seconds of seeing the slide. Text is a last resort; images, diagrams, and large typography do the heavy lifting. The presentations function more like visual storytelling than illustrated lecture notes.

---

## Slide Format

- **16:9 widescreen**, always.
- **One idea per slide.** Never two. If a slide has two ideas, split it.
- **Progressive builds over multiple slides** rather than animation within a single slide. The same title may appear on 3--5 consecutive slides as content is layered in (e.g., adding arrows, labels, or new elements one at a time). This gives the presenter full control of pacing.

---

## Typography

- **Massive, bold headlines.** Titles should be the largest element on the slide, often 60--100+ pt. They are the slide's entire message, not a label for content below.
- **Very few words per slide.** Most content slides have fewer than 15 words total. Many have fewer than 10. A single short phrase or sentence is ideal.
- **Mixed font weights for emphasis.** Bold for key terms, italic for secondary/qualifying text, regular weight for supporting context. Size differences between primary and secondary text should be dramatic (2--3x).
- **No sentence case for titles.** Use Title Case or ALL CAPS for impact. Small caps (like `STABILIZER`, `MESH`) for tool/system names gives them a branded feel.

---

## Color & Backgrounds

- **Two background modes:**
  - **Black** for dramatic, narrative, or cinematic moments (opening sequences, big reveals, animations). Text on black is bold yellow, blue, or white.
  - **White** for explanatory content, diagrams, data, and technical details. Text on white is black, with colored accents.
- **Color is semantic, not decorative:**
  - **Red:** warnings, annotations, hand-drawn circles/arrows calling attention to something.
  - **Blue:** key technical terms, links, tool names, the "primary accent" color.
  - **Green:** positive outcomes, correct results, live objects in memory diagrams.
  - **Orange/Yellow:** highlights, emphasis, secondary accent. Used for chart lines, callout labels, and the iconic yellow-on-black title style.
  - **Gray:** de-emphasized or background elements, inactive/dead items in diagrams.
- **Bold, saturated colors only.** No pastels, no gradients, no subtle tints. Colors should read clearly from the back of a large room.

---

## Images & Visual Content

### Scale and Placement
- Images are **large**---often filling 50--100% of the slide. Never use small, decorative thumbnail images. If an image is worth including, it should dominate.
- Full-bleed images (edge to edge) are preferred for cinematic/narrative slides.
- When combining image and text, use a **split layout**: image on one side, text on the other. Or place text as a large overlay on the image.

### Types of Images Used
- **Pop culture references and memes:** The Simpsons, Star Wars, Grumpy Cat, "expanding brain" meme, Don Quixote, Jurassic Park. These are not decoration---they are the *primary vehicle for conveying concepts*. The audience remembers "Malloc of La Mancha" or "The Simpsons: Tapped Out = the ride is over" long after they forget a bullet point.
- **Custom diagrams:** Memory layouts, system architectures, and data flow diagrams drawn in a clean, colorful style with large labels. Use colored blocks (blue, green, orange, gray) rather than thin-line wireframes.
- **Annotated screenshots:** Real tool output (e.g., Scalene profiler) shown as screenshots, with large color-coded labels added to explain each section.
- **Charts and graphs:** Large, clean, with minimal chartjunk. Axes labeled in large text. Key data points circled or annotated with bold callout text directly on the chart (e.g., "Too Hot!" with an explosion graphic, "Transistor counts still increased" with an arrow).

### Visual Motifs
- Each presentation has a **recurring visual theme** carried throughout:
  - *Performance Matters:* Star Wars + custom cartoon character (the blue-shirt developer)
  - *Cambrian Explosion / Powered by AI:* Simpsons dinosaur characters, evolution metaphor
  - *Mesh:* Don Quixote / La Mancha theme (windmills, Spain), yellow/gold color palette
  - *Python Performance Matters:* Python logos, Simpsons, expanding brain meme
- Commit to the theme. Reuse motif characters/imagery across multiple slides so the audience builds a mental association.

---

## Diagrams & Technical Illustrations

- **Large colored blocks** for memory pages, objects, processes. Not thin outlines---solid filled rectangles with clear color distinctions.
- **Arrows should be thick and obvious.** Thin arrows disappear at distance.
- **Dark backgrounds (dark blue, black)** work well for memory/system diagrams where colored blocks need to pop.
- **Progressive diagram builds:** Show the empty structure first, then add elements across successive slides. This is critical for teaching---never show a complete complex diagram all at once.
- **Label directly on the diagram**, not in a separate legend. Place labels adjacent to the thing they describe.

---

## Code

- Code appears in **dark-background boxes** (terminal/editor style), but is always secondary to the visual narrative.
- Keep code snippets **very short**---5--10 lines maximum. If more context is needed, use multiple slides.
- Code is shown to illustrate a point, never as the point itself. Surround it with large text explaining what to notice.
- **Never show code without visual annotation** pointing to the relevant lines or explaining what matters.

---

## Charts & Data

- Axes and labels in **large, readable fonts.** If the axis labels aren't legible from 30 feet, they're too small.
- Use **hand-drawn style annotations** on charts: red circles around key data points, arrows pointing to inflection points, bold text callouts ("13x!" or "Too Hot!").
- Prefer **scatter plots and line charts** over bar charts when showing trends.
- **Side-by-side comparisons** (e.g., two charts showing Moore's Law vs. Dennard Scaling) are effective for contrasting related trends.
- Show the **minimum necessary data.** No grid lines unless they aid comprehension. No 3D effects. No chart borders.

---

## Humor & Narrative

- **Humor is structural, not incidental.** It's not comic relief between serious slides---it *is* the slide. Technical points are delivered through visual jokes, puns, memes, and pop culture analogies.
- **Puns and wordplay** in slide titles: "Malloc of La Mancha," "Compacting the Uncompactable!," "Use the Coz" (Use the Force).
- **Meme formats** used to create escalating sequences (expanding brain meme for Python -> Scalene -> Scalene+AI).
- **Running gags** that pay off later in the talk. Set up a visual motif early and call back to it.
- **Self-deprecating and playful tone.** The humor makes dense technical material approachable without dumbing it down.

---

## Slide Types (Templates)

### Title Slide
- Dramatic, themed. Large bold title (often styled/branded). Speaker name and affiliation below in smaller text. Lab logo (PLASMA) if applicable. Optional: QR code, conference branding.
- Can use either black or themed background.

### Narrative/Transition Slide
- Black background. Short phrase in large colored text (blue or yellow). Sets up the next section of the talk. Often references pop culture ("A short time ago in a valley far, far away...").

### Image Slide
- Full-bleed or near-full-bleed image. Title or no title. The image *is* the content. Used for dramatic moments, pop culture references, and visual metaphors.

### Concept Slide
- White background. One large headline stating the concept. Optional: a simple supporting image or icon. No bullets. No paragraphs.

### Diagram/Technical Slide
- Clean diagram with large labels. Can be on white or dark background. Title at top. Progressive builds across multiple slides.

### Data/Chart Slide
- Large chart with bold annotations. Title states the takeaway (not "Results" but "Performance not easy anymore"). Annotations tell the audience what to see.

### Screenshot/Demo Slide
- Actual tool output or UI screenshot, annotated with colored labels explaining each section. Often zoomed to highlight the relevant portion.

### Closing/Summary Slide
- Key takeaways in large text. Tool names with logos. QR codes linking to repos/tools. Speaker contact info. Lab branding.

---

## What to Avoid

- **Bullet point lists.** Almost never used. If you find yourself making a bulleted list, turn each bullet into its own slide with a large headline.
- **Small text.** If any text on the slide requires effort to read from the back of the room, it's too small. The minimum readable size is roughly 28pt; most text should be 40pt+.
- **Paragraphs of text.** Never. If the audience is reading, they're not listening.
- **Clip art or stock photos that feel generic.** Every image should be specific, evocative, and ideally funny or surprising.
- **Decorative borders, drop shadows, or gradient fills.** Keep the visual design flat and bold.
- **Complex tables.** If data requires a table, simplify it to the 2--3 numbers that matter and present those as large text with context.
- **Slide numbers, footers, or logos on every slide.** These add clutter. Reserve branding for title and closing slides.
- **Templates with busy backgrounds or corporate chrome.** The slide background should be either solid black or solid white (with rare exceptions for conference-mandated templates).
