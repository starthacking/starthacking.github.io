---
layout: page
title: Ruby
hierarchy:
  -
    name: "Windows"
    path: "/windows/"
---

## Ruby: TreeYaks app

This guide will show you how to make an app called TreeYaks, which
lets people post content and upvote/downvote what other people
posted.

You can install Ruby from [here][ruby] on Windows. Download the
code for this guide [here][hackpack], then navigate to the
`treeyaks/` folder in the command line and run `bundle install`.

Then, type `ruby app.rb`. Now, go to
[http://localhost:4567][localhost] in your browser. If you see the
TreeYaks page, then you're all set and everything is installed 
correctly! If not, it probably means something went wrong when installing Ruby and/or running `bundle install`.

## Getting Started

We'll build TreeYaks in Ruby using a framework called
[Sinatra][sinatra]. Sinatra is a web framework written in Ruby to
help you develop web applications. If you've never used Ruby
before, don't worry! We'll explain the syntax as we go along. If
you want to learn more about Ruby, however, check out these
interactive Ruby tutorials:

- [Ruby \| Codecademy][codecademy]
- [Try Ruby][tryruby]

### Viewing All Posts

The first milestone we'll tackle is viewing all posts. In
`app.rb`, there's a class `Yak`. A class in Ruby has instance
variables and methods, just like a class in Java or C++. Each
`Yak` object will represent one yak a user has posted.

```ruby
class Yak < ActiveRecord::Base
end
```

Let's assign all the yaks to a variable called `yaks` in the
`get '/'` method. This will make all the yaks appear on the
homepage. You can get all the `Yak`s every user has posted by
calling the `all` method on the `Yak` class.

```ruby
get '/' do
    # BEGIN YOUR CODE HERE
    
    # Here, you should store all the Yaks in the database in a variable called `yaks`.
    
    # END YOUR CODE HERE

    erb :index, locals: { yaks: yaks }
end
```

There should already be a line that calls the `erb` function.
`erb` is a special function that will render the HTML that shows
the `yaks`. That's why we pass in the `yaks` variable to it - it
will take all the yaks we loaded from the database and return the
rendered HTML to the browser. The HTML it renders is in the
`views/index.erb` file. You don't need to edit this file, but feel
free to change the styles around to customize the look and feel of
the homepage!

### Adding Posts

Next, let's let users add posts. You'll notice there's already a
"Create Yak" link on the homepage for TreeYaks. However, filling
out the form won't actually do anything right now.

In the `post '/new_yak'` method, the contents of the form the user
filled out is already in the `contents` variable. To complete the
rest of the method, add code that makes a new `Yak`, sets up the
instance variables, and calls the `save` method on the object to
save it to the database.

```ruby
post '/new_yak' do  
    contents = params['contents']

    # BEGIN YOUR CODE HERE

    # Here, you should create a new yak, initialize it with the data from the form, and then save it to the database.
    # END YOUR CODE HERE
    redirect to('/')
end
```

The call to `redirect_to` at the end of the method means that
after the user has posted a new yak, we'll take them back to the
homepage - that way they can see the yak they just posted!

Now, you should be able to test everything out. Go to the
homepage, and you should already see some yaks. Click on "Create
Yak", add a new yak, and go back to the homepage. If you see the
yak you just posted, you're in good shape!

### Upvoting and Downvoting

Now, let's add the ability for users to upvote or downvote yaks.
The code for both will be very similar, so let's first handle
upvoting. You'll notice that there are already some links for
Upvote and Downvote in each yak's card. Clicking on the Upvote
link will call the `post '/upvote'` method in `app.rb`. 

```ruby
post '/upvote' do
    yak_id = params['yak_id']

    # BEGIN YOUR CODE HERE

    # In this section, you should increment the yak's upvotes by 1 and return the new number of upvotes in json.
    # (Note: This will be called via AJAX, so you don't need to render any html or redirect to any other page.)

    # END YOUR CODE HERE
end
```

The `yak_id` variable is an integer containing the ID of the yak
that the user clicked upvote on. Fill in the rest of the method,
which should find the yak, increment the number of `upvotes` on
it, and save it to the database.

Now, do something similar for `downvote`, except decremenet the
number of upvotes by one rather than increasing it. This method
should look pretty similar to the `post '/upvote'` method.

```ruby
post '/downvote' do
    yak_id = params['yak_id']

    # BEGIN YOUR CODE HERE
    
    # In this section, you should decrement the yak's upvotes by 1.   
    # This will be called via AJAX, so you don't need to render any html or redirect to any other page.
    # Hint: You should be able to reuse some code from the '/upvote' method.

    # END YOUR CODE HERE
end
```

### Sorting

For the last feature, we'll add the ability to sort yaks by the
number of upvotes, so users can easily find the most popular yaks.
Take a look at the `get '/hot'`method. This will get called when
the user wants to view all the yaks, but sorted in descending
order of number of upvotes.

```ruby
get '/hot' do
    # BEGIN YOUR CODE HERE

    # Here, you should use the order method on the Yak class to get all the Yaks ordered by upvotes.
    # The order method takes one parameter, which is the field you want to order by.

    # END YOUR CODE HERE
end

get '/new' do
    # BEGIN YOUR CODE HERE

    # Here, you should use the order method on the Yak class to get all the Yaks ordered by their `created_at` fields.
    # The order method takes one parameter, which is the field you want to order by.

    # END YOUR CODE HERE
end
```

### Extension: Comments

Congratulations! You've now built a fully functional app with the
ability to create new yaks, upvote and downvote, and sort. If
you're really feeling ambitious, add the ability to comment on
yaks. This is pretty challenging and will require you to do a little bit of research of your own!

### License
MIT

[ruby]: http://rubyinstaller.org
[hackpack]: https://github.com/starthacking/hackpack-web
[localhost]: http://localhost:4567
[sinatra]: http://www.sinatrarb.com/
[codecademy]: https://www.codecademy.com/learn/ruby
[tryruby]: http://tryruby.org/
