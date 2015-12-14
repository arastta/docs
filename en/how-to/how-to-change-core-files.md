How to change core files?
=========================

While strictly modules, product feeds and extensions should be standalone and modular, some may require modifications to the Arastta core. Modifying Arastta core files greatly reduces your ability to update your store to later versions, and can affect other extensions/themes.

Therefore, Arastta ships with 4 systems:
1. [Translation System](docs/user-manual/system/language-overrides) for language changes
2. [Override System](docs/developers/override-system) for HTML/CSS changes
3. [Event System](docs/developers/event-system) for PHP changes
4. [Modification System](docs/developers/modification-system) for PHP changes

We strongly recommend to use the Event System for PHP changes because with Modifications, if two or more extensions/themes want to change the same code, you will run into conflicts very easily.
