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
