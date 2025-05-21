# Problem:
AstroJS adds `<style>` script inside body when any Preact component is rendered with `client` directive not on the top level (inside astro component, eg. inside Layout)  

This causes HTML validation error:  
<img width="668" alt="Screenshot 2025-05-21 at 11 34 14" src="https://github.com/user-attachments/assets/28abfa19-4aec-423a-9efd-1e1eb3025efc" />

## Setup
Using Preact and standard `create astro` project
There is the [simpliest example](https://github.com/AnaMoskvina/astrojs-test/tree/main) with [Layout](https://github.com/AnaMoskvina/astrojs-test/blob/main/src/layouts/Layout.astro) and [Component](https://github.com/AnaMoskvina/astrojs-test/blob/main/src/components/test.jsx)

## Screenshots
When Test component (client:load) is rendered inside the Layout as slot - `<style>` is added to `<body>` (same happens when Preact component is redered inside astro component *not* as a slot)
<img width="668" alt="Screenshot 2025-05-20 at 19 52 46" src="https://github.com/user-attachments/assets/9fb8081e-8288-4d35-94ff-01ef2d5b7dc9" />


When Test component (client:load) is rendered outside the Layout
<img width="668" alt="Screenshot 2025-05-20 at 19 53 32" src="https://github.com/user-attachments/assets/872d5516-bfa4-4284-8c41-0aa3fffe8858" />

## Questions:
1. Is this issue is going to be solved?
2. Is there's a a way to make `<style>astro-island,astro-slot,astro-static-slot{display:contents}</style>` be added to `<head>`, not to the `<body>`?
3. Are components with client directive supposed to be rendered in astro components and layouts in general?
