# CircleCI Documentation [![CircleCI Build Status](https://circleci.com/gh/circleci/circleci-docs.svg?style=shield)](https://circleci.com/gh/circleci/circleci-docs) [![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/circleci/circleci-docs/master/LICENSE) [![CircleCi Community](https://img.shields.io/badge/community-CircleCI%20Discuss-343434.svg)](https://discuss.circleci.com)

This is the public repository for <https://circleci.com/docs/>, a static website generated by [Jekyll](https://jekyllrb.com/). If you find any errors or have requests, you can set up a [local environment](#local-development) and make changes by following our [Contributing Guide](CONTRIBUTING.md).

If you can't contribute but still want to report a problem, open an [Issue](https://github.com/circleci/circleci-docs/issues) on this project. If you have a question or need help debugging a problem, **do not submit an issue**. Instead, please head to [CircleCI Discuss](https://discuss.circleci.com/) where our support team will help you out.

## Local Development
There are two ways to run a local development server: [With Vagrant](#run-with-vagrant) or [Without Vagrant](#run-without-vagrant).

### Run With Vagrant
The easiest way to get started is by using Vagrant because it gives you a clean environment with all of the necessary dependencies.

#### Prerequisites
- Vagrant: [download directly](https://www.vagrantup.com/downloads.html), `brew cask install vagrant`, or `sudo apt-get install vagrant`
- VirtualBox: [download directly](https://www.virtualbox.org/wiki/Downloads), `brew cask install virtualbox`, or `sudo apt-get install virtualbox`

#### macOS Setup

Open a terminal window and follow these steps to set up your local development environment with Vagrant and Brew.

1. Install Xcode:

    `xcode-select --install`

2. Install Homebrew, a macOS package manager:

    `ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

3. Install Vagrant:

    `brew cask install vagrant`

4. Install VirtualBox:

    `brew cask install virtualbox`

5. Fork the `circleci-docs` repo on GitHub:

6. Clone your fork of the `circleci-docs` repo:

    `git clone https://github.com/<my_github_username>/circleci-docs.git`

7. `cd` into `circleci-docs` and start Jekyll by running `./jctl start`. The first time you run this command, Vagrant will provision the entire VM based on the contents of `boostrap.sh`. This process can take a few minutes, but it's a one-time deal.

After successful completion, Jekyll will automatically start in the VM. Vagrant will then begin forwarding port 4040, and you'll be able to view the complete documentation site at <http://localhost:4040/docs/>.

#### Jekyll Controller Commands

The Jekyll Controller (`jctl`) is a bash wrapper script that talks to Jekyll & Vagrant.

- `./jctl start`: Starts Jekyll; will also start Vagrant, if not already running
- `./jctl rebuild`: Rebuilds the site
- `./jctl stop`: Shuts down entire VM (including Jekyll)
- `./jctl restart`: Stops and then starts the VM `./jctl stop && ./jctl start`

As an alternative to `jctl`, you can log directly into the VM to interact with Jekyll. Run `vagrant ssh` to enter the VM, then `cd /vagrant/jekyll` to access the repository's files. From there, you can run standard Jekyll commands with any preferred options.

### Run Without Vagrant
If you already have a stable Ruby environment and feel comfortable installing dependencies, you can run the server directly on your machine.

#### Prerequisites
- Ruby: See this project's Gemfile for the version of Ruby currently being used. We recommend RVM for managing multiple Ruby versions, but there are other options available.
- [Jekyll](https://jekyllrb.com/): Jekyll 3 transforms Markdown files.
- [HTMLProofer](https://github.com/gjtorikian/html-proofer): Used for testing links, images, and HTML. The docs site will need a passing build to be deployed, so use HTMLProofer to test everything before you push changes to GitHub.

You're also welcome to use Bundler to install required gems. If you are using RVM (or similar), make sure they all play nicely together.

#### First Run
To get a local copy of <https://circleci.com/docs/>, run the following commands:

```bash
git clone https://github.com/circleci/circleci-docs.git
cd circleci-docs/jekyll
jekyll serve
```

Jekyll will build the site and start a web server, which can be viewed in your browser at <http://localhost:4000/docs/>.

#### Jekyll Commands
`jekyll build`: Generates static files for the site in the `jekyll/_site` directory.

`jekyll serve`: Runs `jekyll build`, then starts an included mini webserver to serve files from `'jekyll/_site`; listens to localhost:4000 by default.

`jekyll serve --detach`: Serves the site as before, but runs in the background so you can use the same terminal window. Jekyll will display its process ID, so you can use that to kill the process when you want to stop Jekyll. If you lose the PID, you can run `pkill -f jekyll` to kill all Jekyll instances.

### Editing Docs

Now that you have a working local environment, please follow our [Contributing Guide](CONTRIBUTING.md) to make and submit changes.

## License Information
Documentation (guides, references, and associated images) is licensed as Creative Commons Attribution-NonCommercial-ShareAlike CC BY-NC-SA. The full license can be found [here](http://creativecommons.org/licenses/by-nc-sa/4.0/legalcode), and the human-readable summary [here](http://creativecommons.org/licenses/by-nc-sa/4.0/).

Everything in this repository not covered above is licensed under the [included MIT license](LICENSE).
