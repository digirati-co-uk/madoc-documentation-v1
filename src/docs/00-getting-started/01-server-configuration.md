---
name: Server configuration
order: 1
---

# Server configuration
Before you set up your platform, you will want to ensure that you change the default passwords.

## MySQL
In the `madoc-example-config` there is a file called `.env`, by default it will look something like:

```
# MySQL
MYSQL_DATABASE=omeka_s
MYSQL_USER=omeka_s
MYSQL_PASSWORD=Password123
MYSQL_PORT=3306

# Omeka
APP_ENV=dev
MAIN_SITE_DOMAIN=http://localhost:8898/
ELUCIDATE_URL=example-annotation-server:8080
ELUCIDATE_PUBLIC_DOMAIN=http://localhost:8898/
```

You should change the password here to something secret and secure. 

## Omeka configuration
For more advanced configurations, you may want to configure Omeka or our modules themselves using code. You can `COPY` in extra configuration files in the docker file in the example configuration.

### Adding Zend modules
<div class="fesk-info fesk-info--warning">
  Do not remove modules that are already configured here, it may break aspects of the platform.
</div>

You can add Zend modules here, this may be a requirement of a 3rd party Omeka module. Its not recommended to use this method for adding new Zend modules to your Omeka build.

### Thumbnail sizes
By default we ship with 3 thumbnail variants. Large, medium and square. These are used around the platform to showcase IIIF content.

This too is where you can add custom image-magic parameters. Full documentation can be found in Omeka-S documentation.

```
'thumbnails' => [
    'types' => [
        'large' => ['constraint' => 1024],
        'medium' => ['constraint' => 512],
        'square' => ['constraint' => 256],
    ],
    'thumbnailer_options' => [
        'imagemagick_dir' => null,
    ],
],
```

All thumbnail sizes are in pixels. If you put very large values here it will slow down the generation of IIIF thumbnails.

### Mount volume of modules
You have 4 main options for using custom modules. You can ssh into the container and install the modules in place. This may not persist if you rebuild the images. You may be able to use `docker-compose commit` to save those changes. The second is to use volumes to individually volume modules into the module directory:
```
    volumes:
      - ./path/to/my-module:/srv/omeka/modules/my-module
```

The 3rd way, which may be better if you have lots of modules is to configure another module path in the `application.config.php`:
```diff
 'module_listener_options' => [
        'module_paths' => [
            'Omeka' => OMEKA_PATH . '/application',
             OMEKA_PATH . '/modules',
+            OMEKA_PATH . '/custom-modules',
        ],
        'config_glob_paths' => [
            OMEKA_PATH . '/config/local.config.php'
        ]
    ],
```

Lastly, you can create a new Dockerfile and extend the Omeka docker file and add a step to copy modules into place. This is not documented, but you can find information on this process in the [Docker documentation](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)

## Elucidate annotation server

The annotation server also comes with configuration inside the docker container. You should refer to the [Elucidate Server](https://github.com/dlcs/elucidate-server) for more details.
