# How to Set Docker Environment ENV Variables?

The ENV instruction sets the environment variable <key> to the value <value>. The environment variables set using ENV will persist when a container is run from the resulting image.

- You can pass ENV variables not only during the image building but also at runtime when your containers are running
- ENV variables are usually your API keys, database URLs, secret keys, etc.
- Like ARG variables, the ENV can also have a default value in the dockerfile. 
- You can override ENV values set in a Dockerfile by providing updated ENV values through your docker-compose.yml file or Docker CLI.


server.js file env has been set *app.listen(process.env.PORT);* that are pass via cli --env-file project root directory.

**Steps 1:** Build docker image.

```
docker build -t ashadozzaman/nodejs:0.1 .
```
`ashadozzaman/nodejs:0.1` from the current directory `(.)` where the Dockerfile is located.

**Steps 2:** Run build image via ENV values

```
docker run -p 8081:8000 -e PORT=8000 ashadozzaman/nodejs:0.1
```
This command runs a Docker container based on the previously built image `(ashadozzaman/nodejs:0.1)`. The `-p` flag maps port `8081` on the host to port `8000` in the container. The `-e` flag sets the environment variable `PORT` to the value `8000`.

#### Alternatively, you can use an environment file (.env) to pass multiple environment variables:
```
docker run -p 8081:8000 --env-file .env ashadozzaman/nodejs:0.1
```
The `--env-file` flag specifies a file (` .env`) containing environment variables, and these variables will be used during the container runtime.

Finally, you can access your Node.js application in a web browser at `http://localhost:8081/` or whatever port you specified in your `Node.js` application.