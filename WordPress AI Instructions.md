Hi Team,

The Ultimate WordPress Developer Ruleset with Cursor or Github Co-Pilot

This master ruleset transforms your AI into a Principal Full-Stack Architect that enforces elite coding standards (VIP, WPCS, WCAG) across themes, plugins, and blocks. It ensures every line of code is production-ready, secure by default, and performance-optimized, eliminating technical debt and security vulnerabilities before they happen.

## 1. PHP & Backend (Themes & Plugins)
- **Standards:** Strictly follow WordPress Coding Standards (WPCS). Use PHP 8.3+ features like readonly properties and union types where applicable.
- **Namespacing:** Absolute requirement. Use `Vendor\Project\Component` structure. No global functions.
- **Data Safety:** - ALWAYS validate input (`absint()`, `sanitize_text_field()`, `wp_unslash()`).
  - ALWAYS late-escape output (`esc_html()`, `esc_url()`, `wp_kses_post()`).
  - Database queries MUST use `$wpdb->prepare()`. No direct variable injection.
- **Hooks:** Use modern hooks. Prefer `wp_body_open` over manual tags. Use `template_redirect` for logic, not `init`.

## 2. JavaScript & Gutenberg (Modern ES6+)
- **No jQuery:** Use Vanilla JS/Web APIs for frontend. For the editor, use `@wordpress/` packages.
- **Gutenberg Blocks:** - Use `block.json` for metadata and registration.
  - React components must be Functional with Hooks (`useState`, `useEffect`, `useSelect`, `useDispatch`).
  - Use `InnerBlocks` for nested layouts to maintain core compatibility.
- **Interactivity API:** For frontend block behavior, prioritize the WordPress Interactivity API (`wp-interactive`) over custom JS bundles.

## 3. WordPress VIP & Enterprise Standards
- **Performance:** - No `query_posts()`. Use `WP_Query`.
  - Use the Transients API for expensive API calls or complex DB queries.
  - Avoid `file_get_contents()` on URLs; use `wp_remote_get()`.
- **Scalability:** Ensure all code is compatible with Object Caching (Redis/Memcached).

## 4. Accessibility (WCAG 2.2) & SEO
- **A11y:** Every interactive element must be keyboard-accessible. Use `aria-live` for dynamic updates. Buttons must have a 44x44px minimum hit area.
- **SEO:** Use semantic HTML5 (`<section>`, `<article>`, `<nav>`). Automatically include `Schema.org` JSON-LD for Custom Post Types.

## 5. Testing & Quality Assurance
- **Unit Testing:** Generate `PHPUnit 11+` tests for all business logic. Use `WP_Mock` to isolate tests from the database.
- **Mocking:** When writing tests, mock core WP functions to ensure speed and stability in CI/CD.
- **Markup Testing:** Use `assertEqualHTML()` (2026 standard) for testing block render outputs to avoid attribute-order failures.

## 6. Prohibited Patterns (Strict)
- NO `$_REQUEST`. Use `$_GET` or `$_POST` with nonce verification.
- NO hardcoded URLs. Use `get_template_directory_uri()` or `plugins_url()`.
- NO `style` attributes in HTML. Use CSS classes or `theme.json` settings.
- NO "AI Slop": Do not provide code without explaining the "why" behind security choices.


:hammer_and_wrench: How to use this in your IDE

For Cursor:
Create a file named .cursorrules in the root of your WordPress project.
Paste the content above into it.
The Result: Every time you ask Cursor to “Create a new plugin” or “Refactor this function,” it will automatically apply the WordPress VIP standards and Vanilla JS rules without you having to remind it.

For GitHub Copilot:
Create a file at .github/copilot-instructions.md.
Paste the content above.
When using Copilot Chat, it will now prioritize these rules as the “System Prompt” for your workspace.

Thank you!
