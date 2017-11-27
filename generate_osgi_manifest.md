# Generating OSGi Manifests with Bnd (Mac OSX)

```brew install bnd``` to install bnd tools for commandline. We won't be using this for the generation of the manifest, but it's got some useful commands.

We'll be using this: https://github.com/bndtools/bnd/tree/master/biz.aQute.bnd.gradle. Below is a basic way to set this up.


Add the following to your build.gradle. (This is just one way of doing this, here's an example https://gist.github.com/tux2323/15d4dc67b07bb93ae3f0)


```
buildscript {
  repositories {
    mavenCentral()
  }
  dependencies {
    classpath 'biz.aQute.bnd:biz.aQute.bnd.gradle:3.5.0'
  }
}

apply plugin : 'biz.aQute.bnd.builder'

# This is optional. The below exports all packages and imports all external dependencies it finds in your import statements.
jar {
    manifest {
        attributes('Export-Package': '*')
        attributes('Import-Package': '*')
    }
}
```



