GwtBootstrap3 is a GWT wrapper for Twitter's Bootstrap library version 3
containing design templates, styles and beautiful widgets.

Have a look at the [demo]().

**Note:** This library is **not** feature complete as it contains only the
widgets / functionality that I needed for another project of mine. Also
since Bootstrap 3 is still a release candidate API is likely to change.
Patches / pull requests are welcome. See *Feature matrix* below.

# Usage

Add the dependency to your Maven POM:

```xml
<dependency>
    <groupId>com.svenjacobs.gwtbootstrap3</groupId>
    <artifactId>gwtbootstrap3</artifactId>
    <version>0.1-SNAPSHOT</version>
    <scope>provided</scope>
</dependency>
```

Inherit the GwtBootstrap3 module in your GWT module:

```xml
<module>
    <inherits name='com.svenjacobs.gwtbootstrap3.GwtBootstrap3'/>
    ...
</module>
```

Make sure to not inherit GWT's default styles or any other styles because
Bootstrap brings its own styles which are provided by the GwtBootstrap3 module.

Use the widgets in your UiBinder XML:

```xml
<ui:UiBinder xmlns:ui='urn:ui:com.google.gwt.uibinder'
             xmlns:g='urn:import:com.google.gwt.user.client.ui'
             xmlns:b='urn:import:com.svenjacobs.gwtbootstrap3.client.ui'>

    <b:Container>
        <b:PageHeader>Yay buttons!</b:PageHeader>

        <b:Button>Some button</b:Button>
        <b:Button type='DANGER' size='LARGE'>Dangerous button</b:Button>
    </b:Container>

</ui:UiBinder>
```

or create them in code if that's what you prefer.

**Tip:** GwtBootstrap3's styles and widgets, especially the fluid grid system,
work best when using the "classic" [panels](http://www.gwtproject.org/doc/latest/DevGuideUiPanels.html)
throughout your application and **not** the absolut positioned layout panels
introduced in GWT 2.0.

# Feature matrix

Following Bootstrap features are natively supported by GwtBootstrap3 through
widgets. Other Bootstrap features **still can be used** with plain HTML and
JavaScript, see Bootstrap's [documentation](http://getbootstrap.com/).

## CSS

| Feature     | Status              |
|-------------|---------------------|
| Glyphicons  | Not supported       |
| Grid system | Supported           |
| Typography  | Partially supported |
| Code        | Supported           |
| Tables      | Not supported       |
| Forms       | Partially supported |
| Buttons     | Supported           |
| Images      | Not supported       |

## Components

| Feature                             | Status              |
|-------------------------------------|---------------------|
| Dropdowns                           | Supported           |
| Button groups                       | Supported           |
| Button dropdowns                    | Supported           |
| Input groups                        | Partially supported |
| Navs                                | Supported           |
| Navbar                              | Supported           |
| Breadcrumbs                         | Not supported       |
| Pagination                          | Not supported       |
| Labels                              | Supported           |
| Badges                              | Supported           |
| Typography (Jumbotron, Page header) | Supported           |
| Thumbnails                          | Not supported       |
| Alerts                              | Supported           |
| Progress bars                       | Not supported       |
| Media object                        | Not supported       |
| List group                          | Not supported       |
| Panels                              | Not supported       |
| Wells                               | Supported           |

## JavaScript

| Feature     | Status        |
|-------------|---------------|
| Transitions | Not supported |
| Modal       | Supported     |
| Dropdown    | Supported     |
| Scrollspy   | Supported     |
| Tab         | Not supported |
| Tooltip     | Not supported |
| Popover     | Not supported |
| Alert       | Supported     |
| Button      | Supported     |
| Collapse    | Not supported |
| Carousel    | Not supported |
| Affix       | Supported     |

# Relationship between raw Bootstrap components and GWT widgets 

GwtBootstrap's widgets are designed to mimick the HTML structure of Bootstrap UI
elements as best as possible while not introducing another layer of abstraction.
While this might result in a bit more typing it also offers greater flexibility
and reusability of components. Thus it should be relatively easy to translate
Bootstrap's [HTML code](http://getbootstrap.com/components/) into UiBinder XML.

For example a button dropdown is implemented in UiBinder XML like:

```xml
<b:ButtonGroup>
    <b:Button toggle="DROPDOWN">Test</b:Button>
    <b:DropDownMenu>
        <b:ListItem>Item 1</b:ListItem>
        <b:ListItem>Item 2</b:ListItem>
        <b:ListItem>Item 3</b:ListItem>
        <b:Divider/>
        <b:ListItem>Item 4</b:ListItem>
    </b:DropDownMenu>
</b:ButtonGroup>
```

Compare this to the HTML version:

```html
<div class="btn-group">
    <button type="button" class="btn btn-default dropdown-toggle" data-toggle="dropdown">
        Test <span class="caret"></span>
    </button>
    <ul class="dropdown-menu">
        <li><a href="#">Item 1</a></li>
        <li><a href="#">Item 2</a></li>
        <li><a href="#">Item 3</a></li>
        <li class="divider"></li>
        <li><a href="#">Item 4</a></li>
    </ul>
</div>
```