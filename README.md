<pre lang=C#>
using System;
using System.CodeDom;
using System.Collections.Generic;
using System.Diagnostics.Contracts;
using System.Linq;
using System.Runtime.InteropServices;
using System.Text;
using System.Threading.Tasks;

namespace _4._1._2._3_ObjectOrientedProgramming
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //• object
            Ball myBall = new Ball(); //• instantiation
            myBall.SetDiameter(10);//• encapsulation
            Console.WriteLine(myBall.Volume());
            Football myFootball = new Football();
            myFootball.SetDiameter(10);
            Console.WriteLine(myFootball.Volume());
            Building b = new Building(3);
            Console.WriteLine(b.TotalArea());
            Hotel h = new Hotel(4,true);
        }
    }
}
//Be familiar with the concepts of:
//• class
class Ball
{
    private double diameter;//• encapsulation

    public void SetDiameter(double diam)
    {
        diameter = diam;
    }
    public virtual double Volume()
    {
        double vol = 4.0 / 3.0 * Math.PI * Math.Pow(diameter / 2.0, 3);
        return vol;
    }
}
class Football : Ball//• inheritance
{
    public override double Volume()//• polymorphism
    {
        double vol = base.Volume();
        return  5*vol;
    }
}

class Building
{
    protected List<Room> rooms;
    protected List<Resident> residents;
    public Building(int numRooms)
    {
        rooms = new List<Room>();
        residents = new List<Resident>();
        for (int i = 0; i < numRooms; i++)
        {
            double width, length, height;
            string type;
            Console.Write("Enter room width: ");
            width = Convert.ToDouble(Console.ReadLine());
            Console.Write("Enter room length: ");
            length = Convert.ToDouble(Console.ReadLine());
            Console.Write("Enter room height: ");
            height = Convert.ToDouble(Console.ReadLine());
            Console.Write("Enter the type of room: ");
            type = Console.ReadLine();
            Room room = new Room(width,length,height,type);//• composition
            rooms.Add(room);
        }

    }
    public void addResidents(Resident resident)//• aggregation
    {
        residents.Add(resident);
    }
    public double TotalArea()
    {
        double area = 0;
        foreach(Room room in rooms)
        {
            area += room.getArea();
        }
        return area;
    }
    
}
class Room
{
    private double width;
    private double height;
    private double length;
    private string type;

    public Room(double width, double height, double length, string type)
    {
        this.width = width;
        this.height = height;
        this.length = length;
        this.type = type;
    }
    public double getArea()
    {
        return width*length;
    }
    public double getVoluem()
    {
        return height*width*length;
    }
}

class Resident
{
    private string ResName;
    private string ResType;
    public Resident(string ResName, string ResType)
    {
        this.ResName = ResName;
        this.ResType = ResType;

    }
}
class Hotel : Building
{
    private bool hasPool;
    public Hotel(int numRooms, bool hasPool) : base(numRooms)
    {
        this.hasPool = hasPool;
    }
}
//• encapsulation

//• aggregation

//• polymorphism
//• overriding.
        </pre>
