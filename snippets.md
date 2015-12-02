# Register post types


    if ( ! function_exists('custom_post_type_editions') ) {
    	// Register Custom Post Type
    	function custom_post_type_editions() {
    
    		$labels = array(
    			'name'                  => 'Ausgaben',
    			'singular_name'         => 'Ausgaben',
    			'menu_name'             => 'Ausgaben',
    			'name_admin_bar'        => 'Ausgaben',
    			'parent_item_colon'     => 'Eltern-Element',
    			'all_items'             => 'Alle Elemente',
    			'add_new_item'          => 'Neue Ausgabe hinzufügen',
    			'add_new'               => 'Neue Ausgabe hinzufügen',
    			'new_item'              => 'Neue Ausgabe hinzufügen',
    			'edit_item'             => 'Element bearbeiten',
    			'update_item'           => 'Element aktualisieren',
    			'view_item'             => 'Vorschau',
    			'search_items'          => 'Element suchen',
    			'not_found'             => 'Nicht gefunden',
    			'not_found_in_trash'    => 'Nicht gefunden im Papierkorb',
    			'items_list'            => 'Elementliste',
    			'items_list_navigation' => 'Element Liste Navigation',
    			'filter_items_list'     => 'Filter Elementliste',
    		);
    		$args = array(
    			'label'                 => 'Ausgaben',
    			'description'           => 'Die Ausgaben des Handelsblatt Magazin',
    			'labels'                => $labels,
    			'supports'              => array( 'title', 'editor', 'thumbnail', 'revisions', 'custom-fields', ),
    			'hierarchical'          => false,
    			'public'                => true,
    			'show_ui'               => true,
    			'show_in_menu'          => true,
    			'menu_position'         => 15,
    			'menu_icon'             => 'dashicons-format-aside',
    			'show_in_admin_bar'     => true,
    			'show_in_nav_menus'     => false,
    			'can_export'            => false,
    			'has_archive'           => false,		
    			'exclude_from_search'   => true,
    			'publicly_queryable'    => true,
    			'capability_type'       => 'page',
    		);
    		register_post_type( 'editions', $args );
    
    	}
    	add_action( 'init', 'custom_post_type_editions', 0 );
    }
    
    
# Add custom script
    
    }

    if ( ! function_exists('integrate_base_js') ) {
    	function integrate_base_js() {
    		$basejs = '<script type="text/javascript" src="'.get_template_directory_uri().'-Child/js/base.js"></script>';
    		echo $basejs;
    	}
    }
    
    add_action('wp_head', 'integrate_base_js');
    
    
# Add simple live reload

    
    if ( ! function_exists('integrate_generated_css') ) {
    	function integrate_generated_css() {
    		$base = '<link id="sass" rel="stylesheet" href="'.get_template_directory_uri().'-Child/generated-via-sass.css">';
    		
    		$dev_base = '<!-- DEVLOPMENT ONLY -->
    					<!-- build:css(.tmp) styles/main.css -->
    					<link rel="stylesheet" href="http://localhost:9000/styles/main.css">
    					<!-- endbuild -->
    					<script type="text/javascript" src="http://localhost:9000/browser-sync/browser-sync-client.2.10.0.js"></script>
    					<!-- END DEVLOPMENT ONLY -->';
    		
    		if($_GET["livereload"] != "true") {
    			echo  $base;
    		} else {
    			echo $dev_base;
    		}
    
    	}
    }
    add_action('wp_head', 'integrate_generated_css');


# Add Image sizes

// Image Formate
add_image_size ("magazinformat", 300, 400, false);
add_image_size ("magazinlistenformat", 220, 295, false);
add_image_size ("sliderformatfullwidth", 1155, 530, array('right', 'bottom'));
add_image_size ("sliderformatsmallwidth", 750, 400, array('right', 'bottom'));

