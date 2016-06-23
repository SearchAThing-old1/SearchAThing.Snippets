<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [SearchAThing.Snippets](#searchathingsnippets)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Snippets](#snippets)
    - [pg](#pg)
    - [pgs](#pgs)
    - [pgps](#pgps)
    - [pgis](#pgis)
    - [pf](#pf)
    - [pfig](#pfig)
    - [pfi](#pfi)
    - [pce](#pce)
    - [pc](#pc)
    - [dp](#dp)
    - [dpc](#dpc)
    - [obc](#obc)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# SearchAThing.Snippets
VS Snippets

## Installation

From Visual Studio / Tools / Code Snipper Manager, add the folder SearchAThing.Snippet.

## Usage

Type the snippet name and tab twice.

## Snippets

### pg

*Property with only get*

Defaults:
- type (int)
- property (MyProperty)
- default value (0)

```csharp
#region MyProperty [pg]
public int MyProperty
{
    get
    {
        return 0;
    }
}
#endregion
```

### pgs

*Property get/set*

Defaults:
- type (int)
- property (MyProperty)

```csharp
#region MyProperty [pgs]
public int MyProperty { get; set; }
#endregion
```

### pgps

*Property get/private set*

Defaults:
- type (int)
- property (MyProperty)

```csharp
#region MyProperty [pgps]
public int MyProperty { get; private set; }
#endregion
```

### pgis

*Property get/internal set*

Defaults:
- type (int)
- property (MyProperty)

```csharp
#region MyProperty [pgis]
public int MyProperty { get; internal set; }
#endregion
```

### pf

*Property with field*

Defaults:
- type (int)
- property (MyProperty)

```csharp
#region MyProperty [pf]
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

### pfg

*Property only get w/field*

Defaults:
- type (object)
- property (MyProperty)

```csharp
#region MyProperty [pfg]
object _MyProperty;
public object MyProperty
{
    get
    {
        if (_MyProperty == null) _MyProperty = new object();
        return _MyProperty;
    }
}
#endregion
```

### pfi

*Property with field and init construct*

Defaults:
- type (int)
- property (MyProperty)

```csharp
#region MyProperty [pfi]
int _MyProperty;
public int MyProperty
{
    get
    {
        if (_MyProperty == null) _MyProperty = new int();
        return _MyProperty;
    }
    set
    {
        _MyProperty = value;
    }
}
#endregion
```

### pce

*Property changed event handler*

```csharp
#region INotifyPropertyChanged [pce]       
public event PropertyChangedEventHandler PropertyChanged;
protected void SendPropertyChanged(string propertyName)
{
    PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
}
#endregion
```

### pc

*Property with notify property changed*

Defaults:
- type (int)
- property (MyProperty)
- defaultValue (null)

```csharp
#region MyProperty [pc]
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

### dp

*Dependency property*

Defaults:
- type (int)
- property (MyProperty)
- defaultValue (null)

```csharp
#region MyProperty [dp]
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

### dpc

*Dependency property with OnPropertyChanged handler*

Defaults:
- type (int)
- property (MyProperty)
- defaultValue (null)

```csharp
#region MyProperty [dpc]
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

### obc

*Observable Collection*

Defaults:
- type (int)

```csharp
using System.Collections.ObjectModel;
//...
ObservableCollection<int> obc;
```