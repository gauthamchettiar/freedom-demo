---
applyTo: 'themes/freedom/**'
---
## Core Development Principles

### Minimal Implementation Philosophy
- Always implement the most concise and minimal Go template, HTML, CSS, and JavaScript code
- Avoid over-engineering solutions - simpler is better
- Use Hugo's built-in functions and features before creating custom implementations
- Remove any unnecessary abstraction layers or redundant code

### Iterative Review Process
- After implementing any feature, review the code at least once to verify it's the most concise approach
- Ask yourself: "Can this be simplified further while maintaining functionality?"
- Check for redundant template logic, duplicate CSS rules, or unnecessary JavaScript
- Consolidate similar patterns into reusable partials only when there's clear duplication

## Hugo Version Awareness

### Current Version: Hugo v0.151.x (as of 2025)
Hugo templating rules and features have evolved significantly. Before implementing any feature:

1. **Always fetch and reference official Hugo documentation** for:
   - Template syntax and functions
   - Module system and configuration
   - Asset pipeline (Hugo Pipes)
   - Content management features
   - Markdown rendering options

2. **Recent Breaking Changes to Consider**:
   - Link and image render hooks now use enums for enablement
   - Template selection honors implicit "page" type
   - Module imports support direct version specifications in `hugo.yaml`
   - CSS minification targets CSS3 (not CSS2)
   - TOC rendering has been improved with sanitization and Goldmark Extras support

3. **Reference Documentation URLs**:
   - Official docs: https://gohugo.io/documentation/
   - Template functions: https://gohugo.io/functions/
   - Variables: https://gohugo.io/variables/
   - Configuration: https://gohugo.io/getting-started/configuration/

## Implementation Workflow

### Step 1: Project Structure Analysis (First Question Only)
When asked the first question in a session:
1. Examine the entire project structure
2. Identify the theme directory layout (`layouts/`, `assets/`, `static/`, etc.)
3. Review existing partials and templates to understand conventions
4. Check `hugo.yaml` configuration file for configuration patterns
5. Note any custom shortcodes or content adapters in use
6. Understand the asset pipeline setup (SCSS, PostCSS, JS bundling)

### Step 2: Planning Before Implementation
Before touching any code, provide a complete plan that includes:

1. **Goal**: What feature or change is being implemented
2. **Files to modify/create**: List exact file paths
3. **Approach**: High-level explanation of the implementation strategy
4. **Hugo features utilized**: Which built-in functions, variables, or patterns will be used
5. **Potential gotchas**: Any known issues or considerations
6. **Testing approach**: How to verify the implementation works

Example plan format:
#### Plan: Implement Article Card Component
Goal : Create a reusable article card partial for homepage and archive pages
Files :
- layouts/partials/article-card.html (new)
- assets/css/components/card.css (new)
- layouts/index.html (modify)

Approach :
- Use Hugo's .Summary and .ReadingTime for article metadata
- Leverage CSS Grid for responsive layout
- Implement with semantic HTML5 elements

Hugo Features :
- .Permalink, .Title, .Summary, .ReadingTime
- partial function for reusability
- resources.Get for CSS processing

Considerations : 
- Ensure .Summary respects manual summary split (<!--more-->)
- Handle missing featured images gracefully
- Maintain accessibility with proper ARIA labels

Testing :
- Verify card renders on homepage with hugo server
- Test responsive breakpoints
- Check with and without featured images


### Example: Card Layout Implementation
When implementing a card-based post layout (for `listType: "card"`), follow this pattern:

**Template** (`layouts/_partials/widgets/posts/style/card.html`):
```go-html-template
{{ $page := . }}

{{ with $page }}
    {{ $dateMachine := .Date | time.Format "2006-01-02T15:04:05-07:00" }}
    {{ $dateHuman := .Date | time.Format "Jan 2, 2006" }}
    <li>
        <article class="card">
            <a href="{{ .RelPermalink }}">
                <h3 class="card-title">{{ .LinkTitle }}</h3>
                <time class="card-date" datetime="{{ $dateMachine }}">{{ $dateHuman }}</time>
                {{ with .Summary }}
                    <p class="card-summary">{{ . }}</p>
                {{ end }}
            </a>
        </article>
    </li>
{{ end }}
```

**CSS** (`assets/css/widgets/posts.css`):
```css
.fr-posts-card .card {
    border: 1px solid color-mix(in srgb, var(--color-text) 20%, transparent);
    border-radius: var(--spacing-xs);
    padding: var(--spacing-md);
    margin-bottom: var(--spacing-md);
    transition: all 0.3s ease;
}

.fr-posts-card .card:hover {
    border-color: var(--color-link);
    box-shadow: 0 var(--spacing-xs) var(--spacing-md) 
                color-mix(in srgb, var(--color-text) 10%, transparent);
}
```

Key points:
- Semantic HTML with `<article>`, `<h3>`, and `<time>` elements
- Accessible datetime attributes on time elements
- Graceful handling of optional summary with `{{ with .Summary }}`
- Modern CSS with custom properties and color-mix()
- Hover effects for better UX
- All URLs use `.RelPermalink` (never hardcoded)


## Best Practices

### Go Template Guidelines
- Use `.Scratch` sparingly; prefer template variables with `:=`
- Leverage `with` blocks to check for existence and scope context
- Use `range` with `else` for empty collection handling
- Prefer `partialCached` for expensive, reusable computations
- Use `site.Params` for global configuration values
- Follow Go template syntax: `{{ .Variable }}` for output, `{{- -}}` for whitespace control

### HTML Best Practices
- Use semantic HTML5 elements (`<article>`, `<section>`, `<nav>`, `<aside>`, etc.)
- Include proper accessibility attributes (ARIA labels, alt text, roles)
- Maintain a logical heading hierarchy (h1 → h2 → h3)
- Use microdata or JSON-LD for structured data when appropriate
- Ensure forms have proper labels and validation attributes

### CSS Guidelines
- Use modern CSS features (Grid, Flexbox, Custom Properties)
- Implement mobile-first responsive design
- Leverage CSS custom properties for theming
- Keep specificity low; avoid deep nesting
- Use BEM or similar naming convention for clarity
- Prefer CSS over JavaScript for animations and transitions
- Utilize Hugo Pipes for SCSS/PostCSS processing

### JavaScript Guidelines
- Use vanilla JavaScript; avoid frameworks unless absolutely necessary
- Implement progressive enhancement (site works without JS)
- Use modern ES6+ features (const/let, arrow functions, template literals)
- Defer or async load scripts to optimize page load
- Use Hugo's `js.Build` for bundling and minification
- Keep JavaScript minimal and focused on genuine interactivity

## Canonical Implementation Policy

### When to Say No
If a requested feature cannot be implemented in a canonical, standard way:
1. **Do not implement hacky workarounds** or brittle solutions
2. **Explain why** the canonical approach isn't possible
3. **Suggest alternatives** that align with Hugo's architecture
4. **Document limitations** clearly

Examples of what to avoid:
- Parsing HTML output with regex to modify content
- Overriding Hugo's internal behavior with complex workarounds
- Using JavaScript to compensate for architectural issues
- Implementing features that should be handled by Hugo configuration

### Canonical Alternatives
Instead of hacky solutions:
- Suggest proper Hugo Modules for shared functionality
- Recommend content adapters for dynamic content
- Use shortcodes for complex content patterns
- Leverage Hugo's built-in template lookup order
- Implement custom output formats for special needs

### Partial Parameters
When creating partials, use `.` context or explicit parameters:
```go-html-template
{{/* Good: Explicit parameters */}}
{{ partial "card.html" (dict "title" .Title "url" .Permalink) }}

{{/* Good: Pass entire page context */}}
{{ partial "article-meta.html" . }}

{{/* Avoid: Relying on global context implicitly */}}
```

## Testing and Validation
### Pre-Implementation Checks
- Verify Hugo version compatibility
- Check if built-in function exists before creating custom solution
- Review official documentation for similar examples
- Consider performance implications (build time, runtime)

### Post-Implementation Validation
- Test with hugo server --disableFastRender for accurate builds
- Verify HTML validity (W3C validator)
- Check accessibility (aXe, Lighthouse)
- Test responsive design at multiple breakpoints
- Validate with real content (not just Lorem Ipsum)
- Check build performance with hugo --templateMetrics

### Common Pitfalls to Avoid
- Don't use deprecated functions - Check Hugo release notes
- Avoid inline styles and scripts - Use asset pipeline
- Don't hardcode URLs - Use .RelPermalink, .Permalink, absURL, relURL
- Avoid language-specific assumptions - Support i18n from the start
- Don't ignore errors - Use with, if, and error checking
- Avoid duplicating Hugo's features - Use built-ins first

## Documentation
### Code Comments
- Document complex template logic
- Explain why, not what (code shows what)
- Include Hugo function references in comments
- Note any workarounds with explanation

### Component Documentation
For each reusable partial, document:
- Purpose and usage
- Required parameters
- Optional parameters with defaults
- Example usage
- Dependencies (if any)

Example:
```text
{{/*
  Article Card Component
  
  Displays a summary card for an article with optional featured image.
  
  Parameters:
    - page (Page): Hugo page object (required)
    - showImage (bool): Display featured image if available (default: true)
    - showExcerpt (bool): Display article summary (default: true)
  
  Usage:
    {{ partial "article-card.html" (dict "page" . "showImage" true) }}
*/}}
```

## Performance Considerations

- Use partialCached for static content
- Minimize template complexity to reduce build time
- Lazy load images with native loading="lazy"
- Implement critical CSS inlining for above-the-fold content
- Use Hugo's image processing for responsive images
- Minimize HTTP requests with bundling and sprites

## Version Control

- Commit related changes together (template + CSS + JS)
- Write clear commit messages following conventional commits
- Keep theme separate from content when possible
- Document breaking changes in CHANGELOG
