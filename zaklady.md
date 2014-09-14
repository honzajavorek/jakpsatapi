# Základy

## Terminologie

V rámci API se pracuje s mnoha pojmy. Pokusím se některé z nich vysvětlit:

- **RPC:** Protokol, pomocí něhož lze provádět "vzdálené volání procedur". Řekneme serveru co má udělat, zabalíme to do obálky, pošleme. On si to rozbalí, udělá co je třeba, zabalí odpověď a pošle zpět. ([wiki](https://cs.wikipedia.org/wiki/Remote_procedure_call))
- **SOAP:** Nástupce XML-RPC. Všechno je ale o dost robustnější, zaobálkovanější. ([wiki](https://cs.wikipedia.org/wiki/SOAP))

Jistý R. Fielding se ve [své dizertační práci](https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm) snažil popsat principy, na jakých úspěšně funguje web. Vzniklo z toho několik omezení/doporučení pro (webové) aplikace, kterým se říká REST. Mnoha lidem se REST zalíbil jako předloha pro API a utekli k němu od SOAP. ([wiki](https://cs.wikipedia.org/wiki/Representational_State_Transfer))

- **Webová API:** Souhrnný název pro API postavená nad webovými technologiemi, především protokoly HTTP/HTTPS.
- **REST:** Správně je to takové API, které dodržuje principy REST. V bitvě proti SOAPu se ale tento termín začal používat v podstatě pro jakékoliv "posílání JSONu přes HTTP". REST API se tedy dnes pro většinu lidí shoduje s pojmem webové API.
- **Hypermedia:** API, které *doopravdy* dodržuje principy REST. Tento termín se uchytil mezi odborníky po tom, co zjistili, že pojem REST API je nejspíš nenávratně ztracen. Používá se pro odlišení od obecných webových API.



