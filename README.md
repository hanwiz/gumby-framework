# Gumby2 Front End Frameword - Rails Gem

This is a Rails gem that will install the [Gumby Front End Framework](http://gumbyframework.com/) in your application.

## Installation

Add this line to your application's Gemfile:

    gem 'gumby-framework'

And then execute:

    $ bundle install

Or install it yourself as:

    $ gem install gumby-framework

## Usage

You will need to add also the <code>modernizr-rails</code> gem to your gemfile:

	# Gemifile
	
	gem "modernizr-rails"
	gem "gumby-framework", :github => 'TeckniX/gumby-framework', :submodules => true
	
Then run <code>bundle install</code>.

The Gumby framework is always pulled fresh from their repo - the only issue is that their folder structure isn't rails compliant.
This is fixed by adding the following to your `config/application.rb`
	
	config.assets.paths << Gumby::Framework::Engine.root.join("vendor", "assets", "sass")
	config.assets.paths << Gumby::Framework::Engine.root.join("vendor", "assets", "js")
	config.assets.paths << Gumby::Framework::Engine.root.join("vendor", "assets", "fonts")
	config.assets.paths << Gumby::Framework::Engine.root.join("vendor", "assets", "img")
	
Notice we're pulling their Sass files instead of their css - This means that you can over-write any setting the sass way. Now isn't that sassy?

You will need to add also this tag to your HTML head tag:

	<%= javascript_include_tag :modernizr %>
	
#### CSS

Add this line at the end of your application.css

	*= require gumby
	
#### Javascript


You will need to add modernizr and global Gumby object in your application.js:

	//= require modernizr
	//= require main
	//= require plugin
	
After this line, you can add the Gumby JS plugins like this:

	//= require ui/gumby.checkbox
	//= require ui/gumby.radiobtn
	
You have available the following plugins:

	//= require ui/gumby.fittext
	//= require ui/gumby.navbar
	//= require ui/gumby.checkbox
	//= require ui/gumby.fixed
	//= require ui/gumby.radiobtn
	//= require ui/gumby.retina
	//= require ui/gumby.skiplink
	//= require ui/gumby.tabs
	//= require ui/gumby.toggleswitch
	//= require ui/jquery.validation



## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
