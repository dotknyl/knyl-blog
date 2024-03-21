*---
layout: "../../layouts/PostLayout.astro"
title: "Install TimescaleDB on an existing PostgreSQL container"
description: "I researched TimescaleDB, a powerful database for time-series data. While installing it on an existing container, I encountered a challenge. After experimenting with different methods and configurations, I successfully installed TimescaleDB."
heroImage: "/blog/install-timescaledb-on-an-existing-postgresql-container/Untitled%203.png"
pubDate: "Mar 21 2023"
---
## Table of Contents
- [Introducing](#introducing)
- [Installation](#installation)
  - [Install missing packages for docker container](#install-missing-packages-for-docker-container)
  - [Install TimescaleDB](#install-timescaledb)
    - [Add the TimescaleDB third party repository](#add-the-timescaledb-third-party-repository)
    - [Install Timescale GPG key](#install-timescale-gpg-key)
    - [Update your local repository list and install TimescaleDB](#update-your-local-repository-list-and-install-timescaledb)
  - [Update config settings for TimescaleDB](#update-config-settings-for-timescaledb)
  - [Restart your Docker container to load TimescaleDB](#restart-your-docker-container-to-load-timescaledb)
  - [Add TimescaleDB extension](#add-timescaledb-extension)
    - [Log in to psql again](#log-in-to-psql-again)
    - [Create a new database or switch to an existing one](#create-a-new-database-or-switch-to-an-existing-one)
    - [Create the TimescaleDB extension](#create-the-timescaledb-extension)
    - [Check that the TimescaleDB extension is installed](#check-that-the-timescaledb-extension-is-installed)
- [Summary](#summary)


## Introducing

I have been conducting extensive research on TimescaleDB, a powerful relational database that is designed to handle time-series data. As part of my research, I recently encountered a challenge when trying to install TimescaleDB on an existing container. Despite initially struggling, I spent a considerable amount of time experimenting with different installation methods and configurations, and ultimately, I was able to successfully install TimescaleDB on my container.

## Installation

We have an existing Postgres container with resources that we cannot override, such as our databases, and installed extensions. Since we cannot use `sudo` on the docker terminal and some packages required for TimescaleDB installation are missing, I customized the installation process. Here are the steps I took:

**1. Install missing packages for docker container**

```bash
apt-get update
apt-get install gnupg postgresql-common apt-transport-https lsb-base lsb-release wget
```

You may receive a notification, in which case you can choose to install the package maintainer's version by selecting `1` from the options. While it is not entirely clear what this option does, I tried it and it worked :)

![Untitled](/blog/install-timescaledb-on-an-existing-postgresql-container/Untitled.png)

**2. Install TimescaleDB**
- Add the TimescaleDB third party repository:

```bash
echo "deb https://packagecloud.io/timescale/timescaledb/debian/ $(lsb_release -c -s) main" | tee /etc/apt/sources.list.d/timescaledb.list
```

- Install Timescale GPG key:

```bash

wget --quiet -O - https://packagecloud.io/timescale/timescaledb/gpgkey | apt-key add -
```

- Update your local repository list and install TimescaleDB:

```bash
apt-get update #Make sure your apt repository is up to date:
apt install timescaledb-2-postgresql-13 # based on PG version
apt-get install postgresql-client-13
apt-get update
```

![Untitled](/blog/install-timescaledb-on-an-existing-postgresql-container/Untitled%201.png)

**3. Update config settings for TimescaleDB**

In this step, you need to add TimescaleDB to `shared_preload_libraries`. To avoid overriding current `shared_preload_libraries` settings, follow these steps to edit them:

- To display the `shared_preload_libraries` settings in a container terminal, first log in to psql.

```bash
psql -U postgres -h localhost
```

- Run this command:

```sql
show shared_preload_libraries;
```

![Untitled](/blog/install-timescaledb-on-an-existing-postgresql-container/Untitled%202.png)

- I have previously added `pg_stat_monitor`, so I need to expand my preload libraries:

```bash
ALTER SYSTEM SET shared_preload_libraries ='timescaledb','pg_stat_monitor';
```

**4. *Now, you need to restart your Docker container to load TimescaleDB.***

**5. Add TimescaleDB extension**
- Log in to psql again:

```bash
psql -U postgres -h localhost
```

- Create a new database or switch to an existing one.

```sql
CREATE database tsdb;
\c tsdb # switching to tsdb 
```

- Create the TimescaleDB extension.

```sql
CREATE EXTENSION IF NOT EXISTS timescaledb;
```

- Here are our results:

![Untitled](/blog/install-timescaledb-on-an-existing-postgresql-container/Untitled%203.*png*)

- Check that the TimescaleDB extension is installed by using the `\dx` command at the `psql`
 prompt:

![Untitled](/blog/install-timescaledb-on-an-existing-postgresql-container/Untitled%204.png)

## Summary

By following these steps, you can successfully set up TimescaleDB for time-series data in your PostgreSQL container. Finally, you can start ingesting time-series data into your PostgreSQL container using TimescaleDB's specialized functions and operators. This allows you to analyze and visualize your data in new and exciting ways. I hope this article is helpful for you.