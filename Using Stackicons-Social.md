![Doing More with Icon Fonts](http://stackicons.com/img/logo-stackicons_340x40.png)

[http://stackicons.com](http://stackicons.com)
[@stackicons](https://twitter.com/stackicons)

## Using Stackicons-Social

Stackicons-Social comes with default CSS that you can simply @import into your main CSS style sheet:

`@import url("stackicons.css");`

Or link to in the header of your html file:

`<link rel="stylesheet" type="text/css" href="css/stackicons.css" />`

Make sure the relative path to the CSS file is correct, and also that the @font-face declaration at the beginning of the CSS file has the correct relative path to the fonts.

There's also an [examples.html](http://stackicons.com/examples.html) file that you can use as a reference.

A smaller version of the font, *Stackicons-Social-Minimal,* includes a subset of commonly-used icons. Change "stackicons.css" to "stackicons-minimal.css" if you don't need more than the following:

* App.net
* Codepen
* Dribbble
* Email
* Facebook
* Flickr
* Github
* Gmail
* Google+
* Instagram
* LinkedIn
* Pinboard
* Pinterest
* RSS
* Tumblr
* Twitter
* Vimeo
* YouTube
* Menu (navicon)
* Search
* Triangle-down

### Markup

The default CSS outputs a horizontal row of icons without text (text in the markup is hidden, but available to screen readers). The icons use `display: inline-block` so it's easy to position them on the left, right, or center using `text-align`.

Stackicons' default CSS renders a slightly rounded button (r1) in a single color that reflects the brand. You can override the shape by adding a class to either the parent element or the icon itself:

* .st-shape-square or .st-shape-r0
* .st-shape-rounded1 or .st-shape-r1
* .st-shape-rounded2 or .st-shape-r2
* .st-shape-rounded3 or .st-shape-r3 *(iOS 7 style)*
* .st-shape-circle or .st-shape-r4
* .st-shape-icon or .st-shape-r5

For example, you might add `class="st-shape-circle"` to brands like App.net, CodePen, Gittip, or StumbleUpon, whose logos are circular. Android, Apple, and Windows are usually informational icons rather than buttons, so you'd add  `class="st-shape-icon"`.

#### Multi-color
Stackicons are designed with a unique "multi-color" option that uses absolute positioning to stack multiple colors on top of each other (sort of like two-color or screen-printing). You can invoke it by adding `class="st-multi-color"`.

Because the button shape is solid with the icon layered on top, .st-multi-color can give you more flexibility in using text-shadows.

Stackicons stack pseudo elements, which may create an issue with clearfix methods that rely on pseudo elements (if you decide to float the icons instead of using inline-block to position horizontally).

#### Other Markup Options

If you're not comfortable using Sass (see below), you can still easily change sizing and spacing by adjusting the CSS. For example, to change the size of the icons, specify a percentage `font-size` on the parent element. To change the spacing, adjust the margin on the ` (.parent-class) a` element.

There's also a built-in class, `.nav-list`, for creating a vertical list with icons to the left of text. Usually, you'd want these to be icon-only, e.g:  `class="nav-list st-icon-only st-multi-color"`.

	CSS:
	.nav-social {
	  /* if they're on the right */
	  text-align: right;
	  /* adjust icons larger or smaller */
	  font-size: 110%; }

	.nav-social a {
	  /* closer spacing */
	  margin-right: -.125em }

	HTML:
	<nav class="nav-social st-multi-color">
	  <ul>
	    <li><a class="st-icon-twitter" href="#">Twitter</a></li>
	    <li><a class="st-icon-facebook" href="#">Facebook</a></li>
	  </ul>
	</nav>

You can also look at the source in the [examples](http://stackicons.com/examples.html) file.

### Customizing With Sass

There is a folder of .scss _partial files that Sass compiles to create the CSS for Stackicons-Social. If you have Sass installed and are comfortable using it to compile CSS, you can adjust a number of variables within these files to adjust the default output.

Start with the two "kit" files:  *_construction-kit-stackicons-social.scss* and *multi-color-kit-stackicons-social.scss*. Here you can change things like the default button shape, colors, :hover behavior, and more.

There are some pre-made "color-style" options: For example, the default output uses the brand color for each button and a lighter variant for the :hover state. You could choose to reverse that, having a pale version of the brand color by default with the brand color on :hover. You could also change the @mixin to make the variant color darker instead of lighter.

With single-color buttons there are four "color-style" options available:

**single-color**
:	All icons are the same color.

**brand-color**
:	Each icon reflects the brand color (defined by variable).

**brand-variant**
:	Each icon reflects the brand color altered by a @mixin that scales the color lighter or darker, changes the saturation, and transparentizes based on variables you can tweak.

**embossed-only**
:	All icons are a darkened background-color, with text-shadow embossing.

Then there are three choices to pair with for the :hover state:

**single-color-hover**
:	All buttons or icons are the same color on :hover.

**brand-color**
:	Each button or icon reflects the brand color on :hover.

**brand-color-hover**
:	Each button or icon reflects the brand color altered by a @mixin that scales the color lighter or darker, changes the saturation, and transparentizes based on variables you can tweak.

There are additional variables related to text-shadows, transitions, and more. The comments within the Sass files provide more information. There's no limit to how you can choose to customize, of course. I just included some pre-made options for convenience.

The other Sass files contain variables for brand color, which you can tweak, and there are files that do the grunt work of generating CSS for each brand. Here's a brief description of each (it's a good idea to make a backup copy before customizing these files):

**fonts-stackicons-social**
:	Path to stackicons-social font. (Make sure it's correct for your directories.)

**colors-social-2014**
:	Color variables for social brands. (Tweak as desired.)

**unicodes-stackicons-social**
:	Font unicode characters abstracted into variables. (Don't change this.)

**construction-kit-stackicons-social**
:	This is where we generate default values for icon size, margin, padding, shape, color, hover-style, etc. (Play here.)

**css-defaults-stackicons-social**
:	This does the CSS grunt work to create each .st-icon-($brand) class.\*

**override-button-shapes-stackicons-social**
:	 Let's you override the button shape on single-color icons using classes: st-shape-square to st-shape-circle.\*

**override-icon-only-stackicons-social**
:	 Allows .st-shape-icon to overrides the default button shape.\*

**override-colors-stackicons-social**
:	"Color-style" classes for single-color icons for demo purposes. This generates lots of extra CSS, so it's commented out by default.\*

**multi-color-kit-stackicons-social.scss**
:	Like "construction-kit" above, but for the .st-multi-color class: generates default shape, color-style, etc. (Play here.)

**multi-color-css-stackicons-social.scss**
:	Like "css-defaults" above, this does the CSS grunt work to generate each multi-color .st-icon-($brand) class.\*

**multi-color-override-shapes-stackicons-social**
:	This allows you to change icon shapes using classes on multi-color icons.\*

\* Because Sass doesn't allow us to use variables within variables, this uses a lot of @if statements to generate the .st-icon-($brand) classes. Ugly, but marginally maintainable. There are several @each statements, listing the brands to output. Ideally, you would go through and edit these lists to limit the CSS output to only the brands you need.

For now, the "multi-color" icons need to be invoked with a separate ".st-multi-color" class. I'm planning to make it an option for default output in the future. If you'd like to be notified of updates, and receive occasional info or offers, head over to <http://stackicons.com/subscribe>.

#### Contribute

Stackicons-Social is open source and free for any use. Attribution is welcome but not required.

If you (or a client) are able to contribute to the project, it would be a big help. As a small token of thanks, I'll send you *Stackicons-Social-Complete,* with a few more of my own custom icons. [Click here to donate any amount, thanks] (https://spb.io/AY3rLlt5aG).

If you have any questions, or are interested in creating a custom icon font for your project, please get in touch:

Parker Bennett

<parker@stackicons.com>

[@parkerbennett](https://twitter.com/parkerbennett)
[@stackicons](https://twitter.com/stackicons)
