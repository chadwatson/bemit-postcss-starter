# BEMIT PostCSS Starter

PostCSS boilerplate with BEM, ITCSS, OOCSS, and namespaces.

## Intro

I think all of [Harry Roberts'](http://csswizardry.com) ideals about CSS are super good, so I decided to take [my BEMIT Sass Starter](https://github.com/chadwatson/bemit-sass-starter), clean it up, and make it into a nice PostCSS boilerplate.

For info on these methods:

[BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)

[ITCSS](https://www.youtube.com/watch?v=1OKZOV-iLj4&hd=1)

[OOCSS](http://www.smashingmagazine.com/2011/12/an-introduction-to-object-oriented-css-oocss/)

[BEMIT](http://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/)

[Namespacing](http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/)

## Organization

- **Settings:** Global variables, config switches

- **General:** Browser resets

- **Base:** Unclassed HTML elements

- **Objects:** Cosmetic-free UI

- **Components:** Designed chunks of UI

- **Trumps:** Helpers & overrides


## Namespacing

*This is taken straight from Harry Roberts' article on namespacing*

- **o-:** Signify that something is an Object, and that it may be used in any number of unrelated contexts to the one you can currently see it in. Making modifications to these types of class could potentially have knock-on effects in a lot of other unrelated places. Tread carefully.

- **c-:** Signify that something is a Component. This is a concrete, implementation-specific piece of UI. All of the changes you make to its styles should be detectable in the context you’re currently looking at. Modifying these styles should be safe and have no side effects.

- **u-:** Signify that this class is a Utility class. It has a very specific role (often providing only one declaration) and should not be bound onto or changed. It can be reused and is not tied to any specific piece of UI. You will probably recognise this namespace from libraries and methodologies like SUIT.

- **t-:** Signify that a class is responsible for adding a Theme to a view. It lets us know that UI Components’ current cosmetic appearance may be due to the presence of a theme.

- **s-:** Signify that a class creates a new styling context or Scope. Similar to a Theme, but not necessarily cosmetic, these should be used sparingly—they can be open to abuse and lead to poor CSS if not used wisely.

- **is-, has-:** Signify that the piece of UI in question is currently styled a certain way because of a state or condition. This stateful namespace is gorgeous, and comes from SMACSS. It tells us that the DOM currently has a temporary, optional, or short-lived style applied to it due to a certain state being invoked.

- **js-:** Signify that this piece of the DOM has some behaviour acting upon it, and that JavaScript binds onto it to provide that behaviour. If you’re not a developer working with JavaScript, leave these well alone.

- **qa-:** Signify that a QA or Test Engineering team is running an automated UI test which needs to find or bind onto these parts of the DOM. Like the JavaScript namespace, this basically just reserves hooks in the DOM for non-CSS purposes.


## Usage

Either download a zip of the repo and drop it somewhere in your project or clone the repo in your project.

```
git clone https://github.com/chadwatson/bemit-postcss-starter.git css
```

Install build packages:

```
npm install
```

Then compile with NPM from the new directory:

```
npm run build
```

This runs

```
postcss -u postcss-import -u postcss-cssnext index.css
```

and writes to stdout.

In order to write to a file, pass an option with the script:

```
npm run build -- -o style.css
```

You can easily plug this into your current NPM build scripts by adding a new script in the project's `package.json` like this:

```json
"scripts": {
  "css": "cd css & npm run build -- -o style.css" 
}
```