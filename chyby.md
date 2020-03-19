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

# Chyby

Pokud při tvorbě odpovědi server zjistí nějakou chybu, měl by odpovědět:

- správným chybovým HTTP kódem
- nejlépe ve formátu, který klient očekává

## Status kód HTTP odpovědi

V zásadě platí pravidlo, že [kódy](https://cs.wikipedia.org/wiki/Stavov%C3%A9_k%C3%B3dy_HTTP) začínající na čtyřku říkají klientovi "něco jsi pokazil, naprav to a požadavek ti vyjde", kdežto kódy začínající na pětku si nesou sdělení "něco je špatně na naší straně, nic s tím neuděláš, omlouváme se". Nejobecnější chybou na straně klienta je 400, na serveru potom 500.

Pokud tedy klient odešle údaje k založení nového inzerátu na auto a na straně API zjistíme, že špatně vyplnil rok výroby a barva karoserie zcela chybí, vrátíme mu ideálně kód 400 a odpověď, v níž bude výčet všech (!) problémů, jež nevedly k úspěšnému přijetí požadavku.

Některé chyby ale mají své vlastní, specifičtější kódy. Měli bychom je použít vždy, když to jde. Pokud si nejsme jisti, najdeme na internetu (třeba na [StackOverflow](https://www.stackoverflow.com)) odpovídající diskuse a zkusíme si udělat nějaký názor, co by asi tak bylo nejlepší. Tento názor pak dodržujeme v celém našem API.

Chybové kódy bychom neměli používat, pokud k chybě nedošlo, a naopak bychom neměli sáhnout po dvoustovkách (úspěch) nebo třístovkách (přesměrování), jestliže k nějaké chybě došlo.

## Formát HTTP odpovědi

Chybový formát může být teoreticky klidně HTML, ale v praxi to moc užitečné není. Lepší je, pokud server odpoví něčím, co je blízké formátu, v jakém klient očekává odpověď (XML, JSON, nebo klidně v obou, budeme-li respektovat `Accept` hlavičky a [content negotiation](content-negotiation.md)). Ať už je to ale cokoliv, měl by být onen formát zdokumentován spolu se zbytkem API.

## Chybové zprávy a kódy

Součástí odpovědi by měl být ideálně nějaký popis chyby. Pokud očekáváme, že klient bude s chybou dále pracovat a vytvářet z ní např. chybové hlášení pro běžného uživatele, je záhodno zahrnout i chybové kódy a v dokumentaci API mít seznam těchto kódů. Pozor, tady mluvíme o kódech v rámci HTTP odpovědi na detailní rozlišení jednotlivých chyb, ne o HTTP kódech!

## Internacionalizace

Chybové kódy usnadňují i překládání chyb na straně klienta. Jiným způsobem, jak lze překládání částečně řešit, je [content negotiation](content-negotiation.md) a hlavičky `Accept-Language`, ale kódy jsou lepší v tom, že klient si může s chybami dělat zcela co uzná za vhodné a není odkázaný na strukturu chyb a překlady přicházející z API serveru.

## Externí zdroje

### [Jørn Wildt:  Error handling considerations and best practices](http://soabits.blogspot.cz/2013/05/error-handling-considerations-and-best.html)

Pěkný rozbor na téma chyb ve webových API. Analýza současných API a různá doporučení, jak by měly chybové odpovědi ideálně vypadat.

### [vnd.error](https://github.com/blongden/vnd.error)

Návrh na obecný formát pro reprezentaci chyb ve webových API. Podporuje JSON i XML.
