# csGPIO

Raspberry Pi GPIO Library for dotnet core 2.1

It also includes an emulator for your convenience. This emulator allows you to develop GPIO related applications on non-pi systems as it emulates the basic functions of an RPi. 

The emulator emulates: 
  - GPIO/BCM pin naming schemes
  - OUTPUT / INPUT pin modes
  - Edge detects. You can specify ANY Edge Detect mode, but it will translate to either HIGH or LOW in the emu.
  - SYST_CLK 
  
Blinking LED example:
<code>
  using System;
  using csGPIO;
  
  namespace TestClient
  {
    class Program
    {
      GPIO gpio = GPIOManager.GetGPIO();
      gpio.SetMode(GPIO.PinNumberingScheme.BCM);
      gpio.Setup(4, GPIO.PinMode.OUT);
      
      while( true ) {
        gpio.Write(4, GPIO.PinLevel.HIGH);
        Thread.Sleep(1000);
        gpio.Write(4, GPIO.PinLevel.LOW);
        Thread.Sleep(500);
      }
      
      gpio.Shutdown();
    }
  }
</code>
