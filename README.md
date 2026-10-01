using System;
using System.Collections.Generic;

namespace UniversityApp
{
   
    class Person
    {
        public string Name { get; set; }

        public Person(string name)
        {
            Name = name;
        }

        public virtual void DisplayInfo()
        {
            Console.WriteLine($"Name: {Name}");
        }
    }

    
    class Student : Person
    {
        public int StudentId { get; set; }

        public Student(string name, int studentId) : base(name)
        {
            StudentId = studentId;
        }

        public override void DisplayInfo()
        {
            Console.WriteLine($"[Student] Name: {Name}, ID: {StudentId}");
        }
    }

    class Employee : Person
    {
        public double Salary { get; set; }

        public Employee(string name, double salary) : base(name)
        {
            Salary = salary;
        }

        public override void DisplayInfo()
        {
            Console.WriteLine($"[Employee] Name: {Name}, Salary: {Salary}");
        }
    }

    class Teacher : Person
    {
        public string CourseName { get; set; }

        public Teacher(string name, string courseName) : base(name)
        {
            CourseName = courseName;
        }

        public override void DisplayInfo()
        {
            Console.WriteLine($"[Teacher] Name: {Name}, Course: {CourseName}");
        }
    }

    class Program
    {
        
        public static void ShowPersonInfo(Person p)
        {
            p.DisplayInfo();
        }

        static void Main(string[] args)
       {
            
            List<Person> members = new List<Person>()
            {
                new Student("Ali", 101),
                new Employee("Ahmad", 4000),
                new Teacher( "Dr.Khaled", "C# Programming")
            };

            
           
            foreach (Person person in members)
            {
                Console.WriteLine($"Runtime Type: {person.GetType().Name}");
                person.DisplayInfo();
                Console.WriteLine("---------------------------------------");
            }

           
            
            Person tempStudent = new Student("Sara", 202);
            ShowPersonInfo(tempStudent);

            Console.ReadLine();
        }
    }
}# University-Members