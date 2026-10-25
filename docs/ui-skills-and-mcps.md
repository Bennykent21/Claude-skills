# UI design skills and MCP research

**Reviewed:** 25 October 2026

This note records the additions to the Bennykent skills collection and the next tools worth considering. The goal is to improve the interfaces the agent actually builds, not simply make the plugin list longer.

## Existing coverage: do not duplicate it

The marketplace already registers [UI/UX Pro Max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill). Its current searchable catalogue includes 79 styles (50 active), 192 palettes, 74 font pairings, 119 UX guidelines, 105 icons, 17 GSAP presets, 25 chart types, and 22 technology stacks. Its style library already includes neumorphism, glassmorphism, claymorphism, brutalism, bento layouts, Liquid Glass, and more.

That makes another large general style database mostly redundant. The new style skills are specialist playbooks for implementation details that are easy to get wrong; UI/UX Pro Max remains the starting catalogue for comparing styles and palettes.

## Added specialist styles

| Skill | Source | Why it earns a place |
| --- | --- | --- |
| `neumorphism` | Written for this collection | A focused soft-UI recipe with consistent light direction, raised/inset states, dark-mode guidance, and explicit accessibility rules. It warns against low-contrast text and using shadows as the only state indicator. |
| `liquid-glass` | [stormaref/LiquidGlassSkill](https://github.com/stormaref/LiquidGlassSkill), MIT | Goes beyond generic blur-based glassmorphism: ambient backdrop, rim highlights, a CSS fallback, optional Chromium refraction, theme handling, menu/modal tiers, and performance-minded guidance. Includes its CSS, Angular directive, demo, references, and licence. |
| `nothing-design` | [dominikmartn/nothing-design-skill](https://github.com/dominikmartn/nothing-design-skill), MIT | A deliberately different industrial, monochrome style with typographic hierarchy, dark/light tokens, mechanical controls, dot-grid motifs, and platform mappings. |

Use a specialist style only when it fits the product or the user requests it. It is not a reason to overwrite an existing design system. The Liquid Glass skill notes an important limitation: SVG-referenced backdrop-filter refraction is Chromium-specific; its ordinary CSS blur remains the fallback for other engines. The refraction code is Angular-specific, and the skill explains how to port it.

## Added optional MCP plugin: `ui-toolkit`

MCP is the live-tool layer; a skill contains workflow instructions. Keeping these servers in a separate opt-in plugin means projects that do not need web UI tooling do not load them.

| Server | What it adds | Why selected |
| --- | --- | --- |
| [shadcn MCP](https://ui.shadcn.com/docs/mcp) | Search, inspect, and install components and blocks from configured registries | Official registry support, including compatible third-party and private registries |
| [Magic UI MCP](https://github.com/magicuidesign/mcp) | Search the Magic UI registry and retrieve component details/instructions | Useful for motion-rich elements and visual effects without embedding a giant component catalogue in this repo |
| [Microsoft Playwright MCP](https://github.com/microsoft/playwright) | Navigate pages, inspect accessibility snapshots, interact with controls, and exercise browser flows | Helps the agent verify the rendered output instead of relying on source-code guesses |

The bundled configuration uses the upstream documented package commands and does not embed API keys. **Node.js 20+ is required for Playwright MCP.** MCP packages execute as local processes, so review the source and permissions before enabling them. The accompanying `ui-build-review` skill tells the agent to search before re-creating components, test at desktop and mobile widths, inspect important interaction states, and report what was genuinely browser-verified.

Install the optional pack using:

```text
/plugin install ui-toolkit@bennykent-skills
```

## Strong optional integrations, deliberately not bundled

- **[Figma MCP](https://developers.figma.com/docs/figma-mcp-server/):** best when a real Figma file is the source of truth. It can provide design context and, with the right access, write native Figma content. It is intentionally not bundled because it depends on the user's Figma account, authentication, and feature/seat access.
- **[Chrome DevTools MCP](https://github.com/ChromeDevTools/chrome-devtools-mcp):** worth adding when computed CSS, browser-console diagnosis, network inspection, and performance traces are important. It overlaps with Playwright's browser-control role, so do not load both automatically unless the workflow benefits from both.
- **[21st MCP](https://21st.dev/mcp):** can search a component catalogue and generate UI variants, but it requires a user API key. Keep it separate from the default pack and never commit credentials in this repository.

## Candidates not copied

- [nicohodt/claude-code-ui-ux-skill](https://github.com/nicohodt/claude-code-ui-ux-skill) has a useful 84-style catalogue, but its role substantially overlaps with the already-registered UI/UX Pro Max database.
- Other broad UI skills such as [lcanady/ui-skill](https://github.com/lcanady/ui-skill) and multipurpose design skill collections may be useful for individual users, but the current stack already contains frontend design, design-system extraction, animation review, accessibility guidance, and web-app testing. Copying them wholesale would increase overlap and context load rather than clearly add a capability.

## Source references

- [UI/UX Pro Max README](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)
- [shadcn MCP documentation](https://ui.shadcn.com/docs/mcp)
- [Magic UI MCP repository](https://github.com/magicuidesign/mcp)
- [Playwright MCP getting started](https://github.com/microsoft/playwright/blob/main/docs/src/getting-started-mcp.md)
- [Figma MCP documentation](https://developers.figma.com/docs/figma-mcp-server/)
- [Chrome DevTools MCP](https://github.com/ChromeDevTools/chrome-devtools-mcp)
