# C-LambdaDemo
Practice using Lambda
using System;

namespace LambdaDemo
{
    class Program
    {
        static int myNum = 3,
            myNum2 = 4;

        static Func<int, int, int> minus = (num1, num2) => num1 - num2;

        static void Main(string[] args)
        {
            //lambda format
            // args => expression
            //number => number * number

            //lambda syntax
            // () => ... cod here
            Func<int, int> square = number => number*number;

            Console.WriteLine(square(5));

            Func<double, double, double> SumUp = (d1, d2) => d1 + d2;

            Console.WriteLine(SumUp(1.916854,1.168435168));

            const int factor = 5;

            Func<int, int> multiplier = (num) => num * factor;

            var myInt = multiplier(5);

            Console.WriteLine(myInt);

            var solution = minus(myNum2, myNum);

            Console.WriteLine(solution);

            Func<int, int, int> FindLargestInt = (num1, num2) =>  num1 > num2 ? num1 : num2;

            Console.WriteLine(FindLargestInt(1,2));

            var books = new BookRepo().GetBooks();

            var BooksOverOneDollar = books.FindAll(b => b.Price > 1);

            foreach (var i in BooksOverOneDollar)
            {
                Console.WriteLine($"${i.Price} {i.Title}");
            }

            //will find the first value
            var OneDollarBook = books.Find(b => b.Price == 1);

            Console.WriteLine(OneDollarBook.Title);

            //this will throw up an error b/c there is not 0 dollar book
            //var FreeBook = books.Find(e =>  e.Price == 0);  

            //will return books less than 3 dollars
            var LessThan3DollarsBooks = books.FindAll(b => b.Price < 3);

            foreach (var b in LessThan3DollarsBooks)
            {
                Console.WriteLine($"${b.Price} {b.Title}");
            }

        }

       

    }
}
