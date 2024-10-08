using System;

class Program
{
    static void Main(string[] args)
    {
        Random rnd = new Random();
        int choice = 0;

        while (choice != 4)
        {
            // Display Menu
            Console.WriteLine("Welcome to Crimson Crust! Choose your pizza option:");
            Console.WriteLine("1. Plain Topping-less Pizza Slice");
            Console.WriteLine("2. Cheese Pizza Slice");
            Console.WriteLine("3. Pepperoni Pizza Slice");
            Console.WriteLine("4. Exit");
            Console.Write("Enter your choice (1-4): ");

            // Get user input and parse it as integer
            string input = Console.ReadLine();
            if (int.TryParse(input, out choice))
            {
                // Call respective function based on choice
                switch (choice)
                {
                    case 1:
                        DisplayPlainPizza(rnd);
                        break;
                    case 2:
                        DisplayCheesePizza(rnd);
                        break;
                    case 3:
                        DisplayPepperoniPizza(rnd);
                        break;
                    case 4:
                        Console.WriteLine("Goodbye!");
                        break;
                    default:
                        Console.WriteLine("Invalid choice. Please try again.");
                        break;
                }
            }
            else
            {
                Console.WriteLine("Invalid choice. Please try again.");
            }
        }
    }

    // Function to display a plain pizza slice
    static void DisplayPlainPizza(Random rnd)
    {
        int rows = rnd.Next(8, 13); // Random rows between 8 and 12
        Console.WriteLine("\nPlain Pizza Slice:");
        DrawPizzaSlice(rows, ' ');
    }

    // Function to display a cheese pizza slice
    static void DisplayCheesePizza(Random rnd)
    {
        int rows = rnd.Next(8, 13); // Random rows between 8 and 12
        Console.WriteLine("\nCheese Pizza Slice:");
        DrawPizzaSlice(rows, '*'); // Cheese represented by '*'
    }

    // Function to display a pepperoni pizza slice
    static void DisplayPepperoniPizza(Random rnd)
    {
        int rows = rnd.Next(8, 13); // Random rows between 8 and 12
        Console.WriteLine("\nPepperoni Pizza Slice:");
        DrawPizzaSlice(rows, '*', rnd); // Cheese as '*' and pepperoni as '[]'
    }

    // Function to draw the pizza slice with optional pepperoni
    static void DrawPizzaSlice(int rows, char filling, Random rnd = null)
    {
        for (int i = 1; i <= rows; i++)
        {
            // Draw the outline of the pizza
            for (int j = 0; j < i; j++)
            {
                if (j == 0 || j == i - 1)
                {
                    Console.Write("#"); // Pizza crust outline
                }
                else
                {
                    if (rnd != null && rnd.Next(0, 4) == 0) // 25% chance for pepperoni
                    {
                        Console.Write("[]"); // Pepperoni
                    }
                    else
                    {
                        Console.Write(filling); // Filling (cheese or empty for plain)
                    }
                }
            }
            Console.WriteLine(); // Move to the next row
        }
    }
}
