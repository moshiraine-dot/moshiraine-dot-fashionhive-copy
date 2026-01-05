# FashionHive — Component Spec (React)

Tone: modern, confident, approachable  
Primary tech: React (JSX). Use PropTypes or TypeScript types as preferred. Accessibility and keyboard support required for all interactive components.

---

## Component: Navbar
Props:
- navItems: Array<{ label: string, url: string, children?: navItems[] }>
- logoUrl: string
- user?: { name?: string, avatarUrl?: string }
- cartCount: number
- onSearch?: (query: string) => void

Variants:
- desktop (full links)
- mobile (hamburger + drawer)

Accessibility:
- Hamburger button: aria-expanded, aria-controls
- Skip to content link at top

Example usage (JSX):
```jsx
<Navbar
  navItems={[{label:'Men', url:'/men'},{label:'Women', url:'/women'}]}
  logoUrl="/assets/logo.svg"
  cartCount={2}
/>
