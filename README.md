## Snap Plugin Go Library: Collector Plugin Example
Here you will find an example plugin that cover the basics for writing a collector plugin.
This repo includes skeleton files for a collector plugin and all the build and test scripts needed to create a standalone plugin binary.

##Setup & Install
To get your plugin to to build properly you will need to have [glide](https://glide.sh/) installed on your $GOPATH.

1. First get the plugin library repo:
`go get github.com/____` will add the repo to your $GOPATH
or clone this repository.

note: if you want to contribute to this repository you should fork this repo and open a PR.

2. Once you have the repo downloaded go to the snap-plugin-collector-rand folder and use `glide up` to update to the newest versions of the package:

```
$ cd snap-plugin-collector-rand
$ glide up
[WARN]	The name listed in the config file () does not match the current location (github.com/intelsdi-x/snap-plugin-collector-example)
[INFO]	Downloading dependencies. Please wait...
[INFO]	No references set.
[INFO]	Resolving imports
[INFO]	--> Fetching updates for github.com/intelsdi-x/snap-plugin-lib-go.
[INFO]	--> Fetching updates for golang.org/x/net.
[INFO]	--> Setting version for golang.org/x/net to 154d9f9ea81208afed560f4cf27b4860c8ed1904.
[INFO]	--> Fetching updates for google.golang.org/grpc.
[INFO]	--> Setting version for google.golang.org/grpc to 0032a855ba5c8a3c8e0d71c2deef354b70af1584.
[INFO]	--> Fetching updates for github.com/golang/protobuf.
[INFO]	--> Setting version for github.com/golang/protobuf to 888eb0692c857ec880338addf316bd662d5e630e.
[INFO]	--> Fetching updates for github.com/jtolds/gls.
[INFO]	--> Setting version for github.com/jtolds/gls to 8ddce2a84170772b95dd5d576c48d517b22cac63.
[INFO]	--> Fetching updates for github.com/smartystreets/assertions.
[INFO]	--> Setting version for github.com/smartystreets/assertions to 443d812296a84445c202c085f19e18fc238f8250.
[INFO]	--> Fetching updates for github.com/smartystreets/goconvey.
[INFO]	--> Setting version for github.com/smartystreets/goconvey to 995f5b2e021c69b8b028ba6d0b05c1dd500783db.
[INFO]	--> Fetching updates for github.com/gopherjs/gopherjs.
[INFO]	--> Setting version for github.com/gopherjs/gopherjs to 4b53e1bddba0e2f734514aeb6c02db652f4c6fe8.
[INFO]	Downloading dependencies. Please wait...
[INFO]	Setting references for remaining imports
[INFO]	Exporting resolved dependencies...
[INFO]	--> Exporting github.com/intelsdi-x/snap-plugin-lib-go
[INFO]	--> Exporting github.com/jtolds/gls
[INFO]	--> Exporting github.com/smartystreets/goconvey
[INFO]	--> Exporting github.com/golang/protobuf
[INFO]	--> Exporting github.com/gopherjs/gopherjs
[INFO]	--> Exporting github.com/smartystreets/assertions
[INFO]	--> Exporting google.golang.org/grpc
[INFO]	--> Exporting golang.org/x/net
[INFO]	Replacing existing vendor dependencies
[INFO]	Project relies on 4 dependencies.
```

3. Then run `make`. This will build your plugin binary and place the binary into the `build/linux/x86_64/` directory.
```
$ make
/Library/Developer/CommandLineTools/usr/bin/make deps
bash -c "./scripts/deps.sh"
2016-09-27 23:10:28 UTC [     info] golang dependency tool: glide
2016-09-27 23:10:28 UTC [     info] ensuring glide is available
2016-09-27 23:10:28 UTC [     info] restoring dependency with glide
[WARN]	The name listed in the config file () does not match the current location (github.com/intelsdi-x/snap-plugin-collector-rand)
[INFO]	Downloading dependencies. Please wait...
[INFO]	--> Found desired version locally github.com/golang/protobuf 888eb0692c857ec880338addf316bd662d5e630e!
[INFO]	--> Found desired version locally github.com/intelsdi-x/snap-plugin-lib-go 55956e53732655f4875708b15c25904090af41ec!
[INFO]	--> Found desired version locally golang.org/x/net 154d9f9ea81208afed560f4cf27b4860c8ed1904!
[INFO]	--> Found desired version locally google.golang.org/grpc 0032a855ba5c8a3c8e0d71c2deef354b70af1584!
[INFO]	--> Found desired version locally github.com/gopherjs/gopherjs 4b53e1bddba0e2f734514aeb6c02db652f4c6fe8!
[INFO]	--> Found desired version locally github.com/jtolds/gls 8ddce2a84170772b95dd5d576c48d517b22cac63!
[INFO]	--> Found desired version locally github.com/smartystreets/assertions 443d812296a84445c202c085f19e18fc238f8250!
[INFO]	--> Found desired version locally github.com/smartystreets/goconvey 995f5b2e021c69b8b028ba6d0b05c1dd500783db!
[INFO]	Setting references.
[INFO]	--> Setting version for github.com/golang/protobuf to 888eb0692c857ec880338addf316bd662d5e630e.
[INFO]	--> Setting version for github.com/gopherjs/gopherjs to 4b53e1bddba0e2f734514aeb6c02db652f4c6fe8.
[INFO]	--> Setting version for github.com/intelsdi-x/snap-plugin-lib-go to 55956e53732655f4875708b15c25904090af41ec.
[INFO]	--> Setting version for github.com/jtolds/gls to 8ddce2a84170772b95dd5d576c48d517b22cac63.
[INFO]	--> Setting version for github.com/smartystreets/assertions to 443d812296a84445c202c085f19e18fc238f8250.
[INFO]	--> Setting version for golang.org/x/net to 154d9f9ea81208afed560f4cf27b4860c8ed1904.
[INFO]	--> Setting version for github.com/smartystreets/goconvey to 995f5b2e021c69b8b028ba6d0b05c1dd500783db.
[INFO]	--> Setting version for google.golang.org/grpc to 0032a855ba5c8a3c8e0d71c2deef354b70af1584.
[INFO]	Exporting resolved dependencies...
[INFO]	--> Exporting github.com/golang/protobuf
[INFO]	--> Exporting github.com/smartystreets/assertions
[INFO]	--> Exporting github.com/intelsdi-x/snap-plugin-lib-go
[INFO]	--> Exporting github.com/jtolds/gls
[INFO]	--> Exporting github.com/gopherjs/gopherjs
[INFO]	--> Exporting golang.org/x/net
[INFO]	--> Exporting github.com/smartystreets/goconvey
[INFO]	--> Exporting google.golang.org/grpc
[INFO]	Replacing existing vendor dependencies
/Library/Developer/CommandLineTools/usr/bin/make all
bash -c "./scripts/build.sh /Users/sjhan/Documents/27-sept/src/github.com/intelsdi-x/snap-plugin-collector-rand"
2016-09-27 23:10:40 UTC [     info] project path: /Users/sjhan/Documents/27-sept/src/github.com/intelsdi-x/snap-plugin-collector-rand
2016-09-27 23:10:40 UTC [     info] plugin name: snap-plugin-collector-rand
2016-09-27 23:10:40 UTC [     info] building plugin: snap-plugin-collector-rand
```

## Plugin Naming, Files, and Directory
For your collector plugin, create a new repository and name your plugin project using the following format:

>snap-plugin-[plugin-type]-[plugin-name]

For example: 
>snap-plugin-collector-rand


Example files and directory structure:  
```
snap-plugin-[plugin-type]-[plugin-name]
 |--[plugin-name]
  |--[plugin-name].go  
  |--[plugin-name]_test.go  
 |--main.go
```

For example:
```
snap-plugin-collector-rand
 |--rand
  |--rand.go  
  |--rand_test.go  
 |--main.go
```

* The main file (for example `main.go`) allows each plugin to be a stand-alone binary executable. The main file will include: pluginName and pluginVersion.
* The [plugin-name] folder (for example `rand`) will include all files to implement the appropriate interface methods
* Your [plugin-name] folder  will also include your test files.



## Interface Methods

In order to write a plugin for Snap, it is necessary to define a few methods to satisfy the appropriate interfaces. These interfaces must be defined for a collector plugin:


```go
// Plugin is an interface shared by all plugins and must implemented by each plugin to communicate with Snap.
type Plugin interface {
	GetConfigPolicy() (ConfigPolicy, error)
}

// Collector is a plugin which is the source of new data in the Snap pipeline.
type Collector interface {
	Plugin

	GetMetricTypes(Config) ([]Metric, error)
	CollectMetrics([]Metric) ([]Metric, error)
}
```
The interface is slightly different depending on what type (collector, processor, or publisher) of plugin is being written. Please see other plugin types for more details.



## Starting a plugin

After implementing a type that satisfies one of {collector, processor, publisher} interfaces, all that is left to do is a call the appropriate plugin.StartX() with your plugin specific options. That could be as simple as:

```go
	plugin.StartCollector(rand.RandCollector{}, pluginName, pluginVersion)
```

### Meta options

The available options are defined in [plugin/meta.go](https://github.com/intelsdi-x/snap-plugin-lib-go/tree/master/v/1/plugin/meta.go). You can use some or none of the options. The options with definitions/explanations are below:

```go
// ConcurrencyCount is the max number of concurrent calls the plugin
// should take.  For example:
// If there are 5 tasks using the plugin and its concurrency count is 2,
// snapd will keep 3 plugin instances running.
// ConcurrencyCount overwrites the default (5) for a Meta's ConcurrencyCount.
func ConcurrencyCount(cc int) MetaOpt {
}

// Exclusive == true results in a single instance of the plugin running
// regardless of the number of tasks using the plugin.
// Exclusive overwrites the default (false) for a Meta's Exclusive key.
func Exclusive(e bool) MetaOpt {
}

// Unsecure results in unencrypted communication with this plugin.
// Unsecure overwrites the default (false) for a Meta's Unsecure key.
func Unsecure(e bool) MetaOpt {
}

// RoutingStrategy will override the routing strategy this plugin requires.
// The default routing strategy is Least Recently Used.
// RoutingStrategy overwrites the default (LRU) for a Meta's RoutingStrategy.
func RoutingStrategy(r router) MetaOpt {
}

// CacheTTL will override the default cache TTL for the this plugin. snapd
// caches metrics on the daemon side for a default of 500ms.
// CacheTTL overwrites the default (500ms) for a Meta's CacheTTL.
func CacheTTL(t time.Duration) MetaOpt {
}
```

An example of what using all of them would look like:

```go
	plugin.StartCollector(mypackage.Mytype{},
				pluginName,
				pluginVersion,
				plugin.ConcurrencyCount(a),
				plugin.Exclusive(b),
				plugin.Unsecure(c),
				plugin.RoutingStrategy(d),
				plugin.CacheTTL(e))
```

## Testing
For testing reference the Snap Testing Guidelines(https://github.com/intelsdi-x/snap/blob/master/CONTRIBUTING.md#testing-guidelines). To test your plugin with Snap you will need to have [Snap](https://github.com/intelsdi-x/snap) installed, check out these docs for [Snap setup details](https://github.com/intelsdi-x/snap/blob/master/docs/BUILD_AND_TEST.md#getting-started).

You should specify the test size (either small, medium, or large) with the specified build tag `// +build test-size`. The default testing will run all size tests if the build tag is not specified.


For example if you want to run only small tests:
```
// +build small
// you must include at least one line between the build tag and the package name.
package rand
```

For example if you want to run small and medium tests:
```
// +build small medium

package rand
```

## Ready to Share

When you've finished your plugin make sure to announce on [slack](https://intelsdi-x.herokuapp.com/) and get your plugin added to the [Plugin Catalog](https://github.com/intelsdi-x/snap/blob/master/docs/PLUGIN_CATALOG.md)
.