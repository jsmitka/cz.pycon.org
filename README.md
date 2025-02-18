# PyCon CZ webpage
## How to run on localhost

### Prerequisites
For local development you only need to install Docker. Tested on version 23.0.2. 

For Docker installation manuals check the following links:
* Ubuntu - install Docker engine using the [apt repository](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository) and add user to `docker` group as described [here](https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user) so you can run Docker locally as a non-root user
* Windows & Mac - you can use Docker Desktop, check out [this](https://docs.docker.com/desktop/install/windows-install/) manual for Windows and [this](https://docs.docker.com/desktop/install/mac-install/) for Mac 

### Local setup
1. Build an image
```bash
make build
```
2. Run migrations 
```bash
make migrate
```

[OPTIONAL] 2.2 Import content into Wagtail tables, so not to have empty pages
```bash
make default-content
```

3. Run dev stack
```bash
make up
```

4. You can stop the server by pressing Ctrl+C, optionally you can run 
```bash
make down 
```
if there are any hanging containers

### Admin & WagTail
In case you want to access admin page, either Django or Wagtail one, you need to create a superuser and log in with its credentials:
```bash
make create-user
```

The development server runs at the address http://0.0.0.0:8000/. Beta instance on fly.io runs on https://pycon-cz-beta.fly.dev/team/. 


### Contributing
If you want to contribute, please run `make lint` before pushing BE code to format it. This step will be automated in the future.

### Debugging 
<details>
  <summary>How to restart machine in fly.io if something gets stuck</summary>

```
fly machines list --app pycon-cz-beta-db
fly machines restart machine-id --app pycon-cz-beta-db
```
</details>



