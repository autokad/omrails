https://toolbelt.herokuapp.com/
https://github.com/autokad/omrails

society is quickly dividing into two groups
1 those who know how to code - they can manipulate the very structure of the world around them
2 those who dont, their lives are being designed and directed by those that do
entrepreneours guide to customer development

front end html css javascript
back end php ruby python SQL
web application frameworks
	ruby on rails
	Django

	its ok to not understand something the first time

	Ruby on Rails Tutorial by Michael Hartl
	Web Applications by John Ousterhout at Stanford University
	rails casts
	
	hackathons
	
rails server

git push heroku master

bundle install --without production
git add .
git commit -am "add pg gem to heroku"
git push
git push heroku master




rails generate controller Pages home
in browser:	http://localhost:3000/pages/home

in routes.rb:  root :to => 'Pages#home'

http://twitter.github.io/bootstrap/
could put in vendor
https://github.com/thomas-mcdonald/bootstrap-sass/blob/master/README.md

gem 'bootstrap-sass', '~> 2.3.1.3'
bundle install
this installs all gems from the web
need to create style sheet to import it
create styles.css.scss
	add	@import 'bootstrap';
	add @import 'bootstrap-responsive';
restart server
	rails s
update javascripts-application.js
	add //= require bootstrap
http://twitter.github.io/bootstrap/scaffolding.html
	add <div class="container"> to application.html.erb around the yield tags.
update header:

<div class="navbar navbar-fixed-top">
  <div class="navbar-inner">
    <div class="container">
 
    	<!-- .btn-navbar is used as the toggle for collapsed navbar content -->
    	<a class="btn btn-navbar" data-toggle="collapse" data-target=".nav-collapse">
	    	<span class="icon-bar"></span>
	        <span class="icon-bar"></span>
	        <span class="icon-bar"></span>
      	</a>
 
	    <!-- Be sure to leave the brand out there if you want it shown -->
	    <a class="brand" href="#">Project name</a>
 
      	<!-- Everything you want hidden at 940px or less, place within here -->
		<div class="nav-collapse collapse">
        <!-- .nav, .navbar-search, .navbar-form, etc -->
	        <ul class="nav">
				<li><%= link_to "Home", root_path %></li>
				<li><%= link_to "About", about_path %></li>
	        </ul>
      	</div>
    </div>
  </div>
</div>

to styles.css.scss:


Need gem devise: https://github.com/plataformatec/devise
this is an authentication gem.
	add gem 'devise'	to gem file
	in cmd, type bundle install
	in cmd type rails generate devise:install
	
	update config/environments/development.rb and production.rb by adding:
		# In production, :host should be set to the actual host of your application
		config.action_mailer.default_url_options = { :host => 'localhost:3000' }
		
	If you are deploying Rails 3.1+ on Heroku, you may want to set:
		config.assets.initialize_on_precompile = false

	run in cmd: rails generate devise User
	
	run in cmd: rake db:migrate or bundle exec rake db:migrate
	
	check routes with rake routes in cmd
	
	restart server
	
	update register now button:	 new_user_registration_path
	update login button:	new_user_session_path

	run rails generate devise:views  for better views
	
	
	simple form gem: to make forms look much better
		https://github.com/plataformatec/simple_form/blob/master/README.md
		check read me, see instructions, says add this to gem file: gem 'simple_form'
		run budnle install in cmd
		run rails generate simple_form:install --bootstrap
		update the views-devise-sessions-new.html.erb
			change	form_for	to	simple_form_for
		
		add user name
			generate our own migration
				rails generate migration AddNameToUsers name:string
				rake db:migrate
				
		Want to generate our own code, pins like in pinterest
			need to runrails generate scaffold Pins description:string -- skipp-stylesheets
				creates controler for pin, model, views, migration
			need to run rake db:migrate
				this is how most resources work, create, show (read), update, destroy pin (CRUD)
			