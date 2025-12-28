# Change: Migrate SCSS from @import to @use syntax

## Why
The Sass `@import` rule is deprecated and will be removed in future versions. Migrating to `@use` provides:
- **Modern Sass compatibility** - Ensures future-proof styling with newer Sass versions
- **Better performance** - `@use` loads each module only once, avoiding duplicate CSS output
- **Explicit namespaces** - Prevents naming conflicts between modules
- **Improved maintainability** - Better module organization and clearer dependencies

Current state: Most SCSS files already migrated, with one remaining file using legacy `@import`

## What Changes
- Replace remaining `@import` statements with `@use` syntax
- Add `as *` namespace where variables need to be globally available
- Update component-level style imports in Vue files
- Ensure all SCSS modules use consistent modern syntax

**Affected files:**
- `src/styles/element-variables.scss` - Update Element UI import to `@use`
- Verify all other `.scss` and `.vue` files use `@use`

## Impact
- **Affected specs:** styling
- **Affected code:** SCSS stylesheet files and Vue component style blocks
- **Breaking changes:** None - visual output remains identical
- **Migration effort:** Low - most files already converted, minimal changes needed
