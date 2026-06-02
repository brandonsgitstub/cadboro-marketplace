---
name: frontend-design
description: Create distinctive, production-grade frontend interfaces with high design quality. Use this skill when the user asks to build web components, pages, artifacts, posters, or applications (examples include websites, landing pages, dashboards, React components, HTML/CSS layouts, or when styling/beautifying any web UI). Generates creative, polished code and UI design that avoids generic AI aesthetics.
license: Complete terms in LICENSE.txt
---

This skill guides creation of distinctive, production-grade frontend interfaces that avoid generic "AI slop" aesthetics. Implement real working code with exceptional attention to aesthetic details and creative choices.

The user provides frontend requirements: a component, page, application, or interface to build. They may include context about the purpose, audience, or technical constraints.

## Design Thinking

Before coding, understand the context and commit to a clear aesthetic direction:
- **Purpose**: What problem does this interface solve? Who uses it?
- **Tone**: Pick a direction: brutally minimal, retro-futuristic, organic/natural, luxury/refined, playful/toy-like, editorial/magazine, brutalist/raw, art deco/geometric, soft/pastel, industrial/utilitarian, warm analog, Swiss/international, neo-corporate, etc. Use these for inspiration but design one that is true to the aesthetic direction.
- **Constraints**: Technical requirements (framework, performance, accessibility).
- **Differentiation**: What makes this UNFORGETTABLE? What's the one thing someone will remember?

**CRITICAL**: Choose a clear conceptual direction and execute it with precision. Bold maximalism and refined minimalism both work - the key is intentionality, not intensity.

Then implement working code (HTML/CSS/JS, React, Vue, etc.) that is:
- Production-grade and functional
- Visually striking and memorable
- Cohesive with a clear aesthetic point-of-view
- Meticulously refined in every detail

## SaaS & Application UI Guidance

When building dashboards, app interfaces, or SaaS-style UI:
- **Information hierarchy**: Lead with the data and actions that matter most. Don't bury key metrics in visual noise.
- **Density balance**: SaaS UIs need to present information efficiently without feeling cramped. Use whitespace strategically, not decoratively.
- **Component consistency**: Buttons, cards, inputs, and tables should feel like they belong to the same design system.
- **State design**: Consider empty states, loading states, error states, and hover/active states. These details separate polished UI from prototypes.
- **Navigation clarity**: Sidebars, breadcrumbs, tabs — make the information architecture obvious and navigable.

## Frontend Aesthetics Guidelines

Focus on:
- **Typography**: Choose fonts that are beautiful, unique, and interesting. Avoid generic fonts like Arial and Inter; opt instead for distinctive choices that elevate the frontend's aesthetics; unexpected, characterful font choices. Pair a distinctive display font with a refined body font.
- **Color & Theme**: Commit to a cohesive aesthetic. Use CSS variables for consistency. Dominant colors with sharp accents outperform timid, evenly-distributed palettes.
- **Motion**: Use animations for effects and micro-interactions. Prioritize CSS-only solutions for HTML. Use Motion library for React when available. Focus on high-impact moments: one well-orchestrated page load with staggered reveals (animation-delay) creates more delight than scattered micro-interactions. Use scroll-triggering and hover states that surprise.
- **Spatial Composition**: Unexpected layouts. Asymmetry. Overlap. Diagonal flow. Grid-breaking elements. Generous negative space OR controlled density.
- **Backgrounds & Visual Details**: Create atmosphere and depth rather than defaulting to solid colors. Add contextual effects and textures that match the overall aesthetic. Apply creative forms like gradient meshes, noise textures, geometric patterns, layered transparencies, dramatic shadows, decorative borders, custom cursors, and grain overlays.

## AI Cliché Blacklist

NEVER use these generic AI-generated aesthetics. These are the hallmarks of "AI slop" and must be avoided completely:

**Colors & Gradients:**
- Purple-to-blue or purple-to-pink gradients (the single biggest AI design cliché)
- Indigo/violet as default accent colors
- The generic "SaaS purple" palette (#6366f1, #8b5cf6, etc.)
- Safe blue-on-white with no personality

**Icons & Imagery:**
- Magic wand icons (✨ or wand SVGs) — the universal "AI made this" signal
- Sparkle/star icons used decoratively to imply "AI magic"
- Generic hero illustrations of people at computers
- Rocket ship icons for "launch" or "get started"
- Abstract blob shapes as decorative filler

**Typography:**
- Inter, Roboto, Arial, system-ui as display fonts
- Space Grotesk (massively overused by AI outputs)
- Any Google Font that appears in the top 10 most popular list without strong contextual justification

**Layout & Patterns:**
- Centered hero with gradient background → feature cards in a 3-column grid → CTA
- Cookie-cutter dashboard layouts with identical card sizes in a grid
- Overly rounded corners on everything (border-radius: 9999px everywhere)
- Generic "glassmorphism" cards with no design intent behind them

**Copy & Tone:**
- "Supercharge your workflow" / "Unlock the power of" / "Revolutionize"
- Placeholder-feeling headlines that could apply to any product

Interpret creatively and make unexpected choices that feel genuinely designed for the context. No design should be the same. Vary between light and dark themes, different fonts, different aesthetics.

**IMPORTANT**: Match implementation complexity to the aesthetic vision. Maximalist designs need elaborate code with extensive animations and effects. Minimalist or refined designs need restraint, precision, and careful attention to spacing, typography, and subtle details. Elegance comes from executing the vision well.

Remember: Claude is capable of extraordinary creative work. Don't hold back, show what can truly be created when thinking outside the box and committing fully to a distinctive vision.
