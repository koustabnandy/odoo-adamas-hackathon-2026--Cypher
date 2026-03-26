IceHrm
===========

IceHrm is an [HRM software](https://icehrm.com) which enable companies to manage employee details and HR workflows.

## Installation

### Setup a Linux Server and Install IceHrm
- Please check [Installation guide](https://icehrm.com/docs/installation/install-linux).

### Installation using Docker

#### Prerequisites

Install Docker on your system. See [Docker Installation Guide](docs/docker-installation.md) for detailed instructions for macOS, Windows, and Linux.

#### Quick Start (Production)

```bash
# Clone the repository
git clone https://github.com/gamonoid/icehrm.git
cd icehrm

# Start IceHrm
docker compose -f docker-compose-prod.yaml up -d
```

Visit [http://localhost:5555](http://localhost:5555) and login with username `admin` and password `admin`.

#### Configuration (Optional)

To customize your installation, create a `.env` file:

```bash
cp docker-prod.env.example .env
```

Edit `.env` to change settings:

```env
# Port where IceHrm will be accessible
APP_PORT=5555

# Base URL (change for production domain)
APP_BASE_URL=http://localhost:5555

# Database credentials (change these in production!)
DB_HOST=mysql
DB_NAME=icehrm
DB_USER=icehrm
DB_PASSWORD=your_secure_password
DB_ROOT_PASSWORD=your_secure_root_password
```

Then restart the containers:

```bash
docker compose -f docker-compose-prod.yaml down
docker compose -f docker-compose-prod.yaml up -d
```

#### Using an External Database

To connect IceHrm to an external MySQL database (e.g., AWS RDS, Azure Database, or your own MySQL server):

1. Create a `.env` file with your external database settings:

```env
APP_PORT=5555
APP_BASE_URL=http://localhost:5555

# External database configuration
DB_HOST=your-database-host.example.com
DB_NAME=icehrm
DB_USER=your_db_user
DB_PASSWORD=your_db_password
```

2. Import the database schema to your external database:

```bash
mysql -h your-database-host.example.com -u your_db_user -p icehrm < docker/init.sql
```

3. Start only the application containers (without the bundled MySQL):

```bash
docker compose -f docker-compose-prod.yaml up -d icehrm icehrm-worker
```

#### Docker Services

| Service | Description | Port |
|---------|-------------|------|
| icehrm | Main application | 5555 |
| mysql | Database server | - |
| icehrm-worker | Background jobs | - |

#### Data Persistence

All data is persisted in Docker volumes:
- `icehrm-mysql-data` - Database files
- `icehrm-app-data` - Uploaded files and logs

#### Stopping IceHrm

```bash
docker compose -f docker-compose-prod.yaml down
```

#### Viewing Logs

```bash
docker compose -f docker-compose-prod.yaml logs -f
```

### Deploy to Render

IceHrm can be deployed to [Render](https://render.com) using the included `render.yaml` blueprint.

#### Prerequisites

Since Render doesn't offer managed MySQL, you'll need an external MySQL database:
- [PlanetScale](https://planetscale.com) (recommended, has free tier)
- [AWS RDS](https://aws.amazon.com/rds/mysql/)
- [DigitalOcean Managed MySQL](https://www.digitalocean.com/products/managed-databases-mysql)

#### Deployment Steps

1. **Create a MySQL database** with your chosen provider

2. **Import the IceHrm schema** to your database:
   ```bash
   mysql -h <host> -u <user> -p <database> < docker/init.sql
   ```

3. **Fork this repository** to your GitHub account

4. **Deploy to Render:**
   - Go to [Render Dashboard](https://dashboard.render.com/blueprints)
   - Click **New Blueprint Instance**
   - Connect your forked repository
   - Set the required environment variables:
     - `APP_BASE_URL` - Your Render app URL (e.g., `https://icehrm-xxx.onrender.com`)
     - `DB_HOST` - Your MySQL host
     - `DB_USER` - Database username
     - `DB_PASSWORD` - Database password

5. **Deploy** and wait for the services to start

6. **Access IceHrm** at your Render URL and login with `admin` / `admin`

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

