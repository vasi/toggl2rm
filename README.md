# toggl2rm

This script copies time logs from the time tracker [Toggl](http://toggl.com/) to the issue tracker [Redmine](http://www.redmine.org/). It uses the APIs for each service, so it doesn't need anything to be done on the server side.

## Usage

You should the relevant Redmine issue number to each time log in Toggl, eg: `This is my fix for issue #1234`.

`toggle2rm -r URL -a TOKEN -t TOKEN [2012-01-31]`

The arguments are:

* -r, --redmine-url: The URL for your Redmine instance, eg: `http://redmine.example.com`. Note that the scheme (http or https) is required.
* -a, --redmine-token: Your [Redmine REST API](http://www.redmine.org/projects/redmine/wiki/Rest_api) token. Your Redmine instance will need to have "Enable REST API" turned on! Then you can get your token from the right column of the "My account" page in Redmine.
* -t, --toggl-token: Your Toggl API token. You can get this from your [Toggl account page](https://toggl.com/app/profile).
* Optionally, the date whose time entries you want to copy. If you leave this out, it will use the current date.

## Caveats

* This isn't particularly well-tested. But it's been working fine for us at [Evolving Web](httsp://evolvingweb.ca)!
* You'll need Ruby to run this script.
* It explicitly doesn't test the Redmine instance's SSL certificate, since OS X's Ruby is weird and broken.
* It only looks at your first Toggl workspace. Patches welcome!
* If a time log has no issue number in its description, it is just skipped.
* There's no duplicate detection—run this script twice, and your time will be logged twice.
* There's no support for SOCKS proxies, patches welcome.

## License

This code is available under the [MIT License](LICENSE)
