---
-api-id: T:Windows.UI.Xaml.Automation.Peers.CaptureElementAutomationPeer
-api-type: winrt class
---

<!-- Class syntax.
public class CaptureElementAutomationPeer : Windows.UI.Xaml.Automation.Peers.FrameworkElementAutomationPeer, Windows.UI.Xaml.Automation.Peers.ICaptureElementAutomationPeer
-->

# Windows.UI.Xaml.Automation.Peers.CaptureElementAutomationPeer

## -description
Exposes [CaptureElement](../windows.ui.xaml.controls/captureelement.md) types to Microsoft UI Automation.

## -remarks
The Windows Runtime  [CaptureElement](../windows.ui.xaml.controls/captureelement.md) class creates a new [CaptureElementAutomationPeer](captureelementautomationpeer.md) as its [OnCreateAutomationPeer](../windows.ui.xaml/uielement_oncreateautomationpeer_1478162674.md) definition. [CaptureElement](../windows.ui.xaml.controls/captureelement.md) is sealed, so the normal scenario of deriving from the class and its existing peer isn't applicable to [CaptureElementAutomationPeer](captureelementautomationpeer.md).

Also, the [CaptureElement](../windows.ui.xaml.controls/captureelement.md) isn't focusable, which limits its participation in a Microsoft UI Automation tree view of the UI.

### Default peer implementation and overrides in **CaptureElementAutomationPeer**

[CaptureElementAutomationPeer](captureelementautomationpeer.md) has overrides of **Core** methods such that the associated [AutomationPeer](automationpeer.md) methods provide peer-specific information to a Microsoft UI Automation client.

+ [GetPattern](automationpeer_getpattern.md) reports no pattern support.
+ [GetClassName](automationpeer_getclassname.md) returns "CaptureElement".
+ [GetAutomationControlType](automationpeer_getautomationcontroltype.md) returns [AutomationControlType.Custom](automationcontroltype.md).
The peer also has other behaviors that are provided by the base [FrameworkElementAutomationPeer](frameworkelementautomationpeer.md) class. For more info, see "Base implementation in FrameworkElementAutomationPeer" section of [Custom automation peers](http://msdn.microsoft.com/library/aa8da53b-fe6e-40ac-9f0a-cb09637c87b4).

## -examples

## -see-also
[FrameworkElementAutomationPeer](frameworkelementautomationpeer.md), [CaptureElement](../windows.ui.xaml.controls/captureelement.md), [Custom automation peers](http://msdn.microsoft.com/library/aa8da53b-fe6e-40ac-9f0a-cb09637c87b4)