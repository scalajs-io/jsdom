Jsdom API for Scala.js
=======================
This is a Scala.js type-safe binding for [jsdom](https://www.npmjs.com/package/jsdom) 

A JavaScript implementation of the DOM and HTML standards.

#### Build Dependencies

* [ScalaJs.io v0.3.x](https://github.com/ldaniels528/scalajs.io)
* [SBT v0.13.13](http://www.scala-sbt.org/download.html)

#### Build/publish the SDK locally

```bash
$ sbt clean publish-local
```

#### Running the tests

Before running the tests the first time, you must ensure the npm packages are installed:

```bash
$ npm install
```

Then you can run the tests:

```bash
$ sbt test
```

#### Examples

```scala
val doc = JsDom.jsdom("""<p id="p1"><a class="the-link" href="https://github.com/tmpvar/jsdom">jsdom!</a></p>""")
val elem = doc.getElementsByClassName("the-link").headOption.orNull
assert(elem != null)

val text = elem.asInstanceOf[HTMLAnchorElement].text
assert(text == "jsdom!")
```

#### Artifacts and Resolvers

To add the Jsdom binding to your project, add the following to your build.sbt:  

```sbt
libraryDependencies += "io.scalajs.npm" %%% "jsdom" % "0.3.0.3"
```

Optionally, you may add the Sonatype Repository resolver:

```sbt   
resolvers += Resolver.sonatypeRepo("releases") 
```