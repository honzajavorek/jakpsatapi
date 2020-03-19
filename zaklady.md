<table>
    <tr>
        <th>⚠️</th>
        <td>
            <strong>Jak psát API</strong> jsem nikdy pořádně nezačal ani nedokončil. Co jsem napsal, to tady je. Nové texty nepřidávám, staré neudržuji, ale třeba se to bude i tak někomu hodit.
        </td>
    </tr>
    <tr>
        <th>📖</th>
        <td>
            Raději mrkni na můj nový projekt, <strong><a href="https://cojeapi.cz/">Co je API</a></strong>, což je polopatický úvod do API pro začátečníky.
        </td>
    </tr>
    <tr>
        <th>🐣</th>
        <td>
            Na <strong><a href="https://junior.guru/">junior.guru</a></strong> lidem ukazuji jak se mohou z nuly naučit programovat a najít si svou první práci v IT.
        </td>
    </tr>
</table>

# Základy

## Terminologie

V rámci API se pracuje s mnoha pojmy. Pokusím se některé z nich vysvětlit:

- **RPC:** Protokol, pomocí něhož lze provádět "vzdálené volání procedur". Řekneme serveru co má udělat, zabalíme to do obálky, pošleme. On si to rozbalí, udělá co je třeba, zabalí odpověď a pošle zpět. ([wiki](https://cs.wikipedia.org/wiki/Remote_procedure_call))
- **SOAP:** Nástupce XML-RPC. Všechno je ale o dost robustnější, zaobálkovanější. ([wiki](https://cs.wikipedia.org/wiki/SOAP))
- **Webová služba, Web Service:** Souhrnný název pro API postavená nad XML/RPC/SOAP technologiemi. Často zkracováno na WS. ([wiki](https://cs.wikipedia.org/wiki/Webov%C3%A1_slu%C5%BEba))

Jistý R. Fielding se ve [své dizertační práci](https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm) snažil popsat principy, na jakých úspěšně funguje web. Vzniklo z toho několik omezení/doporučení pro (webové) aplikace, kterým se říká REST. Mnoha lidem se REST zalíbil jako předloha pro API a utekli k němu od SOAP. ([wiki](https://cs.wikipedia.org/wiki/Representational_State_Transfer))

- **Webová API, Web APIs:** Souhrnný název pro API postavená nad webovými technologiemi, především protokoly HTTP/HTTPS.
- **REST:** Správně je to takové API, které dodržuje principy REST. V bitvě proti SOAPu se ale tento termín začal používat v podstatě pro jakékoliv "posílání JSONu přes HTTP". REST API se tedy dnes pro většinu lidí shoduje s pojmem webové API.
- **Hypermedia, HATEOAS:** API, které *doopravdy* dodržuje principy REST. Tento termín se uchytil mezi odborníky po tom, co zjistili, že pojem REST API je nejspíš nenávratně ztracen. Používá se pro odlišení od obecných webových API. ([wiki](https://en.wikipedia.org/wiki/Hypermedia)) Zkratka HATEOAS znamená *Hypermedia as the Engine of Application State*, což je přesně ten princip původního RESTu, na který se potom tak nějak zapomnělo. ([wiki](https://en.wikipedia.org/wiki/HATEOAS))



