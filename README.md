<h1 align="center">
    homer-themed
</h1>

<h4 align="center">
A simple static home page to access shortcut to all your home-lab services and can easily configurable with <code>yaml</code> file.
</h4>
<br />
<br />
<h2 align="center">Credits [100%]</h2>

The complete codebase is based on work done under following two repos:-
- [Homer Dashboard](https://github.com/bastienwirtz/homer)
- [Homer Theme v2](https://github.com/walkxcode/homer-theme)

I merely combined them to just simplify things for my personal use. All credit goes to them. </h4> 
<br />
<br />
<h2 align="left">Summary of changes</h2>

- Modified Dockerfile to build the docker image with pre-applied  [Homer Theme v2](https://github.com/walkxcode/homer-theme) on [Homer Dashboard](https://github.com/bastienwirtz/homer)
- Added some commonly used icons and shortcuts

<h2 align="left">Preview</h2>

<p align="center">
Dark Mode
<img alt="Homer Theme" src="https://raw.githubusercontent.com/apurbagiri/homer-themed/main/preview-dark.png">
</p>
<p align="center">
  Light Mode
   <img alt="Homer Theme" src="https://raw.githubusercontent.com/apurbagiri/homer-themed/main/preview-light.png">
</p>
 

<br /><br />
## Features
The application packs quite a few features. Instead of copying more stuff here, I would suggest going over to [bastienwirtz/homer](https://github.com/bastienwirtz/homer) and read all about it. 

<br /><br />

### Using docker

Docker-hub location: [apurba/homer-themed](https://hub.docker.com/repository/docker/apurba/homer-themed )

To launch container:

```
docker run -d -p 8090:8080 -v </your/local/assets/>:/www/assets --restart=always apurba/homer-themed:latest
```
<br /><br />

### docker-compose

Add the equivalent of following in `docker-compose.yml` 

```yaml
  homer:
    image: "apurba/homer-themed:latest"
    container_name: homer
    environment:
      - UID=${PUID}
      - GID=${PGID}
    volumes:
      - ${USERDIR}/docker/homer/www/assets:/www/assets
    ports:
      - 8090:8080
    restart: always
```

To launch container:

```sh
sudo docker-compose -f ~/docker/docker-compose.yml up -d
```

Please note that configurations above would require some changes based on your own server configuration, env variables and docker setup.

<br /><br />
Finally, the **Homer Dashboard** page should be accessible under following URL:

<code>http://<server-ip-address:8090></code>

<br /><br />

### Build your custom docker image
- Clone this repo
- Modify <code>/theme/assets/config.yml</code> under this repo
	- You can run this container first and modify <code>/docker/homer/www/assets/config.yml</code> within container
	- Reload the dashboard to see if modification is to your liking (browser might cache old data, so clear cache if changes aren't reflected or simply use new incognito after each change)
- Add/remove any logos necessary inside <code>/theme/assets/tools</code>
- For advance configuration, visit [original author's](https://github.com/walkxcode) [configuration page](https://github.com/walkxcode/homer-theme/blob/main/docs/extra-configuration.md)
- Run following docker command to build the new image:-

	```sh
	docker build . -t dockerid/container-name:versiontag
	```

<br /><br /><br />

### LICENSE NOTICE

- [Homer Dashboard](https://github.com/bastienwirtz/homer) is licensed under **Apache License 2.0** | Copyright 2018 Bastien Wirtz
You may not use this file except in compliance with the License. You may obtain a copy of the License [here](https://github.com/apurbagiri/homer-themed/blob/main/HOMER-LICENSE)
	
- [Homer Theme v2](https://github.com/walkxcode/homer-theme) is licensed under **MIT License** | Copyright (c) 2021 Walkx
You may not use this file except in compliance with the License. You may obtain a copy of the License [here](https://github.com/apurbagiri/homer-themed/blob/main/HOMER-THEME-LICENSE)
