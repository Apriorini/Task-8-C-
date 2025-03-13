 double g = 9.81;
Console.WriteLine("Введите положение пушки по Х начальное");
double x0 = Convert.ToDouble(Console.ReadLine());
Console.WriteLine("Введите положение пушки по Y начальное");
double y0 = Convert.ToDouble(Console.ReadLine());
Console.WriteLine("Введите начальную скорость снаряда V0");
double v0 = Convert.ToDouble(Console.ReadLine());
Console.WriteLine("Введите угол a (в градусах)");
int a0 = Convert.ToInt32(Console.ReadLine());
if (x0 < 0 || y0 < 0 || a0 < 0 || a0 > 360)
{
    Console.WriteLine("Данные введены неправильно, попробуйте еще раз");
}
else
{
    double rad = a0 * Math.PI / 180;
    double cosA = Math.Cos(rad);
    double sinA = Math.Sin(rad);
    double Vx0 = v0 * cosA;
    double Vy0 = v0 * sinA;
    double timeStep = 0.1;
    double t = 0;
    Console.WriteLine("Траектория полета снаряда:");
    Console.WriteLine("Время\t\tX\t\tY");
    while (true)
    {
        double x1 = x0 + Vx0 * t;
        double y1 = y0 + Vy0 * t - 0.5 * g * Math.Pow(t, 2);
        if (y1 < 0)
            break;
        Console.WriteLine($"{t:F2} с\t\t{x1:F2} м\t\t{y1:F2} м");
        t += timeStep;
    }
    Console.WriteLine("Снаряд упал на землю.");
}
