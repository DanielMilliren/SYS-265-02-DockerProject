# Gerrit Docker Compose Project SYS-265-02

I decided to have my project be git + gerrit as a docker service. This uses five folders stored in the same folder as compose.yaml for external volumes, and it works quite well. The install instructions are as follows:

- Run `sudo docker compose up` in the folder this project is in.
- Once docker exits, change `command: init` to `#command: init` in compose.yaml.
- Run `sudo docker compose up -d` in this folder.
- Create a git project on your client.
- On this gerrit server, run `cd gerrit/git` from the folder this file is in.
- Initialize a matching git project in ./gerrit/git as follows: `GIT_DIR=Your_Project.git git init`
- On your client's end, type `git push admin@your_gerrit_server.example.local:/<this_directory>/gerrit/git/Your_Project.git main`. `main` can be whatever your default branch's name is.
- On this server, go back to this directory via `cd ../..` and run `sudo docker compose restart`.
- Your changes will now show at `http://your_gerrit_server.example.local:8080`.

This is for SYS-265-02 at Champlain College.

