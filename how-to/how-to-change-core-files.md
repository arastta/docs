How to change core files?
=========================

While strictly modules, product feeds and extensions should be standalone and modular, some require modifications to the Arastta core. Modifying Arastta core files greatly reduces your ability to update your store to later versions, and can affect other modules and extensions.

Therefore, Arastta comes with 3 systems:
1. [Override System](docs/developers/override-system)
2. [Event System](docs/developers/event-system)
3. [Modification System](docs/developers/modification-system)

You should use:
* Override System for HTML and/or CSS changes
* Event System (recommended) and/or Modification System for PHP changes
