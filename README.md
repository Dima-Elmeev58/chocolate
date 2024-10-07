# chocolate
class Program
{
    static void Main()
    {
        // Инициализация параметров
        Console.WriteLine("Введите количество денег: ");
        int money = Convert.ToInt32(Console.ReadLine());

        Console.WriteLine("Введите цену одной шоколадки: ");
        int price = Convert.ToInt32(Console.ReadLine());

        Console.WriteLine("Введите количество оберток для обмена на новую шоколадку: ");
        int wrappersToTrade = Convert.ToInt32(Console.ReadLine());

        // Подсчет максимального количества шоколадок
        int totalChocolates = CalculateMaxChocolates(money, price, wrappersToTrade);

        Console.WriteLine($"Максимально возможное количество шоколадок: {totalChocolates}");
    }

    // Метод для подсчета максимального количества шоколадок
    static int CalculateMaxChocolates(int money, int price, int wrappersToTrade)
    {
        // Первоначальное количество шоколадок
        int chocolates = money / price;
        int wrappers = chocolates;

        // Цикл обмена оберток на шоколадки
        while (wrappers >= wrappersToTrade)
        {
            int newChocolates = wrappers / wrappersToTrade;
            chocolates += newChocolates;
            wrappers = newChocolates + (wrappers % wrappersToTrade);
        }

        return chocolates;
    }
}
