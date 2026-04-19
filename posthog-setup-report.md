<wizard-report>
# PostHog post-wizard report

The wizard has completed a deep integration of PostHog into the Skild TanStack Start application. Here's what was added:

- **`posthog-js`**, **`posthog-node`**, and **`@posthog/react`** installed as dependencies
- **`vite.config.ts`**: Added a `/ingest` reverse proxy to route PostHog traffic through the Vite dev server, avoiding CORS issues
- **`.env`**: Created with `VITE_PUBLIC_POSTHOG_PROJECT_TOKEN` and `VITE_PUBLIC_POSTHOG_HOST` environment variables
- **`src/routes/__root.tsx`**: Added `PostHogProvider` wrapping the app shell (inside `ClerkProvider`), and a `PostHogIdentifier` component that calls `posthog.identify()` whenever a Clerk user signs in, and `posthog.reset()` on sign-out
- **`src/components/SkillCard.tsx`**: Tracks `skill_install_command_copied` (with slug, title, and install command) when the copy button is clicked, and `skill_opened` (with slug, title, and category) when the Open link is clicked
- **`src/routes/index.tsx`**: Tracks `browse_registry_clicked` and `publish_skill_clicked` on the hero CTA links

| Event | Description | File |
|---|---|---|
| `skill_install_command_copied` | User copies the install command from a skill card | `src/components/SkillCard.tsx` |
| `skill_opened` | User clicks the Open button on a skill card | `src/components/SkillCard.tsx` |
| `browse_registry_clicked` | User clicks the Browse Registry CTA on the home hero | `src/routes/index.tsx` |
| `publish_skill_clicked` | User clicks the Publish Skill CTA on the home hero | `src/routes/index.tsx` |
| `user_signed_in` | Clerk user identified in PostHog on sign-in | `src/routes/__root.tsx` |

## Next steps

We've built some insights and a dashboard for you to keep an eye on user behavior, based on the events we just instrumented:

- **Dashboard**: [Analytics basics](https://us.posthog.com/project/388563/dashboard/1485364)
- **Insight**: [Skill install commands copied](https://us.posthog.com/project/388563/insights/8kEayJPR)
- **Insight**: [Hero CTA funnel: Browse → Publish](https://us.posthog.com/project/388563/insights/sS8EUcNU)
- **Insight**: [Skill opens over time](https://us.posthog.com/project/388563/insights/r5BMt1CF)
- **Insight**: [CTA clicks comparison](https://us.posthog.com/project/388563/insights/WipQ6NMV)
- **Insight**: [User sign-ins over time](https://us.posthog.com/project/388563/insights/GlAwkGsY)

### Agent skill

We've left an agent skill folder in your project. You can use this context for further agent development when using Claude Code. This will help ensure the model provides the most up-to-date approaches for integrating PostHog.

</wizard-report>
