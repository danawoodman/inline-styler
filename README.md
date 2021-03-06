# Django Inline Styler

Inline Styler is the small Django app behind <http://inlinestyler.torchboxapps.com>

It's a service which, when given a block of HTML including CSS, will parse the CSS and convert it to inline "style" attributes on each elements matched by the CSS rules found.

The benefit of this is primarily in developing HTML emails. The most common email clients have patchy support for `<style>` or `<link>` elements, but do on the whole support a varied set of CSS properties. Its therefore necessary to instead define styles in "style" attributes on each of the elements themselves, which is tedious for anything but the simplest of emails and introduces significant code maintenance problems. The Inline Styler frees up the developer to write CSS in less tedious/more maintainable ways: using proper selectors and rules, grouped in either a stylesheet or a `<style>` block. The Inline Styler converts these rules into the inline "style" attributes for you.

Additionally, among the email clients who do support CSS, support for individual CSS properties is variable. The Inline Styler will analyze your CSS and estimate a compatibility rating across all the email clients as a whole, alerting you to any particular properties likely to reduce compatibility.

You can see a working example of this service at <http://inlinestyler.torchboxapps.com>.

To use this app, CSS to be "inlined" must be presented in the HTML either

- Linked absolutely e.g `<link rel="stylesheet" href="http://mysite.com/styles.css" />`, or
- Provided in a `<style>` block in the `<head>` of the HTML, without `@import`s

### Python requirements:

* lxml: <http://lxml.de/>
* cssutils: <http://pypi.python.org/pypi/cssutils>

### Other requirements:

- `css_compliance.csv`: generated by hand from the "complete guide" Excel spreadsheet from Campaign Monitor <http://www.campaignmonitor.com/css/>. This requires periodic updates as campaign monitor release updates to their spreadsheet. If you edit the existing `css_compliance.csv` and compare it to the Excel spreadsheet you download from CM, the essential differences are that the XLS has been stripped of formatting, blank lines or duplicate groups of selector/element information.

## Support

Inline Styler was written several years ago partly as a personal "Hello World" experiment to learn Django/Python. I welcome anyone willing to fork and contribute to the code, but unfortunately I don't have a great deal of time to maintain this myself - for example updating the css compliance CSV. I'm instead releasing it to the public after many requests for the source.

## Questions/Discussion:

- Find me on Twitter at @davecranwell