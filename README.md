# Spree Globalize #

WARNING: Intensive merge and re-work in progress. Do not use for now!

This extension is a work-in-progress merge of jeroenj/spree-product_translations and tomash/globalize_spree to create THE Spree extension for integrating Globalize3.

Makes product details, properties, prototypes, taxonomies and option types translatable by bridging the [Globalize3](https://github.com/svenfuchs/globalize3) gem.

## Installation and configuration ##

In your Gemfile, add:

    gem 'spree_globalize'

Then install the gem:

    bundle install

Finally migrate your database:

    rake db:migrate

If you have pre-existing data, you'll need to run this rake task:

    rake spree:extensions:spree_globalize:globalize_legacy_data

it will copy the original data over to the new translation tables. Globalize3 doesn't default to the original model table for the default locale like v1 used to.

## How to use it ##

To edit the content in a specific language, simply change the locale on the language nav, and edit on the admin as usual.

## Translated fields ##

### Product ###

* name
* description
* meta_description
* meta_keywords

### Property ###

* presentation

### Prototype ###

* name

### Taxonomy ###

* name

### Taxon ###

* name
* description

### OptionType ###

* presentation

### OptionValue ###

* presentation

## Fallbacks for empty translations ##

If you have translations in your database (by using the [spree-simple_product_translations](https://github.com/jeroenj/spree-simple_product_translations) extension for example) with empty translations (being a blank string instead of `nil`) you might want to add this configuration option to an initializer in your app:

    Spree::Config.set :fallbacks_for_empty_translations => true

It will then use fallbacks for empty strings too.

## Running tests ##

The tests are not updated since the original fork of the spree 0.11 compatible version. They will pretty sure fail. Feel free to fork the project and create a pull request with tests.

### Test information by [oliverbarnes](https://github.com/oliverbarnes) ###
You might need to comment out the rspec gem requirement under config/environments/test.rb - for some reason, even with both the rspec gem and plugin installed, I would keep getting an annoying missing gem error.

Spree is officially making a choice for Test::Unit anyway, so this shouldn't create a problem.

(not that I don't like Rspec, I actually prefer it in other projects.)

## Feature requests and patches welcome ##

If you see anything you need missing, or if you have a useful patch, feel free to submit them on the Issues section of the github project.
