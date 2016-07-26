# Jekyll Dynamic Menu

> A Liquid snippet to generate markup for a dynamic navigation menu

From this:

```
.
├── components/
|   ├── Button.md
|   ├── index.md
|   ├── Heading.md
|   └── Footer.md
├── global/
|   ├── other/
|   |   ├── index.md
|   |   └── reset.md
|   ├── Colours.md
|   ├── index.md
|   └── Utils.md
└── index.md
```

To this:

```html
<ul data-menu-depth="0">
  <li>
    <a href="/components">Components</a>
    <ul>
      <li><a href="/components/button.html">Button</a></li>
      <li><a href="/components/heading.html">Heading</a></li>
      <li><a href="/components/footer.html">Footer</a></li>
    </ul>
  </li>
  <li>
    <a href="/global">Global</a>
    <ul data-menu-depth="1">
      <li><a href="/components/colours.html">Colours</a></li>
      <li>
        <a href="/components/other.html">Other</a>
        <ul data-menu-depth="2">
          <li><a href="/components/other/reset.html">Reset</a></li>
        </ul>
      </li>
      <li><a href="/components/utils.html">Utils</a></li>
    </ul>
  </li>
```

# How to use

1. Place `generateDynamicMenu.html` in your `_ includes` folder.

2. Make sure all the folders have an index file (e.g. `index.md`). If there is a `title` property in the front-matter, this will be used as the name of the level.

3. To generate a menu using `/components` as the root directory, include the partial with:

   ```
   {% include generateDynamicMenu.html root="/components" %}
   ````
   
# Parameters

| Parameter | Description | Required |
|---|---|---|---|---|
| `root` | Root directory. Any directories above it will not be included.  | **yes** |
| `listClass`  | Class(es) to be included in the `<ul>` elements | no |
| `listItemClass`  | Class(es) to be included in the `<li>` elements |  no  |
| `linkClass`  | Class(es) to be included in the `<a>` elements |  no  |
| `activeClass`  | Class(es) to be included in the `<a>` element that corresponds to the current active page |  no  |
| `depthAttr`  | Name of the data attribute to include in `<ul>` elements with information about depth (defaults to `data-menu-depth` |  no  |
