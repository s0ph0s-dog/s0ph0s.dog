+++
title = "Custom Hugo Themes"
date = "2021-08-28T22:52:22-04:00"
draft = "true"
tags = ["meta", "hugo", "design", "webdev"]
+++

Creating a Hugo theme from scratch is refreshingly easy, and well worth the time I invested into it.

# Setup

All you really need to do to set up a custom theme is to make a new Hugo site, and then make a new theme inside of it.  Update your `config.toml` to tell Hugo that you want to use the theme you just created, and that's it!

# Problems

It's kinda important to update the `config.toml` with the name of your theme. Otherwise, Hugo will spit out a lot of very confusing errors, and nothing you change will make a difference.