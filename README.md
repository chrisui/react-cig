# Component Interoperability Guidelines
Community-driven guidelines to provide unity, consistency and sanity within the React 3rd-party component ecosystem.

> ### Foreword
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
> - **These guidelines are *not* a static gospel preached by one or a few people.**
>   - They will continue to evolve and be developed by the community - individual guidelines have the freedom to become as loose or as verbose as the use-case requires. They will naturally progress in the same fashion to how the components they help guide progress.
> - **These guidelines are *not* strict, over-complex and in-depth on how to write your code or build your individual components.**
>   - They are purely concerned with providing very thin, very high-level interoperability guidelines for how to publicly expose and provide for consumers. These minimal abstractions will allow for easy creation of middleware so consumers can write their applications how they like (a good example of this is the vast array of methods to style applications and no cohesion on styling 3rd-party components).

## Sections
1. [Basic Component Structure](#basic-component-structure)
2. [Styling Components](#styling-components)

### Basic Component Structure
Covers what is expected when exposing your top-level components

TBC - use of propTypes, doesn't have side effects etc.

### Styling Components
TBC - classmap/stylemap etc.

#### As an author...

Components can opt in to allowing external styling by accepting `classmap` and `stylemap` props. Both should be accepted together to allow consumers to use the styling system of their preference and also to allow the use of both together where needed (ie. js computed styles + classes).

```javascript
propTypes = {
  classmap: React.PropTypes.object,
  stylemap: React.PropTypes.object
}
```

Each one of these props is a simple object map of programmer friendly keys (targets) to their values. It is up to the author to define and document the expected keys. Targets should have identical keys in each object if both are expected.

In the case of a `classmap` the object would resemble a friendly key to a "classname value" map. Note this "classname value" can be any type which would be accepted by the [classnames](https://github.com/JedWatson/classnames) merge function.

> TBC???: And how they are merged together - ie think of the button example below - does (SHOULD???) the author state that `classmap.button` and `classmap.buttonAlt` get merged together or should the classmap have already defined that - ie. `buttonAlt: 'btn btn--alt'` - Seems there might be some consistency needed here? I don't know. Might be nice to have something consistent here as it makes consumption more familiar and makes less "what on earth is expected here?" moments while authoring. Would also be good to have symmetrical behaviour to classmap and stylemap (so what's the best direction for that?)

```jaavscript
const classmap = {
  button: 'btn',
  buttonAlt: 'btn--alt
};
```

In the case of a `stylemap` the object would resemble a friendly key to a "style object". Note this "style object" is the value you pass to any dom element as the `style` prop.

```jaavscript
const stylemap = {
  button: {padding: '10px, 5px', color: 'white', background: 'blue'},
  buttonAlt: {background: 'darkblue'}
};
```

These props are the highest level api the consumer will be faced with.

Now that you, as the author, have access to these maps you can use them to style the your core components and their sub components. It is also recommended that there should be defaults.

>TBC???: There are many options available for author tools to consume these props so that's next

##### Possible author helper

```javascript
const {classmap, stylemap} = this.props;

<button {...style(classmap.btn, stylemap.btn)} />
```

```javascript
// Use of the above HoC passes special `styles` prop (an object) with above helper performed on each key/val of maps passed in by consumer - As a bonus you could have static defaults passed here too
styleHigherOrderComponent(MyComponent, staticDefaultClassmap, staticDefaultStylemap);
const {styles} = this.props;

<button {...styles.btn} />
```

#### As a consumer...

As a consumer of these guideline compliant components you are simply expected to pass through one of the (or both if needed) above-defined props.

> TBC???: Probably best to have consumer usage above author usage in the flow of these docs...

```javascript
<Button classmap={classmap} stylemap={stylemap} />
```

This allows you, as a consumer, to use your own styling system and pass in common formats as props to the 3rd-party component.

#####  Possible consumer helper

`<Button {...style(classmap, stylemap)} />`
