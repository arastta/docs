Admin Menu
==========

Since 1.1 version, Arastta has introduced a new event to interfere the admin menu. Before 1.1, developers had to hack the HTML using vQmod/OCmod in order to add something to the admin menu. This event prevents conflicts between 3rd party developers. Don't forget to check how the [Event System](http://arastta.org/docs/developers/event-system) of Arastta works first.

Example
-------

```
<?php

class EventAppDemo extends Event {

	public function preAdminMenuRender(&$menu) {
		$p_test = $this->user->hasPermission('access','catalog/category');
		$p_test2 = $this->user->hasPermission('access','catalog/product');
		$p_test3 = $this->user->hasPermission('access','catalog/information');

		// Top menu
		$menu->addMenuItem('test', 'Test', $this->url->link('test/test', 'token=' . $this->session->data['token'], 'SSL'), '', $p_test, 'fa-check', 1);

		// Sub menu 1st level
		$menu->addMenuItem('test2', 'Test Submenu', $this->url->link('test/test2', 'token=' . $this->session->data['token'], 'SSL'), 'test', $p_test2, '',  1);

		// Sub menu 2nd level
		$menu->addMenuItem('test3', 'Test Submenu 2', $this->url->link('test/test3', 'token=' . $this->session->data['token'], 'SSL'), 'test2', $p_test3, '',  1);
	}
}
```