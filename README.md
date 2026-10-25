# bennykent-skills

Claude Code skills grouped into packs by stack. Turn on only the packs a
project needs: every enabled skill's description is loaded into each session,
so a few relevant skills work better than dozens of overlapping ones.

| Pack | Use it for | Skills |
| --- | --- | --- |
| `superpowers` | Every project | Upstream [obra/superpowers](https://github.com/obra/superpowers): brainstorming, plans, TDD, systematic debugging, code review, verification |
| `design` | Any UI work | frontend-design, web-design-guidelines, emil-design-eng, create-design-md, review-animations, mobile-native, break-ui, webapp-testing, **neumorphism**, **liquid-glass**, **nothing-design** |
| `ui-ux-pro-max` | Any UI work | Upstream [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) (searchable design-system data; includes neumorphism, glassmorphism, claymorphism, and more; requires Python) |
| `ui-toolkit` | Optional web UI work | shadcn and Magic UI component registries, plus Playwright browser verification; requires Node.js 20+ |
| `impeccable` | Deep UI critique, polish, and visual refinement | Complete upstream [pbakaus/impeccable](https://github.com/pbakaus/impeccable) plugin, including commands and scripts |
| `flutter` | Flutter / Dart apps | flutter-ui-design, flutter-ui-patterns, flutter-accessibility, flutter-responsive-layout, flutter-code-review, flutter-apply-architecture-best-practices |
| `supabase` | Supabase backends | supabase, supabase-postgres-best-practices |
| `react-web` | React / Next.js | react-best-practices, composition-patterns, react-view-transitions, nextjs-app-router-patterns, react-state-management, tailwind-design-system |
| `typescript` | TS / JS / Node | typescript-advanced-types, modern-javascript-patterns, nodejs-backend-patterns, javascript-testing-patterns |
| `react-native` | React Native / Expo | react-native-skills, react-native-architecture, react-native-design |
| `kotlin-android` | Kotlin / Android / Compose | compose-* (state, components, animations, performance, testing, focus), kotlin-* (coroutines and Flow, control flow, API design), adaptive, jetpack-compose-performance, navigation-3, edge-to-edge, testing-setup, android security, java-to-kotlin, mobile-android-design |

## Use it on your own computer (every project)

```
/plugin marketplace add bennykent21/claude-skills
/plugin install superpowers@bennykent-skills
/plugin install design@bennykent-skills
```

For web UI component discovery and browser QA, opt in separately:

```text
/plugin install ui-toolkit@bennykent-skills
```

The UI toolkit starts three MCP servers (shadcn registry, Magic UI registry, Playwright). It requires Node.js 20+ for Playwright. Install it only on projects where you want those tools enabled.

Then install stack packs where you need them, choosing "project" scope so
they only load in that repository.

## Use it in a repository (also works in Claude Code on the web)

Add this to the repository's `.claude/settings.json`, keeping only the packs
that project uses. Cloud sessions install them automatically.

```json
{
  "extraKnownMarketplaces": {
    "bennykent-skills": {
      "source": { "source": "github", "repo": "bennykent21/claude-skills" }
    }
  },
  "enabledPlugins": {
    "superpowers@bennykent-skills": true,
    "design@bennykent-skills": true,
    "react-web@bennykent-skills": true,
    "typescript@bennykent-skills": true
  }
}
```

Starter sets:

- Flutter + Supabase: `superpowers`, `design`, `flutter`, `supabase`
- Next.js: `superpowers`, `design`, `react-web`, `typescript`
- Expo app: `superpowers`, `design`, `react-native`, `typescript`
- Android (Kotlin): `superpowers`, `design`, `kotlin-android`

## Sources and licences

The packs under `plugins/` include copied upstream skill prompts and supporting files. External packs such as UI/UX Pro Max and Impeccable are registered directly from their upstream repositories so their scripts, data, and command references remain intact. Check each upstream repository for its current licence and attribution requirements.

- [anthropics/skills](https://github.com/anthropics/skills) (frontend-design, webapp-testing)
- [emilkowalski/skills](https://github.com/emilkowalski/skills) (emil-design-eng, review-animations, mobile-native, break-ui)
- [ibelick/ui-skills](https://github.com/ibelick/ui-skills) (create-design-md)
- [dominikmartn/nothing-design-skill](https://github.com/dominikmartn/nothing-design-skill) (Nothing-inspired UI; MIT)
- [stormaref/LiquidGlassSkill](https://github.com/stormaref/LiquidGlassSkill) (Liquid Glass; MIT; includes Angular refraction code and CSS fallback)
- [shadcn/ui MCP](https://ui.shadcn.com/docs/mcp), [Magic UI MCP](https://github.com/magicuidesign/mcp), and [Microsoft Playwright MCP](https://github.com/microsoft/playwright) (configured in optional `ui-toolkit` pack)
- [pbakaus/impeccable](https://github.com/pbakaus/impeccable) (complete upstream plugin, registered as an external pack)
- [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) (complete upstream plugin, registered as an external pack)
- [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) (MIT)
- [wshobson/agents](https://github.com/wshobson/agents) (MIT)
- [thiennc-tesoglobal/flutter-skills](https://github.com/thiennc-tesoglobal/flutter-skills) (BSD-3-Clause)
- [flutter/skills](https://github.com/flutter/skills) (BSD-3-Clause)
- [supabase/agent-skills](https://github.com/supabase/agent-skills) (MIT)
- [chrisbanes/skills](https://github.com/chrisbanes/skills) (Apache-2.0)
- [android/skills](https://github.com/android/skills) (Apache-2.0)
- [Kotlin/kotlin-agent-skills](https://github.com/Kotlin/kotlin-agent-skills) (Apache-2.0)

To refresh a pack, re-copy the skill folders from upstream and bump the
pack's `version` in its `plugin.json`.
