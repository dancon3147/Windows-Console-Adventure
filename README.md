# Windows-Console-Adventure
//Creating a Windows Game played through the Console

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace ConsoleApplication1
{
class Program
    {
        class Player
        {

            public string name;
            public string type;

            public double Health;
            public double Shield;
            public double HitPoints;

            public double strike;

            public double pouch;


        }
        class AiPlayer
        {
            public string name;
            public string type;

            public double Health;
            public double Shield;
            public double HitPoints;
            public double strike;

            public double pouch;
        }

        class Potion
        {
            public string name;
            public double Health_Potion;
            public double Poison_Potion;
            public double Poison_Cure;
            public double Cost;

        }
        class Money
        {
            public double gold;
            public double silver;
        }

        static void Main(string[] args)
        {
            Potion HP = new Potion();
            HP.Health_Potion = +25.5;
            HP.Cost = -10.5;
            HP.name = "Health Potion";

            Potion PP = new Potion();
            PP.Poison_Potion = -10.5;
            PP.Cost = -20.0;
            PP.name = "Poison";
            

            Potion PC = new Potion();
            PC.Poison_Cure = +11.5;
            PC.Cost = -22.25;
            PC.name = "Poison Cure";

            Money Gold = new Money();
            Gold.gold = 1.0;
            Money Silver = new Money();
            Silver.silver = 0.5;

            Player p1 = new Player();
            p1.Health = 100.0;
            p1.HitPoints = p1.Health + p1.Shield;
            p1.pouch = 250.0;
            p1.Shield = 0.0;

            AiPlayer p2 = new AiPlayer();
            p2.Health = 100.0;
            p2.name = "Aquelleo";
            p2.type = "Sorcerer";
            p2.strike = 18.5;
            p2.Shield = 100.0;
            p2.HitPoints = p2.Health + p2.Shield;

            AiPlayer a1 = new AiPlayer();
            a1.name = "Thug";
            a1.type = "Chump";
            a1.Shield = 20.0;
            a1.Health = 90.0;
            a1.pouch = 35.75;
            a1.strike = -9.25;
            a1.HitPoints = a1.Health + a1.Shield;

            string start;
            Console.WriteLine("Welcome to the Kingdom");
            Console.WriteLine("Would you like to start yes or no?");
            start = Console.ReadLine();
            while (start == "no")
            {
                Console.WriteLine("Welcome to the Kingdom");
                Console.WriteLine("Would you like to start yes or no?");


                start = Console.ReadLine();
            }
                if (start == "yes" || start == "y" || start == "Yes" || start == "YES" || start =="Y")
                {
                    Console.WriteLine("Welcome to your journey, what is your name?");
                }
        
            p1.name = Console.ReadLine();
            Console.WriteLine("What is your character type " + p1.name + "? You can be a Mage, a Warrior, a Thief,\n or a Vampire.");

            string answer;
            answer = Console.ReadLine(); // alliws player to choose their character type

            //p1 character type will be "Mage"
            if (answer == "mage" || answer == "Mage" || answer == "MAGE")
            {
                p1.type = "Mage";
            }
        
            

            //p1 charcter type will be "Warrior
            if (answer == "Warrior" || answer == "WARRIOR" || answer == "warrior")
            {
                p1.type = "Warrior";
            }

            //p1 character type will be "Thief"
            if (answer == "Thief" || answer =="THIEF" || answer == "thief")
            {
                p1.type = "Thief";
            }

            //p1 character type will be "Vampire"

            if (answer == "Vampire" || answer == "VAMPIRE" || answer == "vampire")
            {
                p1.type = "Vampire";
            }



            Console.WriteLine("So " + p1.name + " you are a " + p1.type + ".");

            if (p1.type == "Mage")
            {
                p1.strike = -10.5;
            }
            if (p1.type == "Warrior")
            {
                p1.strike = -14.5;
            }
            if (p1.type == "Thief")
            {
                p1.strike = -9.5;
            }
            if (p1.type == "Vampire")
            {
                p1.strike = -16.5;
            }
             

            Console.WriteLine("Before you set off on your journey it may be wise to buy a shield from a \n local shop. Would you like to buy a shield for 20 gold yes or no?");

            start = Console.ReadLine();
            if (start == "yes" || start == "y" || start == "Y" || start == "YES")
            {
                p1.Shield = 100.0;
                p1.pouch = p1.pouch - 20.0;
                Console.WriteLine("Thank you for your patronage, We wish you the best of luck " + p1.name + " on your \n journey. We hope it is a bountiful one.");
                Console.Write(p1.pouch + " Gold remains");
                p1.HitPoints = p1.Health + p1.Shield;
                Console.WriteLine("\nHitpoints have raised to " + p1.HitPoints + ".");
            }
            if (start == "NO" || start == "no" || start == "N" || start == "n")
            {
                p1.Shield = 0.0;
                Console.WriteLine("Very well, we will still wish you safe passage, on your journey");
            }
            Console.WriteLine("While our hero is traveling through the woods he encounters an enemy;\n " + a1.name + ". This enemy sneak attacks our hero getting the first \nstrike and an advantage.");
            p1.HitPoints = p1.HitPoints + a1.strike;
           
                Console.WriteLine("HP: " + p1.HitPoints);
                Console.WriteLine(p1.name + ": \nAttack (a) \nRun    (r)");
                string AttackRun;
                AttackRun = Console.ReadLine();
                if (AttackRun == "a")
                {
                    a1.HitPoints = a1.HitPoints + p1.strike;
                    Console.Write(a1.name + " HP: " + a1.HitPoints);
                }
            
                if (AttackRun == "r")
                {
                     Console.WriteLine(p1.name + " is running away.");
                }

                while (a1.HitPoints > 0)
            {
                p1.HitPoints = p1.HitPoints + a1.strike;
                Console.WriteLine(p1.name +" HP: " + p1.HitPoints);
                Console.WriteLine(p1.name + ": \nAttack (a) \nRun    (r)");
                AttackRun = Console.ReadLine();
                if (AttackRun == "a")
                {
                    a1.HitPoints = a1.HitPoints + p1.strike;
                    Console.Write(a1.name + " HP: " + a1.HitPoints+" ");
                    Console.WriteLine(a1.name + " ATTACKS ");
                }
             
                else
                {
                    Console.WriteLine("\n" + p1.name + " has ran away!!!");
                    break;
                }
            }
            if (a1.HitPoints <= 0)
            {
                Console.WriteLine("It appears that " + a1.name + " is dead. \nIt seems that you have obtained his pouch.\n");
                p1.pouch = p1.pouch + a1.pouch;
                Console.WriteLine(p1.name + " now has " + p1.pouch + " gold.");
            }
            Console.WriteLine("As our hero continues forward, he comes across a new town, Bunswick.\n" +
                              "In this new town there is a potion shop. Should we visit one,\nyes or no?");
           
            start = Console.ReadLine();

            if (start == "Y" || start == "y"|| start == "YES" || start == "yes" || start == "Yes")
            {
                Console.WriteLine("Our hero enters the Potion Shop, and is greeted by the keeper of the shop, \n" +
                                 "Keeper: Well, hello ther stranger haven't seen you around here before. \n" +
                                 "What's your name?\n " +
                                 "Our hero says: " + p1.name + ", and I am here to buy some potions.\n");
                                                                "Our hero says: " + p1.name + ", and I am here to buy some potions.\n" +
                                 "Keeper: Well it's bloody good to meet you " + p1.name + ". We have the best \nhealth potion at a fair price 10.5 gold, would you like to buy one?");
                string YoN;
                YoN = Console.ReadLine();
                if (YoN == "Y" || YoN == "y" || YoN == "YES" || YoN == "yes" || YoN == "Yes")
                {
                    p1.pouch = p1.pouch + HP.Cost;
                    Console.WriteLine(p1.name + " now has " + p1.pouch + " gold available, he has also obtained 1 " + HP.name + ".");
                    break;
                }
                if (YoN == "N" || YoN == "n" || YoN == "NO" || YoN == "no" || YoN == "No")
                {
                    Console.WriteLine("Keeper: Very well get hell out of my shop!");
                    Console.WriteLine("You may be making a big mistake, are you sure?");
                    
                    if (YoN == "Y" || YoN == "y" || YoN == "YES" || YoN == "yes" || YoN == "Yes")
                    {
                        Console.WriteLine("Very well");
                        break;
                    }
                }
            }

            Console.ReadLine();
        }
    }
}
