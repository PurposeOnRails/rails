# Welcome to PurposeOnRails

Purpose on Rails is an extension of the Ruby on Rails web-framework that
offers support for purpose-aware and purpose-respecting applications.
Purpose Limitation is one of the major principles of the new European
Law, the GDPR. Also, purpose limitation is generally a pretty nice idea!
With PurposeOnRails (PoR) you can easily allow users to manage purposes
of their data items and respect them when querying.

## Basics
Create a new application using the normal `rails new my_app` command.
There is a new optional flag (default is true) that allows you to create
a purposeful application: `--purposeful=true`. This will create a demo
purpose tree file that you can use to model your purposes, as well as
some files for automatic view creation etc. For example, there's a
`Purpose` Mode, View, Controller setup baked right in. Just add it to
your routes and off you go.

Scaffolding has also been adapted to generate purpose-aware data.
For every column (unless specified otherwise) a purpose partner column
is automatically generated. Controllers can handle these partner
attributes out of the box and generated views also include an editor for
them for the user.

ActiveRecord has been extended by a `for` method. When writing queries,
don't forget to specify for which purpose you are querying. A normal
query should now look something like this:
```
User.where(name: 'Jane Doe')
    .where("age > ?", 50)
    .select(:email)
    .for(purpose_id)
```
If you don't include a purpose_id when querying, no data will be
returned. If you include a purpose_id, only the data is returned that
the user whitelisted for that specific purpose.

## So what is Ruby on Rails anyways?

Rails is a web-application framework that includes everything needed to
create database-backed web applications according to the
[Model-View-Controller (MVC)](http://en.wikipedia.org/wiki/Model-view-controller)
pattern.

Understanding the MVC pattern is key to understanding Rails. MVC divides your
application into three layers: Model, View, and Controller, each with a specific responsibility.

## Model layer

The _**Model layer**_ represents the domain model (such as Account, Product,
Person, Post, etc.) and encapsulates the business logic specific to
your application. In Rails, database-backed model classes are derived from
`ActiveRecord::Base`. [Active Record](activerecord/README.rdoc) allows you to present the data from
database rows as objects and embellish these data objects with business logic
methods.
Although most Rails models are backed by a database, models can also be ordinary
Ruby classes, or Ruby classes that implement a set of interfaces as provided by
the [Active Model](activemodel/README.rdoc) module.

## Controller layer

The _**Controller layer**_ is responsible for handling incoming HTTP requests and
providing a suitable response. Usually this means returning HTML, but Rails controllers
can also generate XML, JSON, PDFs, mobile-specific views, and more. Controllers load and
manipulate models, and render view templates in order to generate the appropriate HTTP response.
In Rails, incoming requests are routed by Action Dispatch to an appropriate controller, and
controller classes are derived from `ActionController::Base`. Action Dispatch and Action Controller
are bundled together in [Action Pack](actionpack/README.rdoc).

## View layer

The _**View layer**_ is composed of "templates" that are responsible for providing
appropriate representations of your application's resources. Templates can
come in a variety of formats, but most view templates are HTML with embedded
Ruby code (ERB files). Views are typically rendered to generate a controller response,
or to generate the body of an email. In Rails, View generation is handled by [Action View](actionview/README.rdoc).

## Frameworks and libraries

[Active Record](activerecord/README.rdoc), [Active Model](activemodel/README.rdoc), [Action Pack](actionpack/README.rdoc), and [Action View](actionview/README.rdoc) can each be used independently outside Rails.
In addition to that, Rails also comes with [Action Mailer](actionmailer/README.rdoc), a library
to generate and send emails; [Active Job](activejob/README.md), a
framework for declaring jobs and making them run on a variety of queueing
backends; [Action Cable](actioncable/README.md), a framework to
integrate WebSockets with a Rails application; [Active Storage](activestorage/README.md), a library to attach cloud
and local files to Rails applications;
and [Active Support](activesupport/README.rdoc), a collection
of utility classes and standard library extensions that are useful for Rails,
and may also be used independently outside Rails.

## Getting Started

1. Install Rails at the command prompt if you haven't yet:

        $ gem install rails

2. At the command prompt, create a new Rails application:

        $ rails new myapp

   where "myapp" is the application name.

3. Change directory to `myapp` and start the web server:

        $ cd myapp
        $ rails server

   Run with `--help` or `-h` for options.

4. Go to `http://localhost:3000` and you'll see:
"Yay! You’re on Rails!"

5. Follow the guidelines to start developing your application. You may find
   the following resources handy:
    * [Getting Started with Rails](http://guides.rubyonrails.org/getting_started.html)
    * [Ruby on Rails Guides](http://guides.rubyonrails.org)
    * [The API Documentation](http://api.rubyonrails.org)
    * [Ruby on Rails Tutorial](https://www.railstutorial.org/book)

## Contributing

[![Code Triage Badge](https://www.codetriage.com/rails/rails/badges/users.svg)](https://www.codetriage.com/rails/rails)

We encourage you to contribute to Ruby on Rails! Please check out the
[Contributing to Ruby on Rails guide](http://edgeguides.rubyonrails.org/contributing_to_ruby_on_rails.html) for guidelines about how to proceed. [Join us!](http://contributors.rubyonrails.org)

Trying to report a possible security vulnerability in Rails? Please
check out our [security policy](http://rubyonrails.org/security/) for
guidelines about how to proceed.

Everyone interacting in Rails and its sub-projects' codebases, issue trackers, chat rooms, and mailing lists is expected to follow the Rails [code of conduct](http://rubyonrails.org/conduct/).

## Code Status

[![Build Status](https://travis-ci.org/rails/rails.svg?branch=master)](https://travis-ci.org/rails/rails)

## License

Ruby on Rails is released under the [MIT License](https://opensource.org/licenses/MIT).
