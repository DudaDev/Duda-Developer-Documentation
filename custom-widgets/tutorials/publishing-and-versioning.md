# Publishing & Versioning

Duda's Widget Builder comes with a fully-featured release and versioning system that helps you keep track of ongoing changes and enables you to rollback back to a previous version, or compare two versions together. Duda does this automatically each time you publish and doesn't require you to know Git or version control paradigms to take advantage.

### Publishing

To make a widget available for use in the editor, you'll need to publish it. Publishing a widget is as easy as clicking **publish** or **republish** in the widget builder.

<figure><img src="https://files.readme.io/86ea1f4-Screen_Shot_2021-12-15_at_10.52.26_AM.png" alt=""><figcaption></figcaption></figure>

Making edits and clicking **republish** triggers a modal that asks you to enter a version note and whether or not you want to push the update to existing widgets.

<figure><img src="https://files.readme.io/7e28601-Screen_Shot_2021-12-15_at_10.21.25_AM.png" alt="2794"><figcaption><p>It's recommended that you enter in some details about the changes made for future reference.</p></figcaption></figure>

After you successfully publish, you can set access and widget details from **Settings** ➡ **General**.

<figure><img src="https://files.readme.io/40114dc-Screen_Shot_2021-12-15_at_10.45.50_AM.png" alt=""><figcaption></figcaption></figure>

**Widget Availability**

* Private: available to you
* Team: available to your teammates
* Public: available to your teammates and clients

### Versioning

At a very high-level, version management is a means to effectively track and control updates to an entity or related entities. This is relevant for widget builder, especially for larger and more complex widgets and workflows.

As explained in the Publishing section, Duda will save a version of the widget after each republish. Once you publish a widget, you can access its versions under **Settings** ➡ **Versions** to preview, rollback, or compare previous versions.

<figure><img src="https://files.readme.io/960dce5-Screen_Shot_2021-12-15_at_10.23.26_AM.png" alt="1958"><figcaption><p>Here you can see my initial version (1) and the current version (2). Note, version (2) displays the version note that was added.</p></figcaption></figure>

You can perform three main actions within the versions tab of a widget: preview, restore and edit, and compare versions.

#### Preview

Enables you to visually preview a specific version of the widget and interact with its content and design panels.

#### Restore & Edit

Enables you to rollback to a previous version and jump straight into the editor to make any modifications before publishing.

#### Compare Versions

Provides a convenient and straightforward view to compare the source code of two versions. If you're familiar with Git, this will look and feel like a standard `git diff`.

<figure><img src="https://files.readme.io/95574ec-Screen_Shot_2021-12-15_at_10.21.50_AM.png" alt=""><figcaption></figcaption></figure>

### Conclusion

Duda's publishing and versioning system abstracts away the complexity of managing large widget projects with many developers and moving pieces. In addition, it provides you with a useful tool to debug breaking changes between versions.
