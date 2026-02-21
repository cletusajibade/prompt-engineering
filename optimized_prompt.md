## Role and Task
You are a senior Laravel engineer working in the `<PROJECT_NAME>` codebase. Implement a refined **User Portal for authenticated non-admin users** by extending existing dashboard behavior, not rebuilding from scratch.

## Objective
Enhance the current `/dashboard` experience so it clearly supports:
1. My Applications Timeline
2. My Learning Journey
3. Profile completeness + action nudges
4. Discord community CTA

## Codebase Context (must align with this)
- Stack: Laravel + Blade + Tailwind (Breeze-style app layout).
- Existing route: `GET /dashboard` (`DashboardController@index`) under `auth` middleware.
- Existing files already contain related logic/UI:
  - `app/Http/Controllers/DashboardController.php`
  - `resources/views/dashboard.blade.php`
  - `routes/web.php`
- Data sources already used:
  - `TrainingRegistration` records filtered by authenticated user email.
  - `LearningPath` for selected/related paths.
  - User profile/email verification state from auth user.
- Existing sections already present in UI; improve quality, clarity, and consistency rather
than duplicating features.

## Functional Requirements
- **My Applications Timeline**
  - Show user’s training registrations (matched by user email), newest first.
  - For each row: date, program title/category, verification status, next step.
  - Verification status must distinguish verified vs pending verification.
  - Next steps should account for missing registration fields.
- **My Learning Journey**
  - Show selected path inferred from latest registration intent.
  - Show saved tracks derived from applied program titles.
  - Show quick links to related learning paths/programs.
- **Profile Completeness + Nudges**
  - Display completeness percentage and checklist.
  - Include nudges for incomplete actions: profile info, email verification, missing registration details.
  - Each nudge must have a clear CTA target route.
- **Discord CTA**
  - Add/retain a clear “Join Discord Community” button.
  - Use this invite URL: `<LINK>` (replace existing hardcoded URL if needed).

## UX and Design Constraints
- Preserve existing dashboard theme/style and component patterns (`x-app-layout`, current spacing/cards/tones).
- Keep design consistent with current palette and typography; avoid introducing a different design system.
- Ensure responsive behavior (mobile + desktop) and empty states.
- Keep copy concise, actionable, and user-centered.

## Engineering Constraints
- Do not introduce admin-only behavior in this portal.
- Avoid breaking existing routes or auth flows.
- Prefer incremental edits to existing controller/view over new parallel implementations.
- Keep logic readable and testable; extract helper methods only when it improves clarity.

## Validation & Quality Bar
- Add/update feature tests for dashboard rendering and key states:
  - user with no registrations
  - user with unverified registration
  - user with verified registration
  - profile completeness/nudge visibility
  - discord CTA presence and URL
- Ensure tests pass and no regressions in current dashboard behavior.

## Output Format
Return:
1. Brief implementation summary
2. Files changed with purpose
3. Key logic/design decisions
4. Test coverage added/updated and results
5. Any assumptions made