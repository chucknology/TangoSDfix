<img src="/../doc-assets/tango_sdfix_icon.png" width="64" height="64" alt="Tango SD Fix app icon" /> TangoSDfix
=========

**One-click microSD card write enabler for the Project Tango tablet**

You may have encountered some issues working with microSD card storage, such as not being able to write to it ! These issues are a result of platform changes in API level 19.

This app enables unrestricted writing to the microSD card.

It doesn't require any permissions apart from `SUPERUSER` so you'll need to be rooted to use it.

Get the <a href="https://github.com/chucknology/TangoRoot">TangoRoot</a> app if you haven't done so already.

---

___Information:___

Tango has 128GB of **internal primary storage**, and a microSD card receptacle for **removable secondary storage**.

Since API level 19 (KitKat) **secondary storage is READ ONLY**, with a few caveats.

*Making use of secondary storage is not straightforward. The Android documentation can be somewhat confusing due to the naming of the API. In most cases, methods with "External" in their name actually address internal storage.*

A reliable approach is to <a href="https://source.android.com/devices/storage/config-example.html">read the absolute paths from your environment variables</a>:

```
String primaryStore   = System.getenv("EXTERNAL_STORAGE");  // Tango tablet currently = "/storage/emulated/legacy"
String secondaryStore = System.getenv("SECONDARY_STORAGE"); // Tango tablet currently = "/storage/sdcard1"
```

If you are targeting devices other than the Tango, you should also do this:

```
if (secondaryStore != null)
    secondaryStore = secondaryStore.split(":")[0]; // some devices (e.g. Samsung) return multiple paths, the first is the microSD card
```

---

This tool is provided as a convenience for developers and people who depend upon legacy software.

You should update production code to use KitKat APIs such as the <a href="https://developer.android.com/guide/topics/providers/document-provider.html">Storage Access Framework.</a>

If your application only needs to store internal data, consider using <a href="https://developer.android.com/reference/android/content/Context.html#getExternalFilesDir%28java.lang.String%29">getExternalFilesDir(String)</a> or <a href="https://developer.android.com/reference/android/content/Context.html#getExternalCacheDir%28%29">getExternalCacheDir()</a>, which require no permissions to read or write.

To learn more about these issues, you should read <a href="http://commonsware.com/blog/2014/04/09/storage-situation-removable-storage.html">Mark Murphy's excellent write-up.</a>

```
There was never any warranty.
Trademarks are owned by their owners!
```
![App screenshot 1](/../doc-assets/Tango SD Fix screenshot 1.png?raw=true "App screenshot 1")

![App screenshot 2](/../doc-assets/Tango SD Fix screenshot 2.png?raw=true "App screenshot 2")

___Removal:___

After you have used this app, you can uninstall it.

<a href="http://facebook.com/chuck.knowledge">Chuck Knowledge</a> loves you.
