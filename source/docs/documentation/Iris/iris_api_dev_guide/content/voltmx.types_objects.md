---
layout: "documentation"
category: "iris_api_dev_guide"
---
                            


Secure Text Exchange between Native Android Code and JavaScript
---------------------------------------------------------------

From Volt MX Iris V9 SP1, the following RawBytes class methods have been introduced on the Android platform. Using the RawBytes interface, you can pass secure or sensitive text between Native Android Code and JavaScript code. You can create a RawBytes Object from the content of the secure text, which can then be passed to JavaScript. Similarly, a JavaScript RawBytes Object can be used to retrieve secure text from Native Android Code.

Package

com.konylabs.api.io

Class

RawBytes

Constructor

_RawBytes(Object secureText)_

The constructor takes an Object that is either a Character array (char\[\]) or a Byte array(byte\[\]) as an input parameter.

Example

{% highlight voltMx %}char[] sensitiveText= {'p','a','s','s','w','o','r','d'};   
RawBytes rawBytes = new RawBytes(sensitiveText);
{% endhighlight %}

Constants

The following Native Android constant identifiers are used to retrieve the content type of the RawBytes Object:

>   
> | Constant | Description |
> | --- | --- |
> | RawBytes.CONTENT\_TYPE\_BYTE\_ARRAY | Constant Identifier that specifies the content type of the RawBytes Object as a Byte array. |
> | RawBytes.CONTENT\_TYPE\_CHAR\_ARRAY | Constant Identifier that specifies the content type of the RawBytes Object as a Character array. |

**Methods**

*   **createJSObject**
    
    The createJSObject method returns a JavaScript-understandable RawBytes object that is created from an Android Native RawBytes Object.
    
    {% highlight voltMx %}public java.lang.Object createJSObject();
    {% endhighlight %}
    
    Code Snippet:
    
    {% highlight voltMx %}char[] sensitiveText = {  
    'p' 'a', 's', 's', 'w', 'o', 'r', 'd'  
    };  
    RawBytes rawBytes = new RawBytes(sensitiveText);  
    /* creates javascript rawBytes object*/  
    Object rawBytesJSObject = rawBytes.createJSObject();
    {% endhighlight %}
*   **getByteArray**
    
    The getByteArray method returns the content of the RawBytes Object as a Byte array.
    
    This method may return a Null value if the Content Type of the RawBytes Object is not a Byte array or a Character array.
    
    {% highlight voltMx %}public byte[] getByteArray();
    {% endhighlight %}
*   **getCharArray**
    
    The getCharArray method returns the content of the RawBytes Object as a Character array.
    
    This method may return a Null value if the Content Type of the RawBytes Object is not a Character array or a Byte array.
    
    {% highlight voltMx %}public char[] getCharArray();
    {% endhighlight %}
*   **getContentType**
    
    The getContentType method returns the [Content Type](#Constants) of the RawBytes.
    
    {% highlight voltMx %}public int getContentType();
    {% endhighlight %}
*   **clear**
    
    The clear method is used to clear the RawBytes values from the memory after the usage of object is done, or the object is no longer needed.
    
    {% highlight voltMx %}public void clear();
    {% endhighlight %}

Example

{% highlight voltMx %}// This JavaScript code demonstrates the following:  
// 1) Retrieves a character array password from the Native layer in the form of RawBytes.  
// 2) Generates a PBKDF2 encryption key using the password from the Native layer.  
// 3) Uses the PBKDF2 key to encrypt user input text content from a sensitive text box.  
// 4) Passes the input sensitive text from Javascript to the Native layer for further processing.  
function encryptSensitiveContentWithPasswordFromFFI() {  
    // 1. Retrieves a character array password from the Native layer in the form of RawBytes.  
    // NativeClass.getRawBytesObject is the javascript-ffi interface method (Refer FFI snippet below this function)  
  
    var voltmxrawbytes = NativeClass.getRawBytesObject();  
    if (voltmx.types.RawBytes.CONTENT_TYPE_CHAR_ARRAY != voltmxrawbytes.getContentType()) {  
        voltmx.print("Unsupported content type");  
        return;  
    }  
  
    // 2. Generates a PBKDF2 encryption key using the password from the Native layer.  
    var pbkdf2Key = voltmx.crypto.createPBKDF2Key("SHA1", voltmxrawbytes, "12345", 1000);  
    // 3. Uses the PBKDF2 key to encrypt user input text content from a sensitive text box.  
    var encryptionText = < FormID > .encryptionText.text; // textArea where Sensitive Text is enabled in the properties  
    var propTable = {  
        padding: "pkcs5",  
        mode: "cbc",  
        initializationvector: "1234567890123456"  
    };  
    var encryptedText = voltmx.crypto.encrypt("aes", pbkdf2Key, encryptionText, propTable);  
    // 4. Passes the input sensitive text from Javascript to the Native layer for further processing.  
    NativeClass.processSensitiveText(encryptionText);  
}  
// FFI code  
import com.konylabs.api.io.RawBytes  
public class NativeClass {  
    public static Object getRawBytesObject() {  
        char[] sensitiveText = {  
            'p', 'a', 's', 's', 'w', 'o', 'r', 'd'  
        };  
        RawBytes rawBytes = new RawBytes(sensitiveText);  
        /*creates a javascript rawBytes object*/  
        Object rawBytesJSObject = rawBytes.createJSObject();  
        return rawBytesJSObject;  
    }  
    public static void processSensitiveText(Object secret) {  
        char[] userSecret = ((RawBytes)secret).getCharArray();  
        //Process this userSecret and zero fill char Array  
    }  
}
{% endhighlight %}

Platform Availability

*   Android

![](resources/prettify/onload.png)
