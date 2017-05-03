---
-api-id: M:Windows.UI.Xaml.UIElement.CapturePointer(Windows.UI.Xaml.Input.Pointer)
-api-type: winrt method
---

<!-- Method syntax
public bool CapturePointer(Windows.UI.Xaml.Input.Pointer value)
-->

# Windows.UI.Xaml.UIElement.CapturePointer

## -description
Sets pointer capture to a [UIElement](uielement.md). Once captured, only the element that has capture will fire pointer-related events.

## -parameters
### -param value
The pointer object reference.

## -returns
**true** if the object has pointer capture; otherwise, **false**.

## -remarks
You can only successfully capture the pointer if that pointer is in a pressed state ([Pointer.IsInContact](../windows.ui.xaml.input/pointer_isincontact.md) should be **true**). What physically constitutes being pressed will vary based on the pointer device type (mouse button pressed, touch point down, stylus in contact). If you attempt to capture a pointer that isn't pressed, or where the pointer was previously pressed but is now released, [CapturePointer](uielement_capturepointer.md) returns **false**. Existing captures aren't affected by a [CapturePointer](uielement_capturepointer.md) call that returned **false**.

You typically capture the pointer within a [PointerPressed](uielement_pointerpressed.md) event handler. The [Pointer](../windows.ui.xaml.input/pointer.md) instance you get from the [PointerRoutedEventArgs](../windows.ui.xaml.input/pointerroutedeventargs.md) event data of your [PointerPressed](uielement_pointerpressed.md) handler is the value you should pass for the *value* parameter when you call [CapturePointer](uielement_capturepointer.md) from within your handler's code.

You typically capture the pointer because you want the current pointer action to initiate a behavior in your app. In this case you typically don't want other elements to handle any other events that come from that pointer's actions, until your behavior is either completed or is canceled by releasing the pointer capture. If a pointer is captured, only the element that has capture gets the pointer's input events, and other elements don't fire events even if the pointer moves into their bounds. For example, consider a UI that has two adjacent elements. Normally, if you moved the pointer from one element to the other, you'd first get [PointerMoved](uielement_pointermoved.md) events from the first element, and then from the second element. But if the first element has captured the pointer, then the first element continues to receive [PointerMoved](uielement_pointermoved.md) events even if the captured pointer leaves its bounds. Also, the second element doesn't fire [PointerEntered](uielement_pointerentered.md) events for a captured pointer when the captured pointer enters it.

<!--TODO something about visual prompts for capture, how do you do this? Search example code ...-->
The pointer capture state and generating the events that are related to pointer capture isn't entirely up to app code. If the user releases the pointer, that generates a [PointerReleased](uielement_pointerreleased.md) event, and pointer captures associated with that pointer are lost. This also fires [PointerCaptureLost](uielement_pointercapturelost.md) on the original capturing element.

In most cases the pointer capture will be released automatically when the user completes an input action that releases the previous pointer capture (lifting a touch point, releasing the left mouse button, taking the stylus out of range). Another condition that might release capture is any action that also fires a [PointerCanceled](uielement_pointercanceled.md) event. Your app can typically rely on the capture-release behavior associated with user input actions, without having to specifically cancel a pointer capture with [ReleasePointerCapture](uielement_releasepointercapture.md) or [ReleasePointerCaptures](uielement_releasepointercaptures.md). For more info, see [Mouse interactions](http://msdn.microsoft.com/library/c8a158ef-70a9-4ba2-a270-7d08125700ac).

The [CapturePointer](uielement_capturepointer.md) method will return **false** if the pointer was already captured.


<!--Needs more investigation: Another reason why the CapturePointer method may return false is that you are calling it on an object that doesn't permit pointer capture.-->
A [UIElement](uielement.md) can capture more than one pointer point at a time. Use the *value* parameter to indicate the [Pointer](../windows.ui.xaml.input/pointer.md) instance you want to capture.

The input events that represent gestures (such as [Tapped](uielement_tapped.md) or [DoubleTapped](uielement_doubletapped.md)) are usually only fired after a pointer is released, so you shouldn't attempt to capture a pointer in event handlers for gesture events. The [Pointer](../windows.ui.xaml.input/pointer.md) reference in event data for gesture events won't be permitted to initiate a pointer capture.



> [!TIP]
> Don't try to use [CapturePointer](uielement_capturepointer.md) outside the scope of pointer-relevant input event handlers. Unless you have a [Pointer](../windows.ui.xaml.input/pointer.md) that you're sure is associated with a pointer that's permitted to have pointer capture at that time, your [CapturePointer](uielement_capturepointer.md) call won't have any effect. There's no practical way to generate a new [Pointer](../windows.ui.xaml.input/pointer.md) and call [CapturePointer](uielement_capturepointer.md) using that new pointer. You should only use the [Pointer](../windows.ui.xaml.input/pointer.md) references the system is providing to you through the event data of the pointer-related input events.

## -examples
This example shows calling [CapturePointer](uielement_capturepointer.md) based on handling [PointerPressed](uielement_pointerpressed.md). It also shows a pattern for tracking and counting pointer references.



[!code-csharp[Scenario2Code](../windows.ui.xaml/code/input/csharp/Scenario2.xaml.cs#SnippetScenario2Code)]

[!code-vb[Scenario2Code](../windows.ui.xaml/code/input/vbnet/Scenario2.xaml.vb#SnippetScenario2Code)]

## -see-also
[Pointer](../windows.ui.xaml.input/pointer.md), [ReleasePointerCapture](uielement_releasepointercapture.md), [Quickstart: Touch input](http://msdn.microsoft.com/library/f10bafee-8792-4a57-ae84-aa11ab95355a), [Input sample](http://go.microsoft.com/fwlink/p/?linkid=226855)
soft.com/fwlink/p/?linkid=226855)