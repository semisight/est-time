# est-time

## A simple python script for estimating time spent on a git repo

ext-time is a simple script that will estimate the time a developer has spent working on a specific git repo. It does this by getting a list of time deltas in between each commit, and creating a list of 'runs' where each delta is less than a specified amount of time (default 40 minutes, or 2400 seconds). Deltas larger than the max-delta start a new run.

The time for each run is estimated at the sum of the deltas for that run, plus the average of the deltas (because there is always one more commit than delta for each run). These are summed together to get the total time.

### Dependencies

* git-python
* python 2.7

### Usage

```sh
./esttime /path/to/repo
./esttime -t [max time spent between commits *in seconds*] /path/to/repo
```

### Why make this?

Because I had the idea and it sounded like an interesting waste of time.

### It grossly underestimates the time I spent on repo X.

Well, first of all, use a larger max-delta. You can specify this on the command line with the -t [time] switch. Second of all, it's a guess. If you worked for 24 hours without a break or a single commit, that will only be counted as T minutes, where T is the average number of minutes between commits for that repo.
