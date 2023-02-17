using System;
using System.Collections.Generic;

namespace Netofife
{
    abstract class User
    {
        protected string jmeno;
        protected string heslo;
        protected int id;
        public User(string Jmeno, string Heslo, int ID)
        {
            jmeno = Jmeno;
            heslo = Heslo;
            id = ID;
        }
        public string GetJmeno()
        {
            return jmeno;
        }
        public void SetJmeno(string Jmeno)
        {
            jmeno = Jmeno;
        }
        public string GetHeslo()
        {
            return heslo;
        }
        public void SetHeslo(string Heslo)
        {
            heslo = Heslo;
        }
        public int GetID()
        {
            return id;
        }
        public void SetID(int ID)
        {
            id = ID;
        }
        public void LogIn()
        {
            Console.WriteLine("Zadejte jméno");
            Console.ReadLine();
            Console.WriteLine("Zadejte heslo");
            Console.ReadLine();
            Console.WriteLine("Úspěšně jste se přihlásli!");
        }
        public void LogOut()
        {
            Console.WriteLine("Byl jste odhlášen");
        }
        public void Vypis()
        {
            Console.WriteLine("Jméno: " + jmeno);
            Console.WriteLine("Heslo: " + heslo);
            Console.WriteLine("ID: " + id);
        }
        public virtual void ZmenaHesla()
        {

        }
    }
    class Admin : User
    {
        public Admin(string Jmeno, string Heslo, int ID) : base(Jmeno, Heslo, ID)
        {
            jmeno = Jmeno;
            heslo = Heslo;
            id = ID;
        }
        public override void ZmenaHesla()
        {
            Console.WriteLine("Zadejte nové heslo");
            heslo = Console.ReadLine();
        }
    }
    class Student : User
    {
        public Student(string Jmeno, string Heslo, int ID) : base(Jmeno, Heslo, ID)
        {
            jmeno = Jmeno;
            heslo = Heslo;
            id = ID;
        }
        public override void ZmenaHesla()
        {
            Console.WriteLine("Zadejte staré heslo");
            while(heslo != Console.ReadLine())
            {
                Console.WriteLine("Špatné heslo");
            }
            Console.WriteLine("Zadejte znova staré heslo");
            while (heslo != Console.ReadLine())
            {
                Console.WriteLine("Špatné heslo");
            }
            Console.WriteLine("Zadejte nové heslo");
            heslo = Console.ReadLine();
        }
    }
    class Teacher : User
    {
        public Teacher(string Jmeno, string Heslo, int ID) : base(Jmeno, Heslo, ID)
        {
            jmeno = Jmeno;
            heslo = Heslo;
            id = ID;
        }
        public override void ZmenaHesla()
        {
            Console.WriteLine("Zadejte své ID");
            while (id != int.Parse(Console.ReadLine()))
            {
                Console.WriteLine("Špatné ID");
            }
            Console.WriteLine("Zadejte staré heslo");
            while (heslo != Console.ReadLine())
            {
                Console.WriteLine("Špatné heslo");
            }
            Console.WriteLine("Zadejte nové heslo");
            heslo = Console.ReadLine();
        }
    }
    class Program
    {
        static void Main(string[] args)
        {
            List<User> Uzivatel = new List<User>();

            Admin admin1 = new Admin("Karel", "123", 1);
            Admin admin2 = new Admin("Karel", "123", 2);
            Admin admin3 = new Admin("Karel", "123", 3);

            Student student1 = new Student("Dominik", "456", 4);
            Student student2 = new Student("Dominik", "456", 5);
            Student student3 = new Student("Dominik", "456", 6);

            Teacher teacher1 = new Teacher("Radek", "789", 7);
            Teacher teacher2 = new Teacher("Radek", "789", 8);
            Teacher teacher3 = new Teacher("Radek", "789", 9);

            Uzivatel.Add(admin1);//0
            Uzivatel.Add(admin2);//1
            Uzivatel.Add(admin3);//2
            Uzivatel.Add(student1);//3
            Uzivatel.Add(student2);//4
            Uzivatel.Add(student3);//5
            Uzivatel.Add(teacher1);//6
            Uzivatel.Add(teacher2);//7
            Uzivatel.Add(teacher2);//8

            Uzivatel[0].LogIn();
            Uzivatel[0].LogOut();
            Uzivatel[0].Vypis();
            Uzivatel[0].ZmenaHesla();
            Console.WriteLine(Uzivatel[0].GetHeslo());

            Uzivatel[3].LogIn();
            Uzivatel[3].LogOut();
            Uzivatel[3].Vypis();
            Uzivatel[3].ZmenaHesla();
            Console.WriteLine(Uzivatel[3].GetHeslo());

            Uzivatel[6].LogIn();
            Uzivatel[6].LogOut();
            Uzivatel[6].Vypis();
            Uzivatel[6].ZmenaHesla();
            Console.WriteLine(Uzivatel[6].GetHeslo()); 
        }
    }
}
