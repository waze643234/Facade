```
using System;

namespace FacadeDemo
{
    
    class TV
    {
        public void TurnOn() => Console.WriteLine("Телевізор увімкнено.");
        public void TurnOff() => Console.WriteLine("Телевізор вимкнено.");
    }

    class SoundSystem
    {
        public void SetVolume(int level) => Console.WriteLine($"Гучність звуку встановлено на {level}%.");
    }

    class Lights
    {
        public void Dim() => Console.WriteLine("Світло приглушено.");
        public void Brighten() => Console.WriteLine("Світло увімкнено на повну.");
    }

    
    class HomeTheaterFacade
    {
        private TV _tv = new TV();
        private SoundSystem _sound = new SoundSystem();
        private Lights _lights = new Lights();

        
        public void WatchMovie()
        {
            Console.WriteLine("--- Підготовка до перегляду фільму ---");
            _lights.Dim();
            _tv.TurnOn();
            _sound.SetVolume(70);
            Console.WriteLine("Фільм запущено!\n");
        }

        public void EndMovie()
        {
            Console.WriteLine("--- Завершення перегляду ---");
            _tv.TurnOff();
            _lights.Brighten();
        }
    }

    class Program
    {
        static void Main()
        {
            
            HomeTheaterFacade theater = new HomeTheaterFacade();
            theater.WatchMovie();
            theater.EndMovie();
        }
    }
}
