# Component Interoperability Guidelines
Community-driven guidelines to provide unity & consistency within the React 3rd-party component ecosystem.

### Foreward
TBC

### Aims of these guidelines
To help and guide (but not restrict) developers to...

- Increase portability of components
- Simplify and speed developer consumption (ie. consistent api's)
- Provide familiar routes to controlling component behaviours (ie. avoid black-boxing components)

### Guidelines
1. Basic Component Structure
2. Styling Components

## Basic Component Structure
Covers what is expected when exposing your top-level components

TBC - use of propTypes, doesn't have side effects etc.

## Styling Components
TBC - classmap/stylemap etc.

`<Button classmap={{}} stylemap={{}} />`

Possible consumer helper

`<Button {...style({}, {})} />`

Possible author helper

`<button {...style(classmap.btn, stylemap.btn)} />`
