---
name: ui-build-review
description: Use when building or polishing a web interface and the UI toolkit's component-registry or browser MCP tools are available. Combines registry discovery with rendered visual and interaction verification.
---

# UI Build & Review

Use the UI toolkit's MCPs as capabilities, not as a substitute for design judgment. If a server is unavailable, continue with the capabilities that exist and state what could not be checked.

## Workflow

1. **Understand the product and existing conventions.** Inspect the current stack, routes, design tokens, component library, and existing states before choosing new primitives.
2. **Choose a deliberate style.** Use the user's requested style; for style discovery consult UI/UX Pro Max. Don't silently default to a trendy style or combine unrelated visual systems. Preserve an established design system unless asked to redesign it.
3. **Search before composing.** Use the shadcn registry MCP to search/view existing primitives or blocks before writing new ones. Use the Magic UI registry MCP for motion-rich or decorative elements only when they serve a product purpose. Check licensing and dependencies before adopting any third-party component.
4. **Implement in the project's existing stack.** Prefer accessible, composable primitives. Do not copy in a whole component library for one isolated effect. Keep tokens central and avoid duplicating components already present.
5. **Run the app and inspect the rendered result.** Use Playwright MCP to navigate, interact, and capture the relevant states. Check at least the main desktop width and a narrow mobile viewport. If browser tools are unavailable, make that limitation explicit.
6. **Verify real states, not just the happy path.** Inspect loading, empty, error, disabled, hover, focus-visible, selected, and open states where relevant. Test keyboard operation and forms, and check the browser console/network for errors when the tools expose them.
7. **Review visual quality.** Look for spacing and alignment drift, broken wrapping, overflow, inconsistent radii/elevation, unreadable contrast, poor image crops, and motion that is excessive or ignores reduced-motion preferences. Compare the screenshot against the intended direction, then fix specific defects.
8. **Report evidence honestly.** Distinguish source-code review from browser-verified results. Never say that an interface was visually tested unless the browser actually loaded and inspected it.

## MCP safety

MCP servers run third-party code or connect to external services. Use only the configured servers the user expects, review generated dependencies, and do not copy API keys or credentials into repository files.
