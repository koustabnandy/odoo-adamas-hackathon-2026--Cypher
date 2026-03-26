IceHrm
===========

IceHrm is an [HRM software](https://icehrm.com) which enable companies to manage employee details and HR workflows.

## Installation

### Setup a Linux Server and Install IceHrm
- Please check [Installation guide](https://icehrm.com/docs/installation/install-linux).

### Installation using Docker

- Install docker on Mac, Windows or Linux [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/)
- Download the [latest version of IceHrm](https://github.com/gamonoid/icehrm/releases/latest) and extract it.
- Alternatively you can cone the repo `git clone https://github.com/gamonoid/icehrm.git`
```
cd icehrm
npm run setup
npm run docker:build
npm run docker:start
```

- Visit [http://localhost:3128/](http://localhost:3128/) and login using `admin` as username and password.
- Visit [http://localhost:3130/](http://localhost:3130/) to access phpmyadmin.
- All user uploaded files are stored under `icehrm/docker/production/app_data`

### Update your existing IceHrm installation to the latest version

- CD into the IceHrm installation directory (e,g `cd /var/www/icehrm`)
- Run `npm install -g icehrm-update`
- If you get an error due to not having Node.js installed use instructions in [Node.js download page](https://nodejs.org/en/download) to install it first.
- Then run `icehrm-update`

This will update your IceHrm installation to the latest version


### Useful Links
* IceHrm Opensource Blog: [http://icehrm.org](http://icehrm.org)
* IceHrm Cloud Hosting: [https://icehrm.com](https://icehrm.com)
* IceHrm Documentation (Opensource and Commercial): [https://icehrm.com/explore/docs/](https://icehrm.com/explore/docs/)
* IceHrm Blog: [https://icehrm.com/blog](http://icehrm.com/blog)
* Purchase Extensions: [https://icehrm.com//buy-icehrm-modules](https://icehrm.com//buy-icehrm-modules)
* Report Issues: [https://github.com/gamonoid/icehrm/issues](https://github.com/gamonoid/icehrm/issues)

### Check Out our Sponsors
* Monitor your IceHrm with [uptimely.cloud](https://uptimely.cloud/?utm_source=icehrm_readme&utm_medium=referral)

