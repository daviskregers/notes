# Running Travis CLI in a container

Since Travis CLI requires rubu installed on a local machine, we don't really want to install it. We can use docker to install the Travis CLI.

```
$ docker run -it -v $(pwd):/app ruby:2.3 sh
Unable to find image 'ruby:2.3' locally
2.3: Pulling from library/ruby
e79bb959ec00: Pull complete 
d4b7902036fe: Pull complete 
1b2a72d4e030: Pull complete 
d54db43011fd: Pull complete 
69d473365bb3: Pull complete 
84ed2a0dc034: Pull complete 
8952ca0665c5: Pull complete 
ef485f36c624: Pull complete 
Digest: sha256:78cc821d95c48621e577b6b0d44c9d509f0f2a4e089b9fd0ca2ae86f274773a8
Status: Downloaded newer image for ruby:2.3
# cd app
# gem install travis
Fetching multipart-post-2.0.0.gem
Fetching faraday-0.15.4.gem
Fetching faraday_middleware-0.13.1.gem
Fetching highline-1.7.10.gem
Fetching backports-3.13.0.gem
Fetching multi_json-1.13.1.gem
Fetching addressable-2.4.0.gem
Fetching net-http-persistent-2.9.4.gem
Fetching net-http-pipeline-1.0.1.gem
Fetching gh-0.15.1.gem
Fetching launchy-2.4.3.gem
Fetching ffi-1.10.0.gem
Fetching ethon-0.12.0.gem
Fetching typhoeus-0.8.0.gem
Fetching websocket-1.2.8.gem
Fetching pusher-client-0.6.2.gem
Fetching travis-1.8.9.gem
Successfully installed multipart-post-2.0.0
Successfully installed faraday-0.15.4
Successfully installed faraday_middleware-0.13.1
Successfully installed highline-1.7.10
Successfully installed backports-3.13.0
Successfully installed multi_json-1.13.1
Successfully installed addressable-2.4.0
Successfully installed net-http-persistent-2.9.4
Successfully installed net-http-pipeline-1.0.1
Successfully installed gh-0.15.1
Successfully installed launchy-2.4.3
Building native extensions. This could take a while...
Successfully installed ffi-1.10.0
Successfully installed ethon-0.12.0
Successfully installed typhoeus-0.8.0
Successfully installed websocket-1.2.8
Successfully installed pusher-client-0.6.2
Successfully installed travis-1.8.9
# travis
Shell completion not installed. Would you like to install it now? |y| n
Usage: travis COMMAND ...

Available commands:

	accounts       displays accounts and their subscription status
	branches       displays the most recent build for each branch
	cache          lists or deletes repository caches
	cancel         cancels a job or build
	console        interactive shell
	disable        disables a project
	enable         enables a project
	encrypt        encrypts values for the .travis.yml
	encrypt-file   encrypts a file and adds decryption steps to .travis.yml
	endpoint       displays or changes the API endpoint
	env            show or modify build environment variables
	help           helps you out when in dire need of information
	history        displays a projects build history
	init           generates a .travis.yml and enables the project
	lint           display warnings for a .travis.yml
	login          authenticates against the API and stores the token
	logout         deletes the stored API token
	logs           streams test logs
	monitor        live monitor for what's going on
	open           opens a build or job in the browser
	pubkey         prints out a repository's public key
	raw            makes an (authenticated) API call and prints out the result
	report         generates a report useful for filing issues
	repos          lists repositories the user has certain permissions on
	requests       lists recent requests
	restart        restarts a build or job
	settings       access repository settings
	setup          sets up an addon or deploy target
	show           displays a build or job
	sshkey         checks, updates or deletes an SSH key
	status         checks status of the latest build
	sync           triggers a new sync with GitHub
	token          outputs the secret API token
	version        outputs the client version
	whatsup        lists most recent builds
	whoami         outputs the current user

run `/usr/local/bundle/bin/travis help COMMAND` for more infos
```