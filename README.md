# citac
## Zapojení digitálního čítače na lis a vyřešení chybného čítání

Tato kapitola popisuje instalaci digitálního čítače cyklů na mechanický lis pro evidenci počtu vyrobených kusů a následné řešení technického problému s duplicitním čítáním a úpravou elektrického obvodu.

### Zapojení napěťového snímače
Pro detekci jednotlivých zdvihů lisu byl instalován aktivní napěťový snímač, který při průchodu beranu lisu v horní úvrati generuje napěťový pulz. 
* **Původní zapojení:** Signálový výstup ze snímače byl přímo zaveden do vstupní svorky digitálního čítače. Očekávalo se, že čítač bude čistě reagovat na hranu napěťového pulzu.

### Problém se sčítáním po dvou a indukce v obvodu
Po spuštění lisu čítač při jednom zdvihu přičítal **dva cykly místo jednoho**. Vzhledem k tomu, že šlo o napěťový snímač, byla příčina čistě elektrická:
* **Indukované napětí a plovoucí potenciál:** Při rozpojení nebo návratu snímače zůstávalo na dlouhém signálovém vodiči indukované zbytkové napětí (kapacita kabelu), nebo docházelo k zakmitávání napěťové úrovně. Čítač toto postupné klesání napětí vyhodnotil jako další samostatný pulz (falešné sepnutí na sestupné hraně).

### Vyřešení problému a úprava zapojení v obvodu
Chyba byla odstraněna hardwarovou úpravou zapojení přímo v elektrickém obvodu čítače:
* **Přidání zatěžovacího odporu (Pull-down):** Do obvodu mezi signálový vstup čítače a záporný pól napájení (0 V / GND) byl zapojen rezistor. Tento odpor spolehlivě stahuje plovoucí napětí na vodiči k nule v momentě, kdy snímač není aktivní. Tím se obvod stabilizoval a eliminovalo se indukované rušení.
* **Úprava polohy snímače:** Snímač byl zároveň mechanicky doladěn tak, aby napěťový impuls vznikal až v prokazatelné koncové pozici bez vlivu mechanických vibrací lisu.

Po této úpravě elektrického zapojení začal systém fungovat stoprocentně a čítač spolehlivě připisuje přesně jeden cyklus na jeden zdvih lisu.
