# Open-Update

To register your mod with the OpenUpdater simply add the following block of code to your mods PreInit
```
		if ((event.getSourceFile().getName().endsWith(".jar")) && event.getSide().isClient()) {
			try {
				Class.forName("pcl.mud.ModUpdateDetector").getDeclaredMethod("registerMod", ModContainer.class, URL.class, URL.class).invoke(null, FMLCommonHandler.instance().findContainerFor(this),
								new URL("http://somewebsite.com/latestbuild.xml"),
								new URL("http://somewebsite.com/changelog.txt"));
			} catch (Throwable e) {
				//Let the user know that registration failed.
			}
		}
```
If the user doesn't have OpenUpdater installed their game will not crash.

the format of latestbuild.xml is simply
```
<?xml version="1.0" encoding="UTF-8"?>
<mod modid="yourmodid">
	<mcVersion version="1.7.10">
		<release type="release" version="modversion"
		url="http://somewebsite.com"
		download="http://somewebsite.com/path/to/your/mod.jar"/>
	</mcVersion>
</mod>
```

Lastly the changelog.txt is just a plaintext listing of changes if you want it displayed to the client.
