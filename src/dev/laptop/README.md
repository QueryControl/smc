# Developing SMC on a personal laptop

Scripts for doing development of SMC on a personal single-user laptop that you fully control.  You _**must not**_ have anything else listening on ports 5000, 5001, 8080, 28015 and 29015.

## Prerequisites:

- Install Node.js version 5.0
- Install rethinkDB >= 2.1.5
- Make sure "python" is python2, and that the yaml module is installed: `pip install pyyaml --user`


## The servers

Explicitly start each of the following scripts in their own terminal session (they will run in the foreground).  Make sure to set the environment with `source smc-env` first:

- `./start_rethinkdb.py`

- `./start_hub.py`

- `./start_webpack.py`


##  Running all servers at once with tmux

Type

    ./tmux-start-all

to create a single tmux session with each of the servers running.

## Use it

Your local SMC server should be running at http://localhost:5000

## Changing the web frontend

Try editing smc-webapp/r_help.cjsx, e.g., changing the heading "Support" to something else.  Watch the webpack process notice the change and build.   Refresh your browser and see the change.


## Changing the hub server backend

Edit files in smc-hub, e.g., `hub.coffee`.  Then hit control+c, then run `./start_hub.py` again.  It's slightly faster if you comment out the `./update_schema.coffee` line in `./start_hub.py`, which is safe unless the schema changes.