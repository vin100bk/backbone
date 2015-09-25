# Backbone modules (multi inheritance)
A multi inheritance capability for Backbone. This feature is close to other ones you can find in some other technologies:
- PHP: http://php.net/manual/en/language.oop5.traits.php
- Ruby (only for instance methods): http://ruby-doc.org/core-2.2.0/Module.html

## Example
### Define your module
```js
/**
 * Module cache
 * @type {{cache: Function, isCached: Function}}
 */
var cache = {
    /**
     * Cache the entity
     * @param cacheKey
     */
    cache: function (cacheKey) {
        // Implementation of your cache system
    },

    /**
     * Is the entity cached?
     * @param cacheKey
     */
    isCached: function(cacheKey) {
        // ...
    }
};
```

### Define your component
```js
var model = Backbone.Model.extend({
    initialize: function() {
        // ...
    },

    // Whatever you want ...
}, {}, [cache]); // You specify the modules dependency
```

### Instantiate your component and use module properties
```js
var model = new Model({

});
// ...

// After manipulate your model, you want to cache it
if(!model->isCached()) {
    model->cache();
}
```

In my example I use a model but you can use this feature for all Backbone components: the model, collection, router, view and history.