<div align="center">

[<img src="https://github.com/sapthesh/Bhadoo-Cloud/blob/master/static/logo.png" data-canonical-src="https://github.com/sapthesh/Bhadoo-Cloud/blob/master/static/logo.png" height="80" />](https://github.com/sapthesh/Bhadoo-Cloud)

Fetch Torrents using .torrent file or Magnet Links, Fetch Files from Other Servers to Own Server and Upload to Google Drive.

Open URLs in Proxy to bypass Restrictions (works like VPN), Check [Demo](http://#) 

<img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/sapthesh/Moquee-Cloud">
<a href="https://github.com/sapthesh/Moquee-Cloud/issues"><img alt="GitHub issues" src="https://img.shields.io/github/issues/sapthesh/Moquee-Cloud"></a>
<a href="https://github.com/sapthesh/Moquee-Cloud/network"><img alt="GitHub forks" src="https://img.shields.io/github/forks/sapthesh/Moquee-Cloud"></a>
<a href="https://github.com/sapthesh/Moquee-Cloud/blob/master/LICENSE"><img alt="GitHub license" src="https://img.shields.io/github/license/sapthesh/Moquee-Cloud"></a>
<img alt="GitHub repo size" src="https://img.shields.io/github/repo-size/sapthesh/Moquee-Cloud">


[![Docker Cloud Automated build](https://img.shields.io/docker/cloud/automated/parveenbhadoo/bhadoocloud.svg)](https://hub.docker.com/r/parveenbhadoo/bhadoocloud)
[![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/parveenbhadoo/bhadoocloud.svg?style=flat)](https://hub.docker.com/r/parveenbhadoo/bhadoocloud)
[![Docker Pulls](https://img.shields.io/docker/pulls/parveenbhadoo/bhadoocloud.svg)](https://hub.docker.com/r/parveenbhadoo/bhadoocloud)
[![Docker Stars](https://img.shields.io/docker/stars/parveenbhadoo/bhadoocloud.svg)](https://hub.docker.com/r/parveenbhadoo/bhadoocloud)
[![Docker Size](https://images.microbadger.com/badges/image/parveenbhadoo/bhadoocloud.svg)](https://hub.docker.com/r/parveenbhadoo/bhadoocloud)
[![Docker Version](https://images.microbadger.com/badges/version/parveenbhadoo/bhadoocloud.svg)](https://hub.docker.com/r/parveenbhadoo/bhadoocloud)

[![GitHub repo size](https://img.shields.io/github/repo-size/parveenbhadooofficial/bhadoocloud.svg)](https://hub.docker.com/r/parveenbhadoo/bhadoocloud)
[![Build Status](https://travis-ci.org/ParveenBhadooOfficial/Bhadoo-Cloud.svg?branch=master)](https://travis-ci.org/ParveenBhadooOfficial/Bhadoo-Cloud)
[![GitHub last commit](https://img.shields.io/github/last-commit/parveenbhadooofficial/bhadoocloud.svg)](https://hub.docker.com/r/parveenbhadoo/bhadoocloud)
[![](https://data.jsdelivr.com/v1/package/gh/ParveenBhadooOfficial/BhadooCloud/badge?style=rounded)](https://www.jsdelivr.com/package/gh/ParveenBhadooOfficial/BhadooCloud)
[![GitHub](https://img.shields.io/github/license/ParveenBhadooOfficial/Bhadoo-Cloud)](https://github.com/ParveenBhadooOfficial/Bhadoo-Cloud)

</div>

[![screenshot](https://raw.githubusercontent.com/ParveenBhadooOfficial/Bhadoo-Cloud/master/.github/screenshot02.png)](https://github.com/ParveenBhadooOfficial/Bhadoo-Cloud)

# Usage

Info: Heroku is not supported, Use AWS EC2 (1 Year Free), G Cloud (300$ for 1 Year Free), MS Azure (30 Days Free) for Bhadoo Cloud Installations.

Installation on [AWS Cloud](https://aws.amazon.com/ec2/)

* [Check Out the Video](#resources)
* Select an Ubuntu 18.xx Server Image
* Use [Putty](https://www.putty.org/) to Login using SSH
* Follow the below commands one by one.

```
  sudo apt-get update && sudo apt-get upgrade
  sudo apt-get install linux-image-extra-virtual
```

```
  sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```

```
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

```
  sudo apt-key fingerprint 0EBFCD88
```

```
  sudo add-apt-repository \
     "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
     $(lsb_release -cs) \
     stable"
```

```
  sudo apt-get update
```

```
  sudo apt-get install docker-ce
```

```
  sudo docker run hello-world
```

* You'll see a Line saying Hello World that means everything you've done worked till now

```
  sudo usermod -a -G docker $USER
```

* Replace `$USER` with your username, it maybe be `ubuntu` by default.
* Close Putty and Login again.
* For Stable Installation (Recommended)

```
  docker run --name ct -d -p 80:3000 \
    --restart always \
    -e GOOGLE_CLIENT_ID='***' -e GOOGLE_CLIENT_SECRET='***' -e GOOGLE_REDIRECT_URL='***/oauthCallback' \
    parveenbhadoo/bhadoocloud:stable node server/server.js
```

* For Latest Installation (Experimental, may not work)

```
  docker run --name ct -d -p 80:3000 \
    --restart always \
    -e GOOGLE_CLIENT_ID='***' -e GOOGLE_CLIENT_SECRET='***' -e GOOGLE_REDIRECT_URL='***/oauthCallback' \
    parveenbhadoo/bhadoocloud node server/server.js
```

Fill `***` with appropriate values from Google Developer Console.

* You can also Delete the Container using below if needed.

```
  sudo docker stop $(docker ps -a -q)
  sudo docker rm $(docker ps -a -q)
```

* You can also remove pulled image to pull latest image again.

```
  sudo docker images -a
  
  sudo docker rmi Image Image2
```

Replace Image with Docker Image ID (Multiple Supported)

# Install on AWS Lightsail

* This will install and deploy (GDrive won't work)

```
bash <(curl -s https://raw.githubusercontent.com/ParveenBhadooOfficial/Bhadoo-Cloud/master/aws-lightsail-install.sh)
```

* This will install requirements only (edit next command with required details)

```
bash <(curl -s https://raw.githubusercontent.com/ParveenBhadooOfficial/Bhadoo-Cloud/master/aws-lightsail-install-advanced.sh)
```

* Fill *** with required details first

```
sudo docker run --name ct -d -p 80:3000 --restart always -e GOOGLE_CLIENT_ID='***' -e GOOGLE_CLIENT_SECRET='***' -e GOOGLE_REDIRECT_URL='***/oauthCallback' parveenbhadoo/bhadoocloud node server/server.js
```

# Get Google_Client_ID and Secret

* Open [Google Dev Credentials Site](https://console.developers.google.com/apis/credentials).
* Create a Project, name as you like.
* Enable [Drive API](https://console.developers.google.com/apis/library/drive.googleapis.com)
* In [Credentials Page](https://console.developers.google.com/apis/credentials) Click `Create Credentials` and then Click `OAuth Client ID`.
* Select Web Application.
* In `Authorized JavaScript origins` enter your domain name or IP whichever you are using for Bhadoo Cloud.
* In `Authorized redirect URIs` enter your domain name or IP with `/oauthCallback` at last.
* Use http:// or https:// as available.
* If you are using Cloudflare for website use https:// and Set Flexible HTTPS in Cloudflare.
* Copy your details and use above.
* `GOOGLE_REDIRECT_URL` is same as `Authorized redirect URIs`



Build from [github.com/Mrigank11/embetacloud](https://github.com/Mrigank11/embetacloud) and [github.com/jpillora/cloud-torrent](https://github.com/jpillora/cloud-torrent)

Forked from (https://github.com/ParveenBhadooOfficial/BhadooCloud/)

License [GPLv3](https://github.com/ParveenBhadooOfficial/BhadooCloud/blob/master/LICENSE)

Contributions are Welcome.

## Donate for Public Server Maintenance

#[<img src="https://raw.githubusercontent.com/ParveenBhadooOfficial/Bhadoo-Cloud/master/files/paypal.png">](#)
#[<img src="https://raw.githubusercontent.com/ParveenBhadooOfficial/Bhadoo-Cloud/master/files/paytm.webp" width="147">](#)


Document Last Updated on 01:04 pm Friday, 13 June 2020 (IST).
