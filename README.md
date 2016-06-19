# SearchAThing.Snippets
VS Snippets

## Installation

From Visual Studio / Tools / Code Snipper Manager, add the folder SearchAThing.Snippet.

## Usage

Type the snippet name and tab twice.

## Snippets

### dpp

*Dependency property*

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

### dppc

*Dependency property with OnPropertyChanged handler*

Defaults:
- type (int)
- property (MyProperty)
- defaultValue (null)

```csharp
#region MyProperty [dppc]
public static readonly DependencyProperty MyPropertyProperty =
    DependencyProperty.Register("MyProperty", typeof(int), typeof(Global), new FrameworkPropertyMetadata(null, OnMyPropertyChanged));

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

static void OnMyPropertyChanged(DependencyObject source, DependencyPropertyChangedEventArgs e)
{
    var obj = (Global)source;
}
#endregion
```

### propc

*Property with notify property changed*

Defaults:
- type (int)
- property (MyProperty)
- defaultValue (null)

```csharp
#region MyProperty [propc]
int _MyProperty;
public int MyProperty
{
    get
    {
        return _MyProperty;
    }
    set
    {
        if (_MyProperty != value)
        {
            _MyProperty = value;
            SendPropertyChanged("MyProperty");
        }
    }
}
#endregion
```

### propce

*Property changed event handler*

```csharp
#region INotifyPropertyChanged [propce]       
public event PropertyChangedEventHandler PropertyChanged;
protected void SendPropertyChanged(string propertyName)
{
    PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
}
#endregion
```

### propf

*Property with field*

Defaults:
- type (int)
- property (MyProperty)

```csharp
#region MyProperty [propf]
int _MyProperty;
public int MyProperty
{
    get
    {
        return _MyProperty;
    }
    set
    {
        _MyProperty = value;
    }
}
#endregion
```