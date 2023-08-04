# WPAdminAssetsJSCSS
WP JS/CSS Installation enqueue admin

```PHP
// Plugin admin area no framework or boilerplate! 
// Admin CSS / Stlesheets 
add_action( 'admin_enqueue_scripts', 'myplugin_enqueue_style_admin' );
function myplugin_enqueue_style_admin() {
	
  /*
   wp_enqueue_style(
     string           $handle,
     string           $src = '',
     array            $deps = array(),
     string|bool|null $ver = false,
     string           $media = 'all'
   )
 */
	
  $src = plugin_dir_url( __FILE__ ) .'admin/css/example-admin.css';
  
  wp_enqueue_style( 'myplugin-admin', $src, array(), null, 'all' );

}
```

```PHP
// Plugin admin area no framework or boilerplate! 
// Admin JS / script
add_action( 'admin_enqueue_scripts', 'myplugin_enqueue_script_admin' );
function myplugin_enqueue_script_admin() {
	
  /*
	  wp_enqueue_script(
	  string           $handle,
	  string           $src = '',
	  array            $deps = array(),
	  string|bool|null $ver = false,
	  bool             $in_footer = false
	   )
	*/
	
	$src = plugin_dir_url( __FILE__ ) .'admin/js/example-admin.js';

	wp_enqueue_script( 'myplugin-admin', $src, array(), null, false );
}
```

```PHP
// Admin Specific page
add_action( 'admin_enqueue_scripts', 'myplugin_enqueue_style_admin_pages' );
function myplugin_enqueue_style_admin_pages( $hook ) {

  // wp_die( $hook );

  if ( 'edit.php' === $hook ) {

    $src = plugin_dir_url( __FILE__ ) .'admin/css/example-admin.css';

    wp_enqueue_style( 'myplugin-admin-pages', $src, array(), null, 'all' );

  }
  
}
```

<br /> Also : 
<br /> Admin inline script : https://developer.wordpress.org/reference/hooks/admin_print_scripts/
<br /> Admin inline style: https://developer.wordpress.org/reference/hooks/admin_print_style/

```PHP
function admin_inline_js(){ 
   echo "<script type='text/javascript'>\n";
   echo "alert('Only in Admin this inline script')";
   echo "\n</script>"; 
} 
add_action( 'admin_print_scripts', 'admin_inline_js' );
```
