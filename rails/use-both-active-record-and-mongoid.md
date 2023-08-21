# Use both ActiveRecord and Mongoid in a Rails project

Use both ActiveRecord and Mongoid in a Rails project is easy. Add mongoid in Gemfile:

```
gem 'mongoid', '~> 6.1.0'
```

then ``bundle install``

However, the ``mongoid`` gem would change your default ORM adapter from ActiveRecord to Mongoid:

If you're not sure which default adapter is you can try: ``rails g model`` and check the output message

```
Usage:
  rails generate model NAME [field[:type][:index] field[:type][:index]] [options]

Options:
      [--skip-namespace], [--no-skip-namespace]  # Skip namespace (affects only isolated applications)
      [--force-plural], [--no-force-plural]      # Forces the use of the given model name
  -o, --orm=NAME                                 # ORM to be invoked
                                                 # Default: mongoid
```

So if you wanna generate a new model inherited from ActiveRecord:

```
rails g model Manager --orm=active_record
```

Notice: it's ``active_record`` instead of ``activerecord``
