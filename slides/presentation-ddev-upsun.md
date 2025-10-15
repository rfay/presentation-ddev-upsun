# **Upsun & DDEV Integration with ddev-upsun Add-on**

<img src="images/upsun.svg" alt="UPSUN Logo" class="upsun-logo">
<img src="images/ddev-logo.svg" alt="DDEV Logo" class="ddev-logo">

---

## What We Have In Code

* Working Drupal 11 Repository in GitHub: https://github.com/ddev/ddev-upsun
* Basic composer-built Drupal 11 site with drush, opensearch, memcached
* `demo_umami` install

---

## What We Have On Upsun

* Upsun site: https://console.upsun.com/ddev/dsatecjxcdp24 (`dsatecjxcdp24`)
* Built with normal Upsun Drupal instructions
* `.environment` for mappting configuration variables
* `.upsun/config.yaml`
* `settings.upsun.php`

---

## What We're going to do

1. Clone the project from GitHub. 
2. `upsun project:set-remote dsatecjxcdp24` to set up the remote config
3. `ddev config --docroot=web --project-type=drupal11` just for basic DDEV configuration
4. Add `.ddev/.env`:
```env
PLATFORM_PROJECT=dsatecjxcdp24
PLATFORM_ENVIRONMENT=main
PLATFORM_PRIMARY_RELATIONSHIP=mariadb
```

---

## `ddev-upsun` setup

```
ddev add-on get ddev/ddev-upsun
```

* Necessary database type and version are detected
* Dependencies are added (`opensearch`, `memcached`)
* Configuration is used via `.environment` and `settings.upsun.php`

---

## Get the database and files

* `ddev start`
* `ddev pull upsun` or `upsun db:dump` and load with `ddev import-db`
* `ddev drush cim`

---

## What we have now

* Local Drupal11 site which tries to imitate and use Upsun configuration
* Discovered dependent add-ons installed
* Local project ready for development. `ddev drush cex` and commit results when needed.

## Resources

* Add-on: https://github.com/ddev/ddev-upsun
* DDEV: https://ddev.com/get-started/
* Drupal on Upsun Flex: https://docs.upsun.com/get-started/stacks/drupal.html
* DDEV Discord: https://ddev.com/s/discord