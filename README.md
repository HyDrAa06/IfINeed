# IfINeed

## LadyBugs
int fieldSize = int.Parse(Console.ReadLine());

            if (fieldSize > 1000)
            {
                Console.WriteLine("Wrong range of size.");
                
                throw new ArgumentOutOfRangeException(nameof(fieldSize));
                return;
            }

            int[] ladyBugsPositions = Console.ReadLine().Split().Select(int.Parse).ToArray();

            int[] field = new int[fieldSize];

            for(int i = 0; i < fieldSize; i++)
            {
                if (ladyBugsPositions.Contains(i))
                {
                    field[i] = 1;
                }
                else
                {
                    field[i] = 0;
                }
            }

            string command = Console.ReadLine();

            while (command != "end")
            {
                string[] commandArg = command.Split();
                int ladyBugPosition=int.Parse(commandArg[0]);
                string direction = commandArg[1];
                int flyLength = int.Parse(commandArg[2]);

                if(ladyBugPosition<0 || ladyBugPosition > field.Length - 1)
                {
                    continue;

                }

                if (field[ladyBugPosition] == 0)
                {
                    continue ;
                }

                field[ladyBugPosition] = 0;

                switch (direction)
                {
                    case "right":
                        {
                            if (ladyBugPosition + flyLength>field.Length-1)
                            {

                                break;
                            }
                                for (int i =ladyBugPosition + flyLength; i < field.Length; i+=flyLength)
                            {
                                

                                if (field[i] == 0)
                                {
                                    field[i] = 1;
                                    break;
                                }
                            }
                            break;
                        }
                    case "left":
                        {
                            break;
                        }
                    default:
                        {
                            break;
                        }
                }


                command=Console.ReadLine();
            }

            Console.Write(string.Join(" ", field));








## Triagnle
using System;

namespace Triangle
{
    internal class Program
    {
        static void Main(string[] args)
        {
            PrintTriangle(11);
        }

        static void PrintTriangle(int number)
        {
            for(int i =1; i <= number; i++)
            {
                PrintLine(0, i);                  
            }

            for (int i = number - 1; i > 0; i--)
            {
                PrintLine(0, i);
            }
        }

        static void PrintLine(int start, int end)
        {
            for (int J = start; J < end; J++)
            {
                Console.Write($"{J + 1} ");
            }
            Console.WriteLine();
        }


    }
}




using System;

namespace GreaterOfTwoValues
{
    internal class Program
    {
        static int GetMax(int n1, int n2)
        {
            int result = Math.Max(n1, n2);
            return result;
        }
        static string GetMax(string s1, string s2)
        {
            int difference = s1.CompareTo(s2);

            string result;

            if (difference < 0)
            {
                result = s2;
            }
            else
            {
                result = s1;
            }
            return result;
        }

        static char GetMax(char c1, char c2)
        {
            int difference = c1.CompareTo(c2);

            char result;

            if(difference < 0)
            {
                result = c2;              
            }
            else
            {
                result = c1;
            }
            return result;
        }
        static void Main(string[] args)
        {
            int maxInt = GetMax(1, 10);
            string maxString = GetMax("aaa", "bbb");
            char maxChar = GetMax('a', 'z');

            Console.WriteLine(maxInt);
            Console.WriteLine(maxChar);
            Console.WriteLine(maxString);
        }
    }
}
