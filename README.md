# Scriptable Singletons
Easy to use singleton implementation for ScriptableObjects in Unity.

## Usage


To make your ScriptableObject a singleton, place your asset instance in a _Resoures_ directory.

Then, make your ScrptableObject class inherit from `ScriptableSingleton` and add the `AssetPathAttribute` with the path to your asset relative to the Resources folder.

### Example

Let's say that you need to access a scriptableObject called _MyGameSettings_ as a singleton.

```c#
public class MyGameSettings : ScriptableObject
{
    // ...
}
```

Make sure only one asset for that object exists and place it in a valid Resources folder (e.g. `Assets/Resources/myGameSettingsAsset.asset`).


Then, make a few changes to the class definition, as follows:
```c#
[AssetPath("myGameSettingsAsset")]
public class MyGameSettings : ScriptableSingleton<MyGameSettings>
{
    // ...
}
```

Note: if your asset is located in a subfolder within the Resources folder, the path specified in the AssetPath attribute should match with it. For example: an asset in `Assets/Resources/Foo/bar.asset` should have an attribute `[AssetPath("Foo/bar")]`.

All set! You can access your asset instance with the `Instance` property.
```c#
MyGameSettings.Instance.DoSomething();
```

## Installation

This package is compatible with the Unity Package Manager (UPM). Please refer to the official Unity documentation to [install this package from a git repository](https://docs.unity3d.com/2020.1/Documentation/Manual/upm-ui-giturl.html).
