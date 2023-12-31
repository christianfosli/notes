# Docker quick ref :whale:

* Most used commands: `docker ps`, `docker images`, `docker build`, `docker run`

* Most used docker-run flags: `-it` interactive terminal, `-d` detached (in the background)

* Detach from running container: Ctrl P Q

* Remove all non-running images: `docker rmi $(docker ps -aq)` or `docker image prune -a`

* Check disk usage: `docker system df`

* Exec as specific user: `docker exec -u root -it <containername>`

* Run container with the same network namespace as another:
  `docker run -it --network container:<containername> alpine`
