# Information on ports, sockets, compatability, pins, speeds, etc.

- **Is there a difference between “Thunderbolt” and “Mini DisplayPort” cables?**  
Yes, they are different. ***Display Port*** is a passive audio/video technology, ***Thunderbolt*** is active generic data technology. The hardware inside the cable is necessary to get the full data throughput. A ***Display Port*** cable will only carry Video/Audio to an attached monitors*, while a ***Thunderbolt*** cable is able to carry all sorts of other data, which is required for your dock with multiple types of ports.  
Whilst you can get away with connecting one monitor to ***Thunderbolt*** with a **mini-DisplayPort*** cable, that's the end of the chain.  
In order to chain, you must have ***Thunderbolt*** cabling throughout.  
***Thunderbolt*** carries ***Displayport*** 1.1a video, and will not work with some newer monitors, including 4k monitors. One will need at least ***DisplayPort*** 1.2 spec cables to power 4k monitors.  
***Thunderbolt*** also carries data - 4 high-speed PCI-E channels - in addition to ***DisplayPort*** 1.1a.  

  Mini DisplayPort Cable:
  ```
         OUT       |        IN        
  ------------------------------------
  Mini DisplayPort | Mini DisplayPort
  Thunderbolt      | Mini DisplayPort  
```

  Thunderbolt Cable:
  ```
         OUT       |        IN        
  ------------------------------------
  Thunderbolt      | Thunderbolt
```
