+++
title = "Custom Hugo Themes"
date = "2021-08-28T22:52:22-04:00"
draft = "true"
tags = ["meta", "hugo", "design", "webdev"]
+++

Creating a Hugo theme from scratch is refreshingly easy, and well worth the time I invested into it.

<!--more-->

# Setup

All you really need to do to set up a custom theme is to make a new Hugo site, and then make a new theme inside of it.  Update your `config.toml` to tell Hugo that you want to use the theme you just created, and that's it!

# Problems

* It's kinda important to update the `config.toml` with the name of your theme. Otherwise, Hugo will spit out a lot of very confusing errors, and nothing you change will make a difference.
* Hugo's templating language does not do string interpolation.  While I was trying to get image resizing working, I ran into a bunch of issues that seemed utterly baffling—because I was treating Hugo like a shell script and expecting `"$variable text $other_variable"` to expand the variables inline.  It does not do this, you have to do `printf "%s text %s" $variable $other_variable` if you want a string with both of those variables in it.
* Hugo doesn't allow arbitrary additional keys in the objects that make up your menus.  I tried to add `icon = "whatever"` to my menus, but there's no way to access that.  The supported way to accomplish this is to set `pre = "whatever"` in the config, and then use `{{ with .Pre }}` in the range call that produces the menu.
