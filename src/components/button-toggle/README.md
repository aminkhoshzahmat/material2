# md-button-toggle

`MdButtonToggle` is a group of buttons that can be toggled.
There are two modes, `multiple` and `exclusive`.
When in 'exclusive' mode, only one button can be selected at a time (like radio buttons).
When in 'multiple' mode, multiple buttons can be selected at once (like checkboxes).
You can read more about button toggles in the
[Material Design spec](https://material.google.com/components/buttons.html#buttons-toggle-buttons).

## Usage

### Setup

Importing the symbols:
```ts
import { MdUniqueSelectionDispatcher } from '@angular2-material/core';
import { MD_BUTTON_TOGGLE_DIRECTIVES } from '@angular2-material/button-toggle'
```

Adding providers and directives:
```ts
@Component({
  ...
  directives: [MD_BUTTON_TOGGLE_DIRECTIVES],
  providers: [MdUniqueSelectionDispatcher]
})
```

### Basic Usage

`md-button-toggle` can be used on its own and acts as a checkbox.

```html
<md-button-toggle>Bold</md-button-toggle>
```

Output:

![Basic Toggle Button Example](https://material.angularjs.org/material2_assets/button-toggle/basic-toggle.png)

### Exclusive Selection

`md-button-toggle` can be used in an exclusive selection group when surrounded by
`md-button-toggle-group`. This styles all buttons within the group to appear as a single
group of button toggles and allows only one button toggle to be selected at a time.

```html
<md-button-toggle-group name="alignment">
    <md-button-toggle value="left"><md-icon>format_align_left</md-icon></md-button-toggle>
    <md-button-toggle value="center"><md-icon>format_align_center</md-icon></md-button-toggle>
    <md-button-toggle value="right"><md-icon>format_align_right</md-icon></md-button-toggle>
    <md-button-toggle value="justify"><md-icon>format_align_justify</md-icon></md-button-toggle>
</md-button-toggle-group>
```

Output:

![Exclusive Toggle Button Example](https://material.angularjs.org/material2_assets/button-toggle/exclusive-toggle.png)

### Multiple Selection

`md-button-toggle` can be used in a multiple selection group when surrounded by
`md-button-toggle-group multiple`. This styles all buttons within the group to appear as a single
group of button toggles.

```html
<md-button-toggle-group multiple>
    <md-button-toggle>Flour</md-button-toggle>
    <md-button-toggle>Eggs</md-button-toggle>
    <md-button-toggle>Sugar</md-button-toggle>
    <md-button-toggle>Milk</md-button-toggle>
</md-button-toggle-group>
```

Output:

![Multiple Toggle Button Example](https://material.angularjs.org/material2_assets/button-toggle/multi-toggle.png)

## Dynamic Exclusive Selection

`md-button-toggle`s can be used with `ngModel` to dynamically create groups and update the value for
a group.

```html
<md-button-toggle-group name="pies" [(ngModel)]="favoritePie">
    <md-button-toggle *ngFor="let pie of pieOptions" [value]="pie">
        {{pie}}
    </md-button-toggle>
</md-button-toggle-group>
<p>Your favorite type of pie is: {{favoritePie}}</p>
```

### Disabled Button Toggle

`md-button-toggle-group` and `md-button-toggle` can both be disabled by adding a `disabled`
attribute to either one. Adding `disabled` to an exclusive group or a multiple group will disable
the entire group. Adding `disabled` to a single toggle will disable that toggle.

```html
<md-button-toggle-group disabled>
    <md-button-toggle value="one">One</md-button-toggle>
    <md-button-toggle value="two">Two</md-button-toggle>
    <md-button-toggle value="three">Three</md-button-toggle>
</md-button-toggle-group>

<md-button-toggle-group>
    <md-button-toggle value="red" disabled>Red</md-button-toggle>
    <md-button-toggle value="blue">Blue</md-button-toggle>
</md-button-toggle-group>
```

Output:

![Disabled Toggle Buttons Example](https://material.angularjs.org/material2_assets/button-toggle/disabled-toggles.png)

## `<md-button-toggle>`

### Bound Properties

| Name | Type | Description |
| --- | --- | --- |
| `id` | string | The unique ID of the toggle. IDs are generated by default when not specified. |
| `name` | string | Optional, defaults to parent group name if one exists for exclusive selection toggles, otherwise null. This is used to differentiate between different groups. |
| `value` | any | Value of the toggle. Only used when in a group to determine which are selected. |
| `checked` | boolean | Optional, default = `false`. Whether or not the toggle is checked. |
| `disabled` | boolean | Optional, default = `false`. Whether or not the toggle is disabled |

### Events

| Name | Description |
| --- | --- |
| `change` | Emitted when the `checked` value is changed. |

## `<md-button-toggle-group>`

### Bound Properties

| Name | Type | Description |
| --- | --- | --- |
| `name` | string | Optional, the name of the group. |
| `disabled` | boolean | Optional, default = `false`. |
| `value` | any | The current value for the group. Will be set to the value of the selected toggle or a list of values from the selected toggles. |
| `selected` | `mdButtonToggle` | The current selected toggle or a list of the selected toggles. |

### Attributes

| Name | Type | Description |
| --- | --- | --- |
| `multiple` | boolean | Optional, default = `false`. Whether or not the group allows multiple selection. |

### Events

| Name | Description |
| --- | --- |
| `change` | Emitted when the `value` of the group changes. |
