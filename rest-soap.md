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

# REST vs. SOAP

[REST](rest.md) a SOAP jsou dvě různé odpovědi na stejnou otázku: Jak komunikovat mezi aplikacemi přes HTTP? (Zanedbám, že jak REST, tak SOAP lze použít i na jiných protokolech - v praxi to nikdo moc nedělá.)

Pocházíte-li ze světa velkých bank a enterprise řešení, s pojmem SOAP jste se určitě už setkali. Jestliže jste student, který se před týdnem naučil [Go](http://golang.org/), nejspíš vůbec nevíte, co si pod tím představit. V tom druhém případě můžete tuto stránku v klidu ignorovat. (Stručně o historii [zde](zaklady.md)).

Protože REST je už popsán [o stránku vedle](rest.md), přeskočme rovnou k vysvětlění SOAP a ke srovnání.

### SOAP

*Simple Object Access Protocol* nakonec moc "simple" vlastně není. Je to standardizovaný protokol založený na XML a vynalezl jej Microsoft jako náhradu za binární formáty, se kterými se přes HTTP pracovalo špatně.

XML, které běhá po síti a do něhož se v SOAP zabalují instrukce mezi službami, je většinou extrémně komplexní a lidsky naprosto nečitelné. Můžete si jej ve svém oblíbeném jazyce skládat nebo číst "ručně", ale většinou to dělat nechcete. Potřebujete knihovnu, která to udělá za vás. Knihovnou jste zpravidla zcela odstíněni od komunikace, takže zmíněné XML nikdy v praxi nezahlédnete.

WSDL (*Web Services Description Language*) je další XML, jež kompletně definuje jak má vaše WS (*Web Service*) fungovat. Pokud takový předpis předhodíte svému všemocnému [IDE](https://cs.wikipedia.org/wiki/V%C3%BDvojov%C3%A9_prost%C5%99ed%C3%AD) a pracujete v nějakém vyvoleném jazyce jako Java nebo .NET, vlastně už ani nemusíte ručně nic dělat. [WSDL](https://cs.wikipedia.org/wiki/Web_Services_Description_Language) je formální kontrakt mezi klientem a serverem.

Paradoxem ekosystému SOAP je skutečnost, že všude používá pojem webová služba, ale ve skutečnosti s webem jako takovým tento protokol nemá ve srovnání s REST nic moc společného.

## Dávno vyhraná bitva

Webová API [vyhrála](http://www.infoq.com/articles/rest-soap). To není moje zbožné přání, to je realita současnosti a fakt. Žádná rozumná firma dnes už na SOAP nevsadí, pokud nemusí. Níže se pokusím sepsat proč, ale předem vás upozorňuji na to, že i kdyby se vám líbil SOAP nevímjak, webová API mají na své straně jeden nezvratný a podstatný argument, který přebije všechno - lidé pro něj našli široké využití, začali jej používat kde to jen jde a SOAP jimi nahrazují.

Zajímá-li vás toto téma do hloubky, přečtěte si knihu [RESTful Web Services](http://shop.oreilly.com/product/9780596529260.do). Najdete tam o dost lepší argumenty, než jaké jsou zde. Je to velice detailní průvodce, který srovnává oba přístupy a pěkně vysvětluje REST. Jak ale napovídá rok vydání oné přelomové knihy, problematika REST vs. SOAP se ve světě řešila kolem roku 2007, tedy sedm let před založením **Jak psát API**.

Považuji tuto bitvu tedy za dávno vyhranou, překonanou a nemám úplně chuť trávit svůj čas psaním či diskutováním na toto téma či průzkumem v této oblasti. To ovšem neznamená, že mi s touto sekcí nemůžete [pomoci](https://github.com/honzajavorek/jakpsatapi#p%C3%ADsmenka), pokud se o tuto problematiku zajímáte. Klidně ji narovnejte do neutrálnější roviny, mě to vadit nebude.

## Krátká odpověď

Pokud nemáte speciální, velice dobrý důvod postavit vaše API jako SOAP, postavte jej jako webové API. Jestliže nevíte jistě, zda je váš důvod dostatečně speciální a dobrý, a přemýšlíte nad tím, tak není.

Když zkusím analogii s hudebními nosiči, představte si, že SOAP je kazeta nebo audio CD, webové API je MP3 a [hypermedia](hypermedia.md) je FLAC. Obaly gramofonových desek nebo booklety kazet a CD pěkně voní, jsou krásné a vyjímají se na poličce, ale světem holt dnes už dávno hýbe pružnější MP3, ne-li dokonce [FLAC](https://cs.wikipedia.org/wiki/Free_Lossless_Audio_Codec). Pokud jste vydavatel hudby, jít do kazety by byla sebevražda. Jestliže jste konzument hudby, chcete MP3 nebo FLAC.

## Dlouhá odpověď

SOAP je neobratný korporátní protokol, který je za zenitem. Webová API na způsob RESTu jsou flexibilní styl, podle něhož se dnes tvoří prakticky všechna nová API (byť je při tom REST jako takový ustavičně mrzačen).

### Standardizace

SOAP je jasně daný a standardizovaný, zatímco REST je jen styl - tedy sada doporučení/omezení. Jak je vysvětleno [zde](zaklady.md), ta omezení většina světa ale vlastně stejně nedodržuje a jako REST je tak označováno vlastně jakékoliv webové API nad HTTP, které není SOAP. REST sám nebo webová API tedy nejsou a nemohou být standardy, ale staví na standardních technologiích (HTTP, URI, SSL, ...).

### Budoucnost

Nová API nad SOAP už příliš nevznikají, využití tohoto protokolu ve světě dožívá. Bude dožívat velice dlouho, protože na něm jedou všechny banky aj. podobně velký byznys (o státních správách nemluvě), ale budoucnost je již jinde. Sám mohu dosvědčit, že i v českých bankách se už začínají sem tam dělat webová API. Vytvářet dnes SOAP API je jako vyvíjet vaši webovou prezentaci v IE6.

### Ekosystém

Pokud píšete Javu, .NET či jiný "vyvolený" jazyk se všemocným IDE, má pro vás SOAP hodně věcí "zadarmo". Je to ale také svět sám pro sebe. Webová API profitují z toho, že běží na stejných principech, jako web. Zkuste si pracovat se SOAP z JavaScriptu. A co třeba AJAX? [Web 2.0](https://cs.wikipedia.org/wiki/Web_2.0) máme od roku 2004. K webovému API lze přistupovat z prohlížeče, příkazové řádky, mobilního zařízení, nebo čehokoliv jiného, co v budoucnu bude mít svou vlastní IP adresu, ať už to bude lednička nebo hodinky.

Webová API **jsou** web a web **je** webové API. Cokoliv co funguje pro web, funguje pro webové API a naopak. Tím, že se snaží maximálně využít vlastnosti HTTP, dělá API srozumitelnější pro kohokoliv, kdo nad HTTP už někdy něco stavěl - což je dnes opravdu velká část vývojářů.

Nevýhodou webových API je, že nástroje kolem nich jsou stále ve vývoji a ekosystém okolo tohoto stylu není tak ustálený nebo pevně standardizovaný jako u SOAP. Sice můžete použít jakýkoliv webový framework v jakémkoliv jazyce a API si relativně snadno postavíte "na koleně", ale brzy zjistíte, že to není úplně ono.

Nicméně toto se zlepšuje - vznikají frameworky, knihovny, nástroje pro dokumentaci, generování kódu, apod. [Hypermedia](hypermedia.md) potom navrhuje univerzální, rozšiřitelné [formáty](hypermedia-formaty.md) odpovědí, které umožňují tvorbu generických klientských knihoven schopných konzumovat jakékoliv hypermedia API. Místo WSDL můžete pro popis API použít např. [API Blueprint](http://apiblueprint.org/) (ač tedy ve WSDL 2.0 lze údajně popsat i REST, nemluvě o WADL).

### Datový vs. procedurální přístup

Webová API jsou orientována datově (nebo by alespoň podle RESTu měla), pracuje s reprezentacemi stavů, ne s instrukcemi co má ten který server udělat (RPC). U webových API se neposílají žádné do XML zabalené objekty, takže nedochází k nedorozumněním mezi různými programovacími jazyky, jako se to občas děje u SOAP. Webová API přímo staví na HTTP, zatímco SOAP přes něj jen posílá zabalené zprávy - nedokáže tak využít plnou sílu (interoperabilitu, univerzálnost) HTTP a je spíš jeho "zneužitím".

Pro přenos dat můžete u webových API použít jakýkoliv formát, který vás napadne. Můžete udělat API, jež bude přímo servírovat vašim klientům CVS, JSON, HTML, XML, [GPX](https://en.wikipedia.org/wiki/GPS_Exchange_Format), SVG, obrázky, zvuk, nebo i klidně všechno uvedené najednou.

### Efektivita, škálovatelnost

Webová API jsou díky svým vlastnostem také efektivní - posílaná data mohou být několikanásobně menší než u SOAP. Tento rozdíl se s použitím komprese jako Gzip stírá, ale např. u mobilních zařízení (nemluvě o [IoT](https://cs.wikipedia.org/wiki/Internet_v%C4%9Bc%C3%AD)), kde se velice šetří zdroji, je toto velkou výhodou webových API. Kdyby měla každá aplikace ve vašem smartphonu parsovat SOAP odpovědmi jako na běžícím páse, zřejmě byste se nedoplatili za data a telefon byste nabíjeli co dvě hodiny (přeháním).

Webová API škálují. Díky pravidlu o bezstavovosti a tomu, že staví na vlastnostech HTTP sloves, lze u REST API kompletně [kešovat](kesovani.md) veškeré čtení.

### Změny v API, "rozvíjitelnost"

Změny v API znamenají u SOAP prakticky okamžité rozbití klienta. "Zadrátování" klienta a serveru je mnohem větší než u webových API. Na jednu stranu nabízí kontrakt určitý pocit bezpečí, ale na druhou zase svazuje API ve vývoji.

I relativně špatně navržené webové API se dokáže poměrně bezbolestně [rozvíjet v čase](verzovani.md). [Správné REST API](hypermedia.md) by mělo navíc poskytnout veškeré informace o tom, jak lze použít, přímo v odpovědích ze serveru a klientovi by měla stačit znalost domény, kde se API nachází. Někteří klienti mohou klidně rozumět jen té části vašeho API, jaká je zajímá, a zbytek ignorovat. SOAP oproti tomu vyžaduje, aby obě strany před jakoukoliv komunkací sdílely naprosto přesnou specifikaci API.

SOAP a webové API, to je něco jako [statická a dynamická typová kontrola](https://cs.wikipedia.org/wiki/Typov%C3%A1_kontrola).

## Přechod od SOAP k REST

Doporučuji onu již výše zmíněnou knihu [RESTful Web Services](http://shop.oreilly.com/product/9780596529260.do). Měla by vás bezbolestně provést celým procesem přechodu. Udělejte hromadnou objednávku a rozdejte ji ve vaší firmě.

## Externí zdroje

### [Ross Mason: How REST replaced SOAP on the Web: What it means to you](http://www.infoq.com/articles/rest-soap)

Rozsáhlý rozbor z roku 2011 o tom, jak webová API (zde označovaná jako REST) ve světě vytlačují SOAP a co to přináší za nové výzvy.

### [Steve Francia: REST vs SOAP, the difference between soap and rest](http://spf13.com/post/soap-vs-rest)

Pokus o shrnutí důvodů proč by někdo mohl chtít použít SOAP. S většinou těch důvodů bych dokázal polemizovat, ale beru to jako seznam toho nejužitečnějšího, co SOAP nabízí.

### [StackOverflow: SOAP vs REST (differences)](https://stackoverflow.com/questions/19884295/soap-vs-rest-differences)

Velká studnice názorů a srovnání obou přístupů k návrhu API.

### [SoapUI API Testing Dojo: SOAP vs. REST Challenges](http://www.soapui.org/The-World-Of-API-Testing/soap-vs-rest-challenges.html)

Poměrně rozsáhlý rozbor na téma SOAP vs. webová API (zde označovaná jako REST), příklady zasílaných dat, podrobný popis i kritika obou přístupů.
