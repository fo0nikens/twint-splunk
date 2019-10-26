
Work in progress!

I will add to this README as parts of this project become usable. :-)


## Quick and Dirty Usage

You don't even need to clone the repo for these:
- This command uses the `twint-user` helper script and does the same, except tweets will be written in JSON format to `logs/user/dmuth/` and a resume file will automatically be used:
   - `bash <(curl -s https://raw.githubusercontent.com/dmuth/twint-splunk/master/twint-user) dmuth --year 2020 --since 2019-01-01`
   - When the command completes a file with the suffix `.done` will be written next to the log so that if the command is re-run with the same parameters, the download will be skipped.
- Download 5 years of tweets with `twint-user-by-year`:
   - `bash <(curl -s https://raw.githubusercontent.com/dmuth/twint-splunk/master/twint-user-by-year) dmuth 2010 2014`


## Regular Usage

First, clone the repo. :-)

Now, you can run `./twint` which is a Docker wrapper for my twint-lite build.
- Get every tweet I made in 2019:
   - `bash <(curl -s https://raw.githubusercontent.com/dmuth/twint-splunk/master/
twint -u dmuth -o tweets.txt --resume resume-user-dmuth.txt --since 2019-01-01 until 2020-01-01`


### Advanced Usage

If you want to download multiple Twitter timelines or a very busy user's timeline,
please check out more detailed instructions in <a href="HOW-TO-DOWNLOAD-MANY-TWEETS.md">HOW-TO-DOWNLOAD-MANY-TWEETS.md</a>.


## Development

- Twint Docker Management:
   - `./bin/build.sh [ full ]` - Build Docker image. For all scripts where `full` is available, if it is speicfied as the first argument, the full (with Pandas) verison will be built.  Otherwise, the Lite version will be built.
   - `./bin/devel.sh [ full ]` - Build Docker image and spawn interactive shell.
   - `./bin/push.sh [ full ]` - Push Docker image to Docker Hub.
   - `./bin/pull.sh [ full ]` - Pull Docker image from Docker Hub.
   - `./bin/run.sh [ full ] args` - Run for production use. Additional args should be passed in on the command line.
- Splunk Management:
   - `./bin/splunk-start.sh [ --devel ]` - Start a Splunk instance at <a href="https://localhost:8000">https://localhost:8000/</a>.  Just follow the instructions on configuring Splunk. Use `--devel` if you want an interactive shell opened in the container.
   - `./bin/splunk-stop.sh` - Kill the Splunk instance


## Bugs/TODO

- If you try writing a file to a directory that is not under the current directory, Docker will likely have path issues.


