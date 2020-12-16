# Open Closed Principle
Sebagai gambaran yang jelas tentang apa yang di maksud dengan OCP. Setiap entitas software, baik itu (Class, module, fungsi) terbuka untuk perluasan, namun tertutup untuk modifikasi.

# Purpose
Open-Closed Principle : Open for extention, closed for modification. Terbuka untuk perluasan, tertutup untuk modifikasi. Dengan tertutupnya code yang sudah ada dari modifikasi maka kemungkinan terjadinya gelombang bug karena kita melakukan suatu perubahan terhadap code yang sudah ada pun dapat dihindari.
# About Program
- Pada Source Code ini terdapat 2 program, yakni CouponWithOCP dan CouponWithoutOCP.
- Pada bagian Coupon With OCP, karena menggunakan Abstraction kita dapat mengubah object menjadi object lain tanpa harus meninggalkan fungsi sesungguhnya.
- Sedangkan pada bagian CouponWithoutOCP, jika kalian mengubah salah satu fungsi maka akan memengaruhi fungsi lain.
- Program ini berjalan pada console, sehingga jalankan dengan Run Without Debug.
# COUPON WITHOUTOCP
- Class Coupon
```csharp
    {
        public double discNominal = 0;
        public double priceNett(double originPrice)
        {
            double net = 0;
            net = (100 - discPercentage) * originPrice / 100;
            return net;
        }
    }
```
- Class Program
```cshrap
{
      static void Main(string[] args)
      {


          Coupon coupon1 = new Coupon();
          coupon1.discNominal = 2000;
          Console.WriteLine(coupon1.priceNett(10000));
      }
  }
```
# COUPON WITHOCP
- Class Coupon.cs
```cshrap
public abstract class Coupon
  {
      public abstract double calculate(double originPrice);
  }
```
- Class CouponWithNominal.cs
```csharp
class CouponWithNominal : Coupon
    {
        public double discNominal;

        public CouponWithNominal(double discNominal)
        {
            this.discNominal = discNominal;
        }

        public override double calculate(double originPrice)
        {
            return originPrice - discNominal;
        }
    }
```
- Class Program.cs
```csharp
class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
            Coupon coupon1 = new CouponWithNominal(2000);
            Console.WriteLine(coupon1.calculate(10000));
        }
    }
```
*MUHAMMAD RIZKO MUNZAL
*19.11.2847
*19-IF-04
