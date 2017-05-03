---
-api-id: T:Windows.UI.Xaml.Automation.Peers.TextBoxAutomationPeer
-api-type: winrt class
---

<!-- Class syntax.
public class TextBoxAutomationPeer : Windows.UI.Xaml.Automation.Peers.FrameworkElementAutomationPeer, Windows.UI.Xaml.Automation.Peers.ITextBoxAutomationPeer
-->

# Windows.UI.Xaml.Automation.Peers.TextBoxAutomationPeer

## -description
Exposes [TextBox](../windows.ui.xaml.controls/textbox.md) types to Microsoft UI Automation.

## -remarks
The Windows Runtime  [TextBox](../windows.ui.xaml.controls/textbox.md) class creates a new [TextBoxAutomationPeer](textboxautomationpeer.md) as its [OnCreateAutomationPeer](../windows.ui.xaml/uielement_oncreateautomationpeer_1478162674.md) definition. Derive your automation peer from [TextBoxAutomationPeer](textboxautomationpeer.md) if you are deriving a custom class from [TextBox](../windows.ui.xaml.controls/textbox.md) and want to add automation support for additional features that you enabled in your custom class. Then override [OnCreateAutomationPeer](../windows.ui.xaml/uielement_oncreateautomationpeer_1478162674.md) so that it returns your custom peer.

### Default peer implementation and overrides in **TextBoxAutomationPeer**

[TextBoxAutomationPeer](textboxautomationpeer.md) has overrides of **Core** methods such that the associated [AutomationPeer](automationpeer.md) methods provide peer-specific information to a Microsoft UI Automation client.

+ [GetPattern](automationpeer_getpattern.md) reports pattern support for [TextPattern](http://msdn.microsoft.com/library/ddcf7ecd-7ed2-4b57-82a7-c7e1608dbfa1) and [ValuePattern](http://msdn.microsoft.com/library/07277405-1172-42e5-af51-8e2c1ea06894), but see "TextPattern support" in this topic for more info.
+ [GetClassName](automationpeer_getclassname.md) returns "RichEditBox".
+ [GetAutomationControlType](automationpeer_getautomationcontroltype.md) returns [AutomationControlType.Edit](automationcontroltype.md).
+ [IsControlElement](automationpeer_iscontrolelement.md) returns **true**.
<!--not sure how this gets set cannot see in the partial cpp-->
The peer also has other behaviors that are provided by the base [FrameworkElementAutomationPeer](frameworkelementautomationpeer.md) class. For more info, see "Base implementation in FrameworkElementAutomationPeer" section of [Custom automation peers](http://msdn.microsoft.com/library/aa8da53b-fe6e-40ac-9f0a-cb09637c87b4).

### TextPattern support

 [TextBoxAutomationPeer](textboxautomationpeer.md) supports the **TextPattern** and **ValuePattern**  Microsoft UI Automation patterns. The support for these pattern is implemented as native code by the peer, so you won't see public API for the [TextBoxAutomationPeer](textboxautomationpeer.md) peer class that exposes the pattern implementation for extension. And you won't see [ITextRangeProvider](../windows.ui.xaml.automation.provider/itextrangeprovider.md) and the similar managed interfaces in the [TextBoxAutomationPeer](textboxautomationpeer.md) inheritance. But Microsoft UI Automation clients can use the **TextPattern** and **ValuePattern** patterns implemented by this peer and call the native API surface through Microsoft UI Automation.


<!--<p  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">specifics of the <xref targtype="iface" rid="winauto.uiauto_IUIAutomationTextPattern">TextPattern</xref> implementation .... not documented</p>-->

## -examples

## -see-also
[TextBox](../windows.ui.xaml.controls/textbox.md), [FrameworkElementAutomationPeer](frameworkelementautomationpeer.md), [Custom automation peers](http://msdn.microsoft.com/library/aa8da53b-fe6e-40ac-9f0a-cb09637c87b4)