---
-api-id: M:Windows.UI.Xaml.Data.BindingOperations.SetBinding(Windows.UI.Xaml.DependencyObject,Windows.UI.Xaml.DependencyProperty,Windows.UI.Xaml.Data.BindingBase)
-api-type: winrt method
---

<!-- Method syntax
public void SetBinding(Windows.UI.Xaml.DependencyObject target, Windows.UI.Xaml.DependencyProperty dp, Windows.UI.Xaml.Data.BindingBase binding)
-->

# Windows.UI.Xaml.Data.BindingOperations.SetBinding

## -description
Associates a [Binding](binding.md) with a target property on a target object. This method is the code equivalent to using a [{Binding} markup extension](http://msdn.microsoft.com/library/3bafe7b5-af33-487f-9ad5-beafd65d04c3) in XAML markup.

## -parameters
### -param target
The object that should be the target of the evaluated binding.

### -param dp
The property on the target to bind, specified by its identifier. These identifiers are usually available as static read-only properties on the type that defines the *target* object, or one of its base types. You can also bind to attached properties, but see Remarks.

### -param binding
The binding to assign to the target property. This [Binding](binding.md) should be initialized: important [Binding](binding.md) properties such as [Path](binding_path.md) should already be set before passing it as the parameter.

## -remarks
You can bind to custom dependency properties or custom attached properties, the identifier you pass as the *dp* parameter doesn't have to be a Windows Runtime defined property.

[BindingOperations.SetBinding](bindingoperations_setbinding.md) is a static utility method, and does basically the same thing as [FrameworkElement.SetBinding](../windows.ui.xaml/frameworkelement_setbinding.md). It's more common to use [FrameworkElement.SetBinding](../windows.ui.xaml/frameworkelement_setbinding.md) because it's an instance method. One important difference though is that [BindingOperations.SetBinding](bindingoperations_setbinding.md) can use a *target* value of any [DependencyObject](../windows.ui.xaml/dependencyobject.md), whereas [FrameworkElement.SetBinding](../windows.ui.xaml/frameworkelement_setbinding.md) can by definition only be used for a [FrameworkElement](../windows.ui.xaml/frameworkelement.md) target. This doesn't usually matter for most Windows Runtime classes used for XAML UI, because these are mostly [FrameworkElement](../windows.ui.xaml/frameworkelement.md) subclasses anyways. But the distinction might matter if you are targeting bindings on your own custom classes that derive from [DependencyObject](../windows.ui.xaml/dependencyobject.md) or [UIElement](../windows.ui.xaml/uielement.md).

<!--Other frameworks provide an expression object as the return value, which can be used to manipulate properties of the binding after it is established but without requiring the binding to be remade. Not clear if anything like that functionality exists.-->

> [!NOTE]
> Calling the [SetBinding](bindingoperations_setbinding.md) method and passing in a new [Binding](binding.md) object won't necessarily remove an existing binding. Instead, you should first call the [DependencyObject.ClearValue](../windows.ui.xaml/dependencyobject_clearvalue.md) method, then call [SetBinding](bindingoperations_setbinding.md).

### Binding to attached properties

You can put data bindings on any attached properties that a target object supports. Technically an [DependencyObject](../windows.ui.xaml/dependencyobject.md) supports all the possible attached properties, but you'd usually only set a binding on an attached property that's relevant to that object or your scenario. For example you would set a binding on [Grid.Row](../windows.ui.xaml.controls/grid_row.md) only if you anticipate that the target element has a [Grid](../windows.ui.xaml.controls/grid.md) parent that will use that info. Specify the *dp* parameter as the dependency property identifier that exists on the attached property's owner class (for the [Grid.Row](../windows.ui.xaml.controls/grid_row.md) example, that identifier is [Grid.RowProperty](../windows.ui.xaml.controls/grid_rowproperty.md)). You won't find that identifier on the target because it's an attached property. For more info on attached properties, see [Attached properties overview](http://msdn.microsoft.com/library/098c1de0-d640-48b1-9961-d0adf33266e2).

## -examples

## -see-also
[Binding](binding.md), [XAML data binding sample](http://go.microsoft.com/fwlink/p/?linkid=226854), [Data binding in depth](http://msdn.microsoft.com/library/41e1b4f1-6caf-4128-a61a-4e400b149011)