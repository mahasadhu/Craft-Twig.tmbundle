# Craft Twig

A Craft CMS influenced Twig bundle for Sublime Text and Textmate, customized to work with Craft CMS specific Twig extensions.

[![Craft-Twig Demo Video][image-1]][1]

## Features

Craft Twig provides syntax highlighting for Craft templates, several snippets available via tab trigger, a couple key bindings, and comment support.

### Twig Tags (via key bindings)

	ctrl+shift+[      {{  }}
	ctrl+shift+5      {%  %}
	command + /       {#  #}

### Twig Tags (via tab trigger)

	}}                {{  }}
	%%                {%  %}
	##                {#  #}
	
	do                {% do ... %}
	extends           {% extends "template" %}
	from              {% from "template" import "macro" %}
	import            {% import "template" as name %}
	importself        {% import _self as name %}
	inc, include      {% include "template" %}
	incp              {% include "template" with params %}
	inckv             {% include "template" with { key: value } %}
	use               {% use "template" %}
	
	autoescape        {% autoescape "type" %}...{% endautoescape %}
	block, blockb     {% block name %} ... {% endblock %}
	blockf            {{ block("...") }}
	embed             {% embed "template" %}...{% endembed %}
	filter, filterb   {% filter name %} ... {% endfilter %}
	macro             {% macro name(params) %}...{% endmacro %}
	set, setb         {% set var = value %}
	spaceless         {% spaceless %}...{% endspaceless %}
	verbatim          {% verbatim %}...{% endverbatim %}
	
	if, ifb           {% if condition %} ... {% endif %}
	ife               {% if condition %} ... {% else %} ... {% endif %}
	for               {% for item in seq %} ... {% endfor %}
	fore              {% for item in seq %} ... {% else %} ... {% endfor %}
	
	else              {% else %}
	endif             {% endif %}
	endfor            {% endfor %}
	endset            {% endset %}
	endblock          {% endblock %}
	endfilter         {% endfilter %}
	endautoescape     {% endautoescape %}
	endembed          {% endembed %}
	endfilter         {% endfilter %}
	endmacro          {% endmacro %}
	endspaceless      {% endspaceless %}
	endverbatim       {% endverbatim %}

### Twig Tags, Customized for Craft (via tab trigger)

	The following tab triggers output a simple example of a loop for their respective Craft tags.
	
	asset                    craft.assets.one()
	assets                   craft.assets loop
	categories               craft.categories loop
	entries                  craft.entries loop
	feed                     craft.feeds.getFeedItems loop
	tags                     craft.tags loop
	users                    craft.users loop
	
	cache                    {% cache %}...{% endcache %}
	children                 {% children %}
	exit                     {% exit 404 %}
	header                   {% header "HEADER" %}
	hook                     {% hook "name" %}
	ifchildren               {% ifchildren %}...{% endifchildren %}
	matrix, matrixif         Basic Matrix field loop using if statements
	matrixifelse             Basic Matrix field loop using if/elseif
	matrixswitch             Basic Matrix field loop using switch
	nav                      {% nav item in items %}...{% endnav %}
	paginate                 Outputs example of pagination and prev/next links
	redirect                 {% redirect "login" %}
	redirectinput            {{ redirectInput("url") }}
	requirelogin             {% requireLogin %}
	requirepermission        {% requirePermission "spendTheNight" %}
	switch                   {% switch variable %}...{% endswitch %}

	// Paths
	alias                    alias("@baseUrl/images/image.png")
	svg                      svg("@webroot/assets/svgs/icon.svg")

	// CSS/JS
	css                      {% css %}...{% endcss %}
	js                       {% js %}...{% endjs %}
	registercssfile          {% do view.registerCssFile ("/resources/css/global.css") %}
	registerjsfile           {% do view.registerJsFile("/resources/js/global.js") %}

	// Output Helpers
	csrf                     {{ csrfInput() }}
	head                     {{ head() }}
	beginbody                {{ beginBody() }}
	endbody                  {{ endBody() }}
	
	// craft.app.request
	getparam                 craft.app.request.getParam()
	getbodyparam             craft.app.request.getBodyParam()
	getqueryparam            craft.app.request.getQueryParam()
	getsegment               craft.app.request.getSegment()
	
	// Settings
	app                      craft.app.SETTING
	config                   craft.app.config.general.SETTING
	getenv                   getenv("VARIABLE")

	// Sites and Locales
	ismultisite              craft.app.isMultiSite
	language                 craft.app.language
	locale                   craft.app.locale
	
	alllocales               craft.app.i18n.allLocales
	applocales               craft.app.i18n.appLocales
	editablelocaleids        craft.app.i18n.editableLocaleIds
	editablelocales          craft.app.i18n.editableLocales
	getlocalebyid            craft.app.i18n.getLocaleById(1)
	primarysitelocale        craft.app.i18n.primarySiteLocale
	sitelocaleids            craft.app.i18n.siteLocaleIds
	sitelocales              craft.app.i18n.siteLocales

	// Closing tags
	case                     {% case "value" %}
	endcache                 {% endcache %}
	endifchildren            {% endifchildren %}
	endcss                   {% endcss %}
	endjs                    {% endjs %}
	endnav                   {% endnav %}

### Craft Twig Functions (via tab trigger)

	ceil                     ceil()
	classname                className(${1:object})$0
	clone                    clone(${1:object})$0
	floor                    floor()
	max                      max()
	min                      min()
	round                    round()
	shuffle                  shuffle()
	siteurl, siteurla        siteurl('path'), siteurla('path', params, 'https', siteIds)
	url, urla                url('path'), url('path', params, 'https', false)

### Debugging

	dump            <pre>{{ dump() }}</pre>

### PHP

	dd              Craft::dd();

---- 

## Installation

TextMate, and most editors that support TextMate bundles, allow the installation of bundles simply by extracting an archive or cloning the repository into the application's bundle directory. This bundle is no different. Below is a list of common bundle directories.

#### Sublime Text

To install this bundle in Sublime Text, download the bundle via Package Control or, if you wish to install the theme manually, a few extra steps are required:

1. Open Sublime Text and in the Preferences menu click `Browse Packages`.
2. Copy `Craft-Twig.tmbundle` into the Packages folder
3. Restart Sublime Text.

**A note on upgrading**

If you are upgrading to Craft-Twig v2 or Craft-Twig v3 you may run into a few errors having to do with cache or sessions. If you run into errors, try the following (this example use paths for OSX and Sublime Text 3):

1. Uninstall your previous version of Craft-Twig
2. Delete any cached version of Craft-Twig in<br>`~/Library/Application Support/Sublime Text 3/Cache/`
3. Delete the Sublime session in<br>`~/Library/Application Support/Sublime Text 3/Local/Session.sublime_session`
4. Delete the Package Control cache in<br>`~/Library/Application Support/Sublime Text 3/Packages/User/Package Control.cache`
5. Reinstall the Craft-Twig package

#### TextMate

- `/Library/Application Support/TextMate/Bundles`

#### Textmate 2

You can install this bundle in TextMate 2 by opening the preferences and going to the bundles tab. After installation it will be automatically updated for you.

---- 

## Themes

This bundle comes with two themes,

- Artisan Light
- Artisan Dark

These Themes are designed for use with the Craft-Twig bundle, but also fit general use. Feel free to use them as a base theme for constructing your own custom theme as well.

### Scopes

To aid customizing your own theme, here's a list of what each Twig element is scoped to:

	Tags:
	    {{ }}:
	        Tag:       punctuation.definition.tag.output.twig
	        Scope:     meta.tag.output.twig
	    {% %}:
	        Tag:       punctuation.definition.tag.expression.twig
	        Scope:     meta.tag.expression.twig
	    {# #}:
	        Tag:       punctuation.definition.tag.comment.twig
	        Scope:     comment.block.twig
	
	Embedded:
	    {% css %}: source.css.embedded.twig
	    {% js %}:  source.js.embedded.twig
	
	Constants:
	    Language:      constant.language.twig
	    Numeric:       constant.numeric.twig
	    Entities:      constant.character.entity.html
	
	Operators:
	    Arithmetic:    keyword.operator.arithmetic.twig
	    Assignment:    keyword.operator.assignment.twig
	    Bitwise:       keyword.operator.bitwise.twig
	    Comparison:    keyword.operator.comparison.twig
	    Logical:       keyword.operator.logical.twig
	
	Strings:
	    Single:        string.quoted.single.twig
	    Double:        string.quoted.double.twig
	
	Arrays:            punctuation.section.twig
	    Accessor:
	        Begin:     punctuation.section.twig
	        End:       punctuation.section.twig
	    Separator:     punctuation.separator.twig
	        Keys:      support.type.argument.twig
	Hashes:            punctuation.section.twig
	    Accessor:
	        Begin:     punctuation.section.twig
	        End:       punctuation.section.twig
	    Separator:     punctuation.separator.twig
	        Keys:      support.type.argument.twig
	
	Tags:              entity.name.tag.twig
	Macros:            entity.name.function.twig
	
	Functions:         entity.name.function.twig
	    Parens:
	        Begin:     punctuation.section.twig
	        End:       punctuation.section.twig
	    Arguments:     support.other.variable
	
	Filters:           support.function.filters.twig
	    Parens:
	        Begin:     punctuation.section.twig
	        End:       punctuation.section.twig
	    Arguments:     support.other.variable
	
	Tests:             support.function.tests.twig

## Extras

There are a few additional things in `/Extras` folder

- A `Craft-Twig Unit Test.twig` file for testing the Grammar and Themes
- Sublime Text Keymaps

## Maintenance & Contributions

It's an ongoing project to keep the Craft-Twig bundle updated with changes in Craft and there are plenty of ways the bundle could be improved. If you'd like to contribute to the Craft-Twig bundle, please consider submitting a pull request, reporting an issue, providing examples of how you would like to see the behavior of the bundle improved, or just giving someone in the community a high five in the hallway!

As Language Grammars are a bit hard to get involved with, I've begun documenting the experience a bit in the off chance it will help someone else save a few hours: [Notes on how to create a Language Grammar and Custom Theme for a Textmate Bundle][2].

## References


- [Craft][3]
- [Twig][4]
- [Sublime Text][5]
- [Textmate][6]
- [Straight Up Craft][7]

---- 

## Notes & Thanks

This repo has been forked from the popular [PHP-Twig][8] Textmate bundle. A lot of updates have been made, a lot of comments have been added, and parts of the bundle have been re-written from scratch (there is really no other way to make sense of maintaining a Language Grammar)!

The Craft Twig fork:

- Adds heavy commenting and new structure to the `Craft-Twig.tmLanguage` file
- Adds auto-pair key bindings for Twig action tags `{% %}`, output tags `{{ }}`
- Adds support to use the comment shortcut `command + /`
- Adds several additional twig snippets
- Adds several additional Craft-specific snippets
- Adds quick documentation snippets for referencing Craft template tags and syntax
- Add css and javascript syntax highlighting support within the appropriate Craft tags
- Adds two Themes: Artisan Light and Artisan Dark
- Updates various scopes in the Language Grammar in attempt to accommodate more Themes
- Updates the README to document the existing features and new snippets
- Updates the README so the language refers to this fork
- Has not been tested on Windows or Linux

Happy tabbing.

[1]:	https://vimeo.com/131062707
[2]:	https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle
[3]:	http://buildwithcraft.com/
[4]:	http://www.twig-project.org/
[5]:	http://www.sublimetext.com/
[6]:	http://macromates.com/
[7]:	http://straightupcraft.com/
[8]:	https://github.com/Anomareh/PHP-Twig.tmbundle

[image-1]:	https://raw.githubusercontent.com/BarrelStrength/Craft-Twig.tmbundle/master/Extras/images/craft-twig-overview-video.png
