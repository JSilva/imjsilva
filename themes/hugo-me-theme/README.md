# Me - Hugo theme for personal site

A simple responsive theme for Hugo based on [Read Only template](http://html5up.net/read-only) by HTML5UP.

**WARNING! WORK IN PROGRESS!**
Theme has some [issues](//github.com/aerohub/hugo-me-theme/issues) and I need help to solve them. Besides there are [some steps to go](#roadmap). Use it for production with care.

## Demo

You can see Me on [Hugo Themes](http://themes.gohugo.io/theme/hugo-me-theme/)

## Features

- Responsive design
- 9 color schemes
- Configurable social links
- Contact form
- Google Analytics


## Screenshot

![Me screenshot](https://raw.githubusercontent.com/aerohub/hugo-me-theme/master/images/screenshot.png)


## Contents

- [Installation](#installation)
- [Getting started](#getting-started)
    - [The config file](#the-config-file)
	- [Color schemes](#color-schemes)
    - [Make the contact form working](#make-the-contact-form-working)
    - [Test your site](#test-your-site)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)


## Installation

Inside the folder of your new Hugo site run:

    $ mkdir themes
    $ cd themes
    $ git clone https://github.com/aerohub/hugo-me-theme hugo-me-theme

For more information read the official [setup guide](//gohugo.io/overview/installing/) of Hugo.


## Getting started

After installing the theme successfully it requires a just a few more steps to get your site running.

### The config file

Take a look inside the [`exampleSite`](//github.com/aerohub/hugo-me-theme/tree/master/exampleSite) folder of this theme. You'll find a file called [`config.toml`](//github.com/aerohub/hugo-me-theme/blob/master/exampleSite/config.toml). To use it, copy the [`config.toml`](//github.com/aerohub/hugo-me-theme/blob/master/exampleSite/config.toml) in the root folder of your Hugo site. Change the strings with your data.

### Color schemes

In your [`config.toml`](//github.com/aerohub/hugo-me-theme/blob/master/exampleSite/config.toml) you may choose a color scheme for your site.

```
[params]
    
	colorscheme = "red"

```

Available schemes are: `blue`, `red`, `orange`, `yellow`, `green`, `cyan`, `magenta`, `brown`, `gray`

![Me color schemes](https://raw.githubusercontent.com/aerohub/hugo-me-theme/master/images/tiny-me-schemes.png)

### Make the contact form working

Since this page will be static, you can use [formspree.io](//formspree.io/) as proxy to send the actual email. Each month, visitors can send you up to one thousand emails without incurring extra charges. Begin the setup by following the steps below:

1. Enter your email address under 'email' in the [`config.toml`](//github.com/aerohub/hugo-me-theme/blob/master/exampleSite/config.toml)
2. Upload the generated site to your server
3. Send a dummy email yourself to confirm your account
4. Click the confirm link in the email from [formspree.io](//formspree.io/)
5. You're done. Happy mailing!


### Test your site

In order to see your site in action, run Hugo's built-in local server. 

    $ hugo server -w

Now enter `localhost:1313` in the address bar of your browser.

## Roadmap

- [x] - color scheme selection in the configuration file
- [ ] - data files for skills and portfolio pages

## Contributing

Did you found a bug or got an idea for a new feature? Feel free to use the [issue tracker](//github.com/aerohub/hugo-me-theme/issues) to let me know. Or make directly a [pull request](//github.com/aerohub/hugo-me-theme/pulls).


## License

This work is licensed under the Creative Commons Attribution 3.0 Unported License. For more information read the [License](//github.com/aerohub/hugo-me-theme/blob/master/LICENSE.md).
