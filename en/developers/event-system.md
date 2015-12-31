Event System
============

Code level changes can easily conflict, if two or more extensions/themes want to change the same code you will run into conflicts very easily. Using Events you reduce this risk as each portion of code is isolated that does not modify any core code.

The event system in Arastta offers a flexible method for extensions/themes to communicate with others by following the [Observer pattern](http://en.wikipedia.org/wiki/Observer_pattern). This pattern is most easily described as a simple communication mechanism. The basic premise is that zero or more "observers" or "listeners" register themselves with the system for a certain, known event. During a specific point in an application's lifecycle, the communicator (in our case system, extension, theme) fires an event, passing some information to all the observers (listeners). The observers can then act on the information passed to them and optionally return a result to the point of trigger.

[Here](https://github.com/arastta/arastta/wiki/Event-List) you can find the list of events fired by Arastta.


Background
----------

### Event implementation

Arastta implements the Observer pattern at a global level through the **Event** and **Trigger** classes. Anyone wanting to receive notification of events will create a class that extends the Event class. Subclasses of Event will automatically register themselves to the global Trigger class when their event folder has been loaded (more on that later). The Trigger class is used as a dispatching mechanism that receives events from the communicators and forwards them on to the listeners that have been loaded.

### Why include listeners

There may be times in your extension's lifecycle when it would be nice to notify others that some action has taken place. For example, let's say you have a compact disk (CD) library extension. You may decide that you would like to let others know when a new CD has been added to the library. In this case, you could document a well known event (*pre.admin.cd.add* for example) and at the appropriate time, trigger the event passing in information about the new CD that was added to the library. All extensions/themes that have implemented that event will be notified with the information and can handle it as they see fit. Instant communication!


Implementation
--------------

### How to become a listener

Since all the dispatching is handled by Arastta, it is easy to become a listener. All you have to do is to put a class file into the "proper" or "app" folder under the "event" directory. Let's continue with CD example handled above. Suppose that the **pre.admin.cd.add** event is being fired from the the following file:

```
admin/model/module/cd_library.php
```

In order to listen that event, the listener file/class must be into one the following folders:

```
admin/event/module/
admin/event/app/
```

**module** is the "proper" folder mentined above and comes from the file path that fired the event.

**app** folder is general folder. Listeners under that folder can listen all of the events, no matter from where they're being fired.

You can also add custom folders located under the *event* folder, before triggering the event:

```
$this->trigger->addFolder('myfolder');
```

You're totally free with the file name and so on the suffix of the class, the trigger system will fire all of the files/listeners under the "proper" and "app" folders.

A listener file/class can listen unlimited events.

### How to create the listener file/class

The file and class must follow the [Coding Standards](https://github.com/arastta/arastta/wiki/Coding-Stardards#file-naming) of Arastta as in example:

```
admin/event/module/foo.php
```

```
class EventModuleFoo extends Event {

    public function preAdminCdAdd(&$artist, $producer) {
        $artist['name'] = 'My Foo ' . $producer['name'];
    }
}
```

As shown above, the *pre.admin.cd.add* turned into *preAdminCdAdd* as event. Because of the $artist variable is being [passed by reference](http://php.net/manual/en/language.references.pass.php), the original source will be automatically changed. In our case, we're changing the artist name of the CD before being stored in library/database!

The *Event* class is similar as Controller/Model so you can use registry/config there.

Check out the examples included into Arastta to under the system:

```
admin/event/app/demo.php
admin/event/catalog/demo.php
catalog/event/account/demo.php
```

### How to fire events

Triggering events is pretty easy thanks to the Trigger class as shown via the following code:

```
$results = $this->trigger->fire('pre.admin.cd.add', array(&$artist, $producer));
```

Events can be fired only from controller and/or model files.

Here we have passed in the artist and producer of the CD. Which and how many parameters you pass is up to you. Passing parameters by reference (using an &) allows the listeners to change the variables passed in. All listeners will receive these parameters, process them and optionally pass back information. The calling code can access the returned values via the array $results (each element corresponds to the result of one listener).

> The trigger system applicable for both **admin** and **catalog** sides.