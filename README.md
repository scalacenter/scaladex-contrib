# Scala Index Community Data

This repository exists to fill the gaps between the Scala Index and publicly available projects.

## Claim your project

When you publish your project with a `source code management` tag ([`scm`](http://maven.apache.org/scm/git.html)) 
which points to a github repository, we can fetch additional information. If you forgot to add the `scm` tag, 
edit [claims.json](claims.json) and create a pull request to claim a project. If your project is not on the list, 
you will need to publish it on Maven Central or Bintray first. See [how-to/publish](how-to/publish.md) to learn 
more about publishing.

## Index artifacts which are published in java-style

When you publish your artifacts in the standard way with a Scala version number attached to the artifact
name, you'll be fine, and your project will be indexed automatically (assuming it's linked with a GitHub repo, see above). In case
you don't follow the Scala standard of publishing artifacts on maven, you can edit [non-standard.json](non-standard.json) and provide a list of all artifacts, their version and the compatible scala version.

For example,
```
{":groupId :artifact :version" => [:scalaVersions]}
// like
{"io.gatling gatling-app *": ["2.11"]} // all versions
{"io.gatling gatling-app 2.*": ["2.11"]} // only 2.* versions
{"io.gatling gatling-app 1.*": ["2.10"]} // only 1.* versions
```

If you never plan to publish your library in the standard Scala way (artifacts suffixed with `_2.x`), you can use a wildcard in the [non-standard.json](non-standard.json) file. If there is at any point no backward compatibility, e.g., if the verison `2.*` is compatible to scala 2.10 and 2.11 but version `3.*` only to 2.11 and 2.12, you can't use a `*` as a wildcard and you will have to manually list all of your artifacts.

When you provide this list, your artifact will also show up as a scala artifact in the index upon the next re-index.

## Disambiguate Licenses

In sbt, the `licenses` setting is defined as: [`val licenses = SettingKey[Seq[(String, URL)]]`](
https://github.com/sbt/sbt/blob/1.0.x/main/src/main/scala/sbt/Keys.scala#L263). We observe that users 
will publish a semantically identical license under different name/URL. See https://github.com/sbt/sbt/issues/1937 
for more detail

We provide two ways to disambiguate license:

* [by name](licenses/byName.json)
* [by URL](licenses/byURL.json)
