# SearchAThing.Snippets
VS Snippets

## Installation

From Visual Studio / Tools / Code Snipper Manager, add the folder SearchAThing.Snippet.

## Usage

Type the snippet name and tab twice.

## Snippets

### dpp

Defaults:
- type (int)
- property (MyProperty)
- defaultValue (null)

```csharp
#region MyProperty [dpp]
public static readonly DependencyProperty MyPropertyProperty =
DependencyProperty.Register("MyProperty", typeof(int), typeof(Global), new FrameworkPropertyMetadata(null));

public int MyProperty
{
    get
    {
        return (int)GetValue(MyPropertyProperty);
    }
    set
    {
        SetValue(MyPropertyProperty, value);
    }
}
#endregion
```