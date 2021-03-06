# Habilitando Twig Debug (Forma manual).

Para habilitar la informacion de `debug` de twig sigue los siguientes pasos:

  1. copia `sites/example.settings.local.php` y pega como `sites/default/settings.local.php`, modifica permisos si es necesario.
  	- 2.1 si usas la terminal cambia los permisos en el folder default usando `chmod 775 sites/default` y `chmod 775 sites/default/settings.php` o `chmod 775 -R sites/default`
  2. ve a `settings.php` dentro de `sites/default/settings.php`, busca y quita los comentarios de las siguientes lineas.

  	```php
  	# if (file_exists(__DIR__ . '/settings.local.php')) {
    #   include __DIR__ . '/settings.local.php';
	  # }
  	```
  	tiene que quedar asi:

  	```php
  	if (file_exists(__DIR__ . '/settings.local.php')) {
	     include __DIR__ . '/settings.local.php';
	  }
  	```  
3. borra las caches.
4. Ubica el archivo `sites/default/default.services.yml` duplicalo y nombralo `sites/default/local.services.yml`
5. Dentro del `settings.local.php` Checa que la siguiente linea no este comentada:

	```
	$settings['container_yamls'][] = DRUPAL_ROOT . '/sites/development.services.yml';
	```
	
5.1 - abre `settings.php`
	
	
	$settings['container_yamls'][] = __DIR__ . '/local.services.yml';
	```
6. Abre `local.services.yml` cambia las siguientes configuraciones:

	```
	[...]
	twig.config:
	[...]
    	debug: true
    	cache: false
   ```
7. Borra caches.

# Habilitando twig debug con drupal console
Para efctos prácticos, también se puede correr un comando de [DrupalCnsole](https://drupalconsole.com/ "Drupal Console").

	```
	drupal site:mode dev
	
	```

# Deshabilitando las caches por completo.

Nesecitas haber completado los pasos anteriores.

1. abre el archivo `settings.local.php` y quita los comentarios a las siguientes lineas.

	```
	# $settings['cache']['bins']['render'] = 'cache.backend.null';

	# $settings['cache']['bins']['dynamic_page_cache'] = 'cache.backend.null';
	```
	quedara asi:

	```
	$settings['cache']['bins']['render'] = 'cache.backend.null';

	$settings['cache']['bins']['dynamic_page_cache'] = 'cache.backend.null';
	```

2. borra las caches.
