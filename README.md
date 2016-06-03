# Scala Index Community Data

This repository exists to fill the gaps between the Scala Index and publicly available projects.

## Claim your project

When you publish your project with a `source code management` tag ([`scm`](http://maven.apache.org/scm/git.html)) which points to a github repository, we can fetch additional informations. If you forgot to add the `scm` tag, edit [claims.json](claims.json) and create a pull request to claim a project. If your project is not on the list, you will need to publish it on Maven Central or Bintray first. See [how-to/publish](how-to/publish.md) to learn more about publishing.

## Disambiguate Licenses

In sbt, the `licenses` setting is defined as: [`val licenses = SettingKey[Seq[(String, URL)]]`](
https://github.com/sbt/sbt/blob/1.0.x/main/src/main/scala/sbt/Keys.scala#L263). We observe that users will publish a semantically identical license under different name/URL. See https://github.com/sbt/sbt/issues/1937 for more detail

We provide two ways to disambiguate license:

* [by name](licenses/byName.json)
* [by URL](licenses/byURL.json)