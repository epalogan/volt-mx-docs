---
layout: "documentation"
category: "iris_wearables_dev_guide"
---
                             


VoltMXDataCache
=============

VoltMXDataCache is a class that stores key-value pairs, similar to a dictionary. The cache stores data temporarily in a watch that is obtained from an iPhone using WatchKit requests. Reusing the cached data improves performance. The cache reduces the processing requests to iPhone and helps to improve responsiveness for the users. However, if the data is not critical to the application and memory is running low, cached data can be discarded. If discarded, the data must be recomputed.

cacheTimeoutInterval
--------------------

This property helps cache the data in an Apple Watch for the duration specified. If you do not specify the cacheTimeoutInterval, the data is cached for one day. The duration must be specified in seconds.

Example

{% highlight voltMx %}VoltMXDataCache * cache = [
    [VoltMXDataCache alloc] initWithName: @“localCache”
];
cache.cacheTimeoutInterval = 20; // so data is cached for 20 seconds
{% endhighlight %}

Following are the APIs available for the VoltMXDataCache class:

*   [initWithName:(NSString\*)cacheName](#initwithname-nsstring-cachename)
*   [(instancetype)sharedInstance](#instancetype-sharedinstance)
*   [(void)setObject:(id)value forKey:(id)key](#void-setobject-id-value-forkey-id-key)
*   [(id)getObjectForKey:(id)key](#id-getobjectforkey-id-key)
*   [(void)setCacheWithDictionary:(NSDictionary\*)dict](#void-setcachewithdictionary-nsdictionary-dict)
*   [(NSDictionary)getDictionaryFromCache](#nsdictionary-getdictionaryfromcache)
*   [(void)setString:(NSString\*)string forKey:(NSString\*)key](#void-setstring-nsstring-string-forkey-nsstring-key)
*   [(NSString\*)getStringforKey:(NSString\*)key](#nsstring-getstringforkey-nsstring-key)
*   [(void)setImage:(UIImage\*)image forKey:(NSString\*)key](#void-setimage-uiimage-image-forkey-nsstring-key)
*   [(UIImage\*)getImageForKey:(NSString\*)key](#uiimage-getimageforkey-nsstring-key)
*   [(NSArray\*)getAllkeys](#nsarray-getallkeys)
*   [(void)clearCache](#void-clearcache)
*   [(void)removeCacheForKey:(NSString\*)key](#void-removecacheforkey-nsstring-key)

initWithName:(NSString\*)cacheName
----------------------------------

This API helps you initialize the VoltMXDataCache object with the specified cache name.

### Signature

**initWithName:(NSString\*)cacheName**

### Input Parameters

cacheName \[String\] - Mandatory

Specifies the name of the cache that must be initialized.

### Return Values

This API returns the initialized VoltMXDataCache object.

### Platform Availability

Available on iOS platform.

### Example

{% highlight voltMx %}VoltMXDataCache * cache = [
    [VoltMXDataCache alloc] initWithName: @"mycache"
];
{% endhighlight %}

(instancetype)sharedInstance
----------------------------

This API helps you create a shared instance of the VoltMXDataCache object with a default name.

### Signature

**(instancetype)sharedInstance**

### Input Parameters

None

### Return Values

This API returns the VoltMXDataCache shared instance.

### Platform Availability

Available on iOS platform.

### Example

{% highlight voltMx %}VoltMXDataCache * cache = [VoltMXDataCache sharedInstance];
{% endhighlight %}

(void)setObject:(id)value forKey:(id)key
----------------------------------------

This API helps you set cache with a given key value pair.

### Signature

**(void)setObject:(id)value forKey:(id)key**

### Input Parameters

value \[object\] - Mandatory

Specifies the value to be cached.

key \[String\] - Mandatory

Specifies the key for the value object.

### Return Values

None

### Platform Availability

Available on iOS platform.

### Example

{% highlight voltMx %}VoltMXDataCache * cache = [
    [VoltMXDataCache alloc] initWithName: @"mycache"
];
NSArray * arr = @ [@"one", @"two"];
[cache setObject: arr forKey: @"key"]
{% endhighlight %}

(id)getObjectForKey:(id)key
---------------------------

This API helps you get the value of the NSObject for the given key object.

### Signature

**(id)getObjectForKey:(id)key**

### Input Parameters

key \[String\] - Mandatory

Specifies the key object for which the associated value is retrieved.

### Return Values

None

### Platform Availability

Available on iOS platform.

### Example

{% highlight voltMx %}NSArray * arr = [cache getObjectForKey: @"key"];
{% endhighlight %}

(void)setCacheWithDictionary:(NSDictionary\*)dict
-------------------------------------------------

This API helps you set cache with a given dictionary.

### Signature

**(void)setCacheWithDictionary:(NSDictionary\*)dict**

### Input Parameters

dict \[Object\] - Mandatory

Specifies the dictionary object with which the cache is set.

### Return Values

None

### Platform Availability

Available on iOS platform.

### Example

{% highlight voltMx %}NSDictionary * dict = @ {@
    "key1": @ "val1",
    @"key2": "val2"
};
[cache setCacheWithDictionary: dict];
{% endhighlight %}

(NSDictionary)getDictionaryFromCache
------------------------------------

This API helps you get the dictionary from cache.

### Signature

**(NSDictionary)getDictionaryFromCache**

### Input Parameters

None

### Return Values

This API returns the dictionary.

### Platform Availability

Available on iOS platform.

### Example

{% highlight voltMx %}NSDictionary * dict = [cache getDictionaryFromCache];
{% endhighlight %}

(void)setString:(NSString\*)string forKey:(NSString\*)key
---------------------------------------------------------

This API helps you set the cache with given key-value string objects.

### Signature

**(void)setString:(NSString\*)string forKey:(NSString\*)key**

### Input Parameters

String \[String\] - Mandatory

Specifies the string object set as a value to the given key.

key \[String\] - Mandatory

Specifies the key for the object.

### Return Values

This API returns the dictionary.

### Platform Availability

Available on iOS platform.

### Example

{% highlight voltMx %}[cache setString: @"stringValue"
    forKey: @"stringkey"
];
{% endhighlight %}

(NSString\*)getStringforKey:(NSString\*)key
-------------------------------------------

This API helps you get the string object associated with the given key.

### Signature

**(NSString\*)getStringforKey:(NSString\*)key**

### Input Parameters

key \[String\] - Mandatory

Specifies the key for the object to which the associated value is retrieved.

### Return Values

This API returns NSString object.

### Platform Availability

Available on iOS platform.

### Example

{% highlight voltMx %}[cache setString: @"stringValue"
    forKey: @"stringkey"
];
{% endhighlight %}

(void)setImage:(UIImage\*)image forKey:(NSString\*)key
------------------------------------------------------

This API helps you set the image object to a given key in cache.

### Signature

**(void)setImage:(UIImage\*)image forKey:(NSString\*)key**

### Input Parameters

image \[UIImage\] - Mandatory

Specifies the image object set as a value to the given key.

key \[String\] - Mandatory

Specifies the key for the object.

### Return Values

This API returns NSString object.

### Platform Availability

Available on iOS platform.

### Example

{% highlight voltMx %}UIImage * image = [UIImage imageNamed: @"image.png"];
[cache setImage: image forKey: @"myImage"];
{% endhighlight %}

(UIImage\*)getImageForKey:(NSString\*)key
-----------------------------------------

This API helps you get the image for a given key.

### Signature

**(UIImage\*)getImageForKey:(NSString\*)key**

### Input Parameters

key \[String\] - Mandatory

Specifies the key object to which the associated value is retrieved.

### Return Values

This API returns UIImage.

### Platform Availability

Available on iOS platform.

### Example

{% highlight voltMx %}UIImage * img = [cache getImageForKey: @"myImage"];
{% endhighlight %}

(NSArray\*)getAllkeys
---------------------

This API helps you get all keys in the cache.

### Signature

**(NSArray\*)getAllkeys**

### Input Parameters

None

### Return Values

This API returns NSArray object.

### Platform Availability

Available on iOS platform.

### Example

{% highlight voltMx %}NSArray *arr = [cache getAllKeys]; 
{% endhighlight %}

(void)clearCache
----------------

This API helps you clear the cache.

### Signature

**(void)clearCache**

### Input Parameters

None

### Return Values

None

### Platform Availability

Available on iOS platform.

### Example

{% highlight voltMx %}[cache clearCache]; 
{% endhighlight %}

(void)removeCacheForKey:(NSString\*)key
---------------------------------------

This API helps you remove cache for the given key.

### Signature

**(void)removeCacheForKey:(NSString\*)key**

### Input Parameters

key \[String\] - Mandatory

Specifies the key object that has to be removed from the cache.

### Return Values

None

### Platform Availability

Available on iOS platform.

### Example

{% highlight voltMx %}[cache removeCacheForKey:@"myImage"]; 
{% endhighlight %}
