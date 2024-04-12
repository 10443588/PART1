# PART1
using System;

namespace Part1
{
    public class Program
    {
        static void Main(string[] args)
        {
            Recipe recipe = new Recipe();
            recipe.EnterRecipe();
            recipe.DisplayRecipe();

            double factor = GetScalingFactor();

            recipe.ScaleRecipe(factor);
            recipe.DisplayRecipe();

            recipe.ClearData();
        }

        static double GetScalingFactor()
        {
            double factor;
            while (true)
            {
                Console.Write("\nEnter the scaling factor (0.5, 2, or 3): ");
                string input = Console.ReadLine().Trim();

                if (double.TryParse(input, out factor) && (factor == 0.5 || factor == 2 || factor == 3))
                {
                    return factor;
                }
                else
                {
                    Console.WriteLine("Invalid input. Please enter 0.5, 2, or 3");
                }
            }
        }
    }
}
using System;

namespace Part1
{
    public class Recipe
    {
        public string[] Ingredients { get; set; }
        public double[] Quantities { get; set; }
        public string[] Units { get; set; }
        public string[] Steps { get; set; }

        public void EnterRecipe()
        {
            Console.Write("Enter the number of ingredients: ");
            int numIngredients = int.Parse(Console.ReadLine());

            Ingredients = new string[numIngredients];
            Quantities = new double[numIngredients];
            Units = new string[numIngredients];

            Console.WriteLine("Enter ingredients:");
            
            for (int i = 0; i < numIngredients; i++)
            {
                Console.Write($"Ingredient {i + 1} name: ");
                Ingredients[i] = Console.ReadLine();

                Console.Write($"Quantity of {Ingredients[i]}: ");
                Quantities[i] = double.Parse(Console.ReadLine());

                Console.Write($"Unit of measurement for {Ingredients[i]}: ");
                Units[i] = Console.ReadLine();
            }

            Console.Write("Enter the number of steps: ");
            int numSteps = int.Parse(Console.ReadLine());

            Steps = new string[numSteps];
            Console.WriteLine("Enter steps:");

            for (int i = 0; i < numSteps; i++)
            {
                Console.Write($"Step {i + 1}: ");
                Steps[i] = Console.ReadLine();
            }
        }

        public void DisplayRecipe()
        {
            Console.WriteLine("\nRecipe:");
            Console.WriteLine("Ingredients:");

            for (int i = 0; i < Ingredients.Length; i++)
            {
                Console.WriteLine($"{Quantities[i]} {Units[i]} of {Ingredients[i]}");
            }

            Console.WriteLine("\nSteps:");
            
            for (int i = 0; i < Steps.Length; i++)
            {
                Console.WriteLine($"{i + 1}. {Steps[i]}");
            }
        }

        public void ScaleRecipe(double factor)
        {
            for (int i = 0; i < Quantities.Length; i++)
            {
                Quantities[i] *= factor;
            }
        }

        public void ClearData()
        {
            Ingredients = null;
            Quantities = null;
            Units = null;
            Steps = null;
        }
    }
}

            
