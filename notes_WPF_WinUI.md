# WinUI and WPF Notes

## Get and Set Properties

Get and Set methods can _access_ and _update_ the values of private fields.

```C#
class Person
{
  private string name; // field
  public string Name   // property
  {
    get { return name; }
    set { name = value; }
  }
}

class Program
{
  static void Main(string[] args)
  {
    Person myObj = new Person();
    myObj.Name = "Liam";
    Console.WriteLine(myObj.Name);
  }
}
```

## ObservableObject Class

Implements: INotifyPropertyChanged, INotifyPropertyChanging

Includes methods concerning Property Change events.
