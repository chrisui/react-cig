# Component Interoperability Guidelines
Community-driven guidelines to provide unity, consistency and sanity within the React 3rd-party component ecosystem.

> ### Foreward
> TBC
> 
> ### Aims of these guidelines
> To help and guide (but not restrict) developers to...
> 
> - Increase portability of components
> - Simplify and speed developer consumption (ie. consistent api's)
> - Provide familiar routes to controlling component behaviours (ie. avoid black-boxing components)
> - Make 80% easy, 20% possible
>
> ### What these guidelines are *not*
> - These guidelines are *not* a static gospel preached by one or a few people. They will continue to evolve and be developed by the community - individual guidelines have the freedom to become as loose or as verbose as the use-case requires. They will naturally progress in the same way that the components they help guide progress.
> - These guidelines are *not* strict, over-complex and in-depth on how to write your code or build your individual components. They are purely concerned with providing very thin, very high-level interoperability guidelines for how to publicly expose and provide for consumers.

## Sections
1. [Basic Component Structure](#basic-component-structure)
2. [Styling Components](#styling-components)

### Basic Component Structure
Covers what is expected when exposing your top-level components

TBC - use of propTypes, doesn't have side effects etc.

### Styling Components
TBC - classmap/stylemap etc.

`<Button classmap={{}} stylemap={{}} />`

Possible consumer helper

`<Button {...style({}, {})} />`

Possible author helper

`<button {...style(classmap.btn, stylemap.btn)} />`
