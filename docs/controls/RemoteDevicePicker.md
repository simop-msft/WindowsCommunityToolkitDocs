---
title: RemoteDevicePicker Control
author: avknaidu
description: The RemoteDevicePicker control helps you to pick a device that you can use to Remote Launch Apps, Services.
keywords: windows 10, uwp, windows community toolkit, uwp community toolkit, uwp toolkit, RemoteDevicePicker, picker
dev_langs:
  - csharp
---

# RemoteDevicePicker Control

The [RemoteDevicePicker](https://docs.microsoft.com/dotnet/api/microsoft.toolkit.uwp.ui.controls.remotedevicepicker) gives you a list of Remote Systems. All the systems must be signed in with the same Microsoft Account (MSA)

> [!IMPORTANT]
> Make sure you enable the [RemoteSystem capability](https://docs.microsoft.com/en-us/windows/uwp/packaging/app-capability-declarations#general-use-capabilities) in your app's `package.appxmanifest` to access remote system information.

> [!div class="nextstepaction"]
> [Try it in the sample app](uwpct://Controls?sample=RemoteDevicePicker)

## Syntax

```c#
RemoteDevicePicker remoteDevicePicker = new RemoteDevicePicker()
{
    Title = "Pick Remote Device",
    SelectionMode = RemoteDevicesSelectionMode.Multiple
};
var result = await remoteDevicePicker.PickDeviceAsync();
await new MessageDialog($"You picked {result.Count.ToString()} Device(s)" + Environment.NewLine + string.Join(",", result.Select(x => x.DisplayName.ToString()).ToList())).ShowAsync();
```

You can also use default filter types for initializing. Like Below.

```c#
RemoteDevicePicker remoteDevicePicker = new RemoteDevicePicker(RemoteSystemDiscoveryType.Proximal, RemoteSystemAuthorizationKind.Anonymous, RemoteSystemStatusType.Any)
{
    Title = "Pick Remote Device",
	SelectionMode = RemoteDevicesSelectionMode.Multiple
};

var remoteSystems = await remoteDevicePicker.PickDeviceAsync();
await new MessageDialog($"You picked {remoteSystems.Count().ToString()} Device(s)" + Environment.NewLine + string.Join(",", remoteSystems.Select(x => x.DisplayName.ToString()).ToList())).ShowAsync();
```

## Properties

| Property | Type | Description |
| -- | -- | -- |
| SelectionMode | RemoteDevicesSelectionMode | Gets or sets the DeviceList Selection Mode. Defaults to RemoteDevicesSelectionMode.Single |
| ShowAdvancedFilters | Boolean | Gets or sets a value indicating whether Advanced Filters are visible or not. Defaults to false |

## Sample Project

[RemoteDevicePicker Sample Page Source](https://github.com/windows-toolkit/WindowsCommunityToolkit/tree/master/Microsoft.Toolkit.Uwp.SampleApp/SamplePages/RemoteDevicePicker). You can [see this in action](uwpct://Controls?sample=RemoteDevicePicker) in the [Windows Community Toolkit Sample App](http://aka.ms/uwptoolkitapp).

## Default Template

[RemoteDevicePicker XAML File](https://github.com/windows-toolkit/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Uwp.UI.Controls/RemoteDevicePicker/RemoteDevicePicker.xaml) is the XAML template used in the toolkit for the default styling.

## Requirements

| Device family | Universal, 10.0.16299.0 or higher |
| --- | --- |
| Namespace | Microsoft.Toolkit.Uwp.UI.Controls |
| NuGet package | [Microsoft.Toolkit.Uwp.UI.Controls](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.UI.Controls/) |

## API

* [RemoteDevicePicker source code](https://github.com/windows-toolkit/WindowsCommunityToolkit/tree/master/Microsoft.Toolkit.Uwp.UI.Controls/RemoteDevicePicker)

## Related Topics

* [Project Rome](https://developer.microsoft.com/en-us/windows/project-rome)
* [Remote Systems Sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/RemoteSystems)
* [Connected apps and devices (Project Rome)](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/connected-apps-and-devices)
* [Communicate with a remote app service](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* [AppServices Sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AppServices)
