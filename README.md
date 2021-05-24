# Install dependencies

Install flatpak:
```
apt install flatpak
```

Add flathub repo to flatpak:
```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

Install build dependencies:
```  
flatpak install flathub org.freedesktop.Platform//20.08 org.freedesktop.Sdk//20.08 org.freedesktop.Sdk.Extension.golang//20.08 org.flatpak.Builder
```


# Build the flatpak

Lets build it using flatpak-builder:
```
flatpak run org.flatpak.Builder --repo=repo --force-clean build-dir org.torproject.SnowflakeProxy.yml
```

This will build the application in `build-dir` and create a `repo` folder.

Now we can bundle it into a file for distribution:
```
flatpak build-bundle repo snowflake-proxy.flatpak org.torproject.SnowflakeProxy
```

This produces a snowflake-proxy.flatpak that we can install directly in any machine:
```
flatpack install snowflake-proxy.flatpak
```
