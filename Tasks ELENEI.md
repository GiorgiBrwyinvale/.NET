# 1. Create the IShape Interface
This interface will define a method CalculateArea that each shape will implement.
```
public interface IShape
{
    double CalculateArea();
}
```
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# 2. Implement the Circle Class

```
public class Circle : IShape
{
    public double Radius { get; set; }

    // Constructor to initialize the radius
    public Circle(double radius)
    {
        Radius = radius;
    }

    // Calculate the area of a circle
    public double CalculateArea()
    {
        return Math.PI * Radius * Radius;
    }
}
```
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# 3. Implement the Rectangle Class
```
public class Rectangle : IShape
{
    public double Width { get; set; }
    public double Height { get; set; }

    // Constructor to initialize the width and height
    public Rectangle(double width, double height)
    {
        Width = width;
        Height = height;
    }

    // Calculate the area of a rectangle
    public double CalculateArea()
    {
        return Width * Height;
    }
}
```
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# 4. Implement the Triangle Class
```
public class Triangle : IShape
{
    public double Base { get; set; }
    public double Height { get; set; }

    // Constructor to initialize the base and height
    public Triangle(double baseLength, double height)
    {
        Base = baseLength;
        Height = height;
    }

    // Calculate the area of a triangle
    public double CalculateArea()
    {
        return 0.5 * Base * Height;
    }
}
```
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# 5. Demonstrate Polymorphism
```
class Program
{
    static void Main(string[] args)
    {
        // Create instances of different shapes
        IShape circle = new Circle(5.0);
        IShape rectangle = new Rectangle(4.0, 6.0);
        IShape triangle = new Triangle(3.0, 5.0);

        // Add shapes to a list to demonstrate polymorphism
        List<IShape> shapes = new List<IShape> { circle, rectangle, triangle };

        // Calculate and display the area for each shape
        foreach (var shape in shapes)
        {
            Console.WriteLine($"The area of the {shape.GetType().Name} is: {shape.CalculateArea()}");
        }
    }
}
```
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# TASK 2
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# 1. Create the Person Class
```
public class Person
{
    public string Name { get; set; }
    public string PhoneNumber { get; set; }

    // Constructor to initialize the contact details
    public Person(string name, string phoneNumber)
    {
        Name = name;
        PhoneNumber = phoneNumber;
    }

    // Override ToString method to return the person's details in a readable format
    public override string ToString()
    {
        return $"Person - Name: {Name}, Phone Number: {PhoneNumber}";
    }
}
```
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# 2. Create the ContactsManager Class

```
public interface IContactManager
{
    void AddContact(Person contact);
    Person GetContact(string name);
    void PrintAllContacts();
    string GetAllContacts();
}

public class ContactsManager : IContactManager
{
    private List<Person> contacts = new List<Person>();

    // Add a contact to the contacts list
    public void AddContact(Person contact)
    {
        contacts.Add(contact);
    }

    // Retrieve a contact by name
    public Person GetContact(string name)
    {
        return contacts.FirstOrDefault(c => c.Name.Equals(name, StringComparison.OrdinalIgnoreCase));
    }

    // Print all contacts
    public void PrintAllContacts()
    {
        foreach (var contact in contacts)
        {
            Console.WriteLine(contact.ToString());
        }
    }

    // Return all contacts as a string
    public string GetAllContacts()
    {
        return string.Join(Environment.NewLine, contacts.Select(c => c.ToString()));
    }
}
```

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# 3. Demonstration of Usage in Program.cs
```
class Program
{
    static void Main(string[] args)
    {
        IContactManager contactManager = new ContactsManager();

        // Add contacts
        contactManager.AddContact(new Person("Merab", "2606060"));
        contactManager.AddContact(new Person("John", "123456789"));
        contactManager.AddContact(new Person("Jane", "987654321"));

        // Retrieve a contact
        Person person = contactManager.GetContact("John");
        if (person != null)
        {
            Console.WriteLine("Contact found: " + person);
        }
        else
        {
            Console.WriteLine("Contact not found.");
        }

        // Print all contacts
        Console.WriteLine("\nAll contacts:");
        contactManager.PrintAllContacts();

        // Get all contacts as string
        Console.WriteLine("\nAll contacts as string:");
        Console.WriteLine(contactManager.GetAllContacts());
    }
}
```

