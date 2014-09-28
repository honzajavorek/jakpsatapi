# Životní cyklus návrhu

API jsou software a tudíž pro ně platí i základní poučky softwarového inženýrství. Bohužel se na to často zapomíná a proces vývoje API připomíná [vodopád](https://cs.wikipedia.org/wiki/Vodop%C3%A1dov%C3%BD_model). Vzniklé problémy jsou potom o to horší, že API stojí často na hranici mezi skupinami vývojářů se zcela odlišnými očekáváními.

## Problém jménem vodopád

"Potřebujeme API." Možná jste tuto větu slyšeli, možná jste ji dokonce sami vyslovili. Tímto většinou všechno začíná. Ale co dál?

Většinou to vypadá tak, že se nahrubo načrtne, jak by mohlo API vypadat a co by mělo obsahovat, potom se začne programovat a pak se už hotové představí druhé straně - tvůrcům klientů.

*Tady by se hodil obrázek tunelářů, kteří tunelovali z obou stran a o pár metrů se minuli. Možná ho někdy nakreslím.*

A v tento okamžik vyplave na povrch spousta problémů. Zjistíte, že jste vlastně podle konzumentů vašeho API vytvořili něco úplně jiného, než si představovali oni. Vy jste přes API otevřeli své ORM modely a namapovali hezky POST-GET-PUT-DELETE na [CREATE-READ-UPDATE-DELETE](https://cs.wikipedia.org/wiki/CRUD), ale najednou zjistíte, že vývojář vaší mobilní aplikace to tak nějak vůbec nedokáže ocenit a spílá vám za to, že musí udělat 130 požadavků jen proto, aby dokázal uživateli sestavit úvodní stránku.

Ke svému API jste ex post sepsali dokumentaci, kterou ale v čase nejste schopni udržet aktuální a to uvádí protistranu do ještě větší bezmoci. Pokud jste ji vygenerovali z kódu, jste na tom jen o něco lépe.

Co je špatně? Středobodem návrhu vašeho API je programový kód. Kód je ale strašně špatné místo k iteraci nebo diskusi. Nejen že jste podobu svého API nekonzultovali s cílovou skupinou - vy jste vlastně ani nemohli. Uvěznili jste se do [vodopádu](https://cs.wikipedia.org/wiki/Vodop%C3%A1dov%C3%BD_model).

## Řešení? Iterativní cyklus na úrovni návrhu

Pokud chcete se svým API uspět, přejděte na interativní model návrhu a vývoje.

Navrhujte *documentation first* - sepište nejdříve dokumentaci k API, ukažte ji vývojářům klientů a konzultujte s nimi, co by se mělo udělat jinak. Pomohou vám v orientaci na *use cases*, tedy reálné případy použití, místo abyste do API kopírovali strukturu vaší databáze.

Vytvářejte prototypy, které si budou moci tvůrci klientů ihned vyzkoušet. Dopomůže to k ještě kvalitnější zpětné vazbě a propracovanějšímu návrhu. Iterujte nad dokumentací a prototypy, dokud nebudou s návrhem spokojeny obě strany ještě před tím, než spálíte stovky člověkohodin na samotné tvorbě API.

A až budete mít API hotové a bude v provozu, testujte jej a sledujte jaké chyby jeho uživatelé dělají. Budete jim moci poskytnout kvalitnější podporu a budete schopni upravit dokumentaci nebo návrh tak, aby se konzumenti vašeho API mohli chyb třeba úplně vyvarovat.

## API Blueprint

[Apiary](http://apiary.io/), kde pracuji, poskytuje nástroje pro velkou část z nastíněného cyklu. [API Blueprint](http://apiblueprint.org/) je dokumentační formát, v němž můžete popsat celé svoje API pomocí lidsky čitelného i zapisovatelného [Markdownu](http://daringfireball.net/projects/markdown/) (něco jako [Texy!](http://texy.info/), akorát na rozdíl od něj Markdown používá celý svět - [StackOverflow](http://stackoverflow.com/), [GitHub](http://github.com/), a další). V jednom snadno spravovatelném textovém souboru pak máte zakódováno DNA vašeho API. Můžete jej sdílet, verzovat, bavit se nad ním s lidmi.

API Blueprint potom můžete [rozparsovat](https://github.com/apiaryio/snowcrash) na tzv. [AST](https://cs.wikipedia.org/wiki/Syntaktick%C3%BD_strom), což je strojově čitelný popis vašeho API. Nad tímto AST můžete snadno postavit dokumentaci, prototypy, a protože blueprint dobře spolupracuje s [JSON Schema](json-schema.md), můžete nad ním mít i komplexní testy.

Apiary nabízí všechny tyto věci zadarmo a ihned k použití. V online editoru napíšete API Blueprint a po jeho uložení k němu máte okamžitě dokumentaci a *mock server*, kam se mohou klienti dotazovat a kde budou na své požadavky dostávat odpovědi podle blueprintu. Bez toho, aniž byste napsali řádek kódu tak máte k dispozici místo, na kterém si klienti mohou odzkoušet vše, co jste pro své API navrhli. Reálný provoz na prototypu můžete navíc sledovat, přičemž máte u každého požadavku k dispozici i rozdíly od toho, co je nadefinováno v blueprintu, popřípadě verdikt, zda se ve srovnání s dokumentací jedná o validní nebo chybný požadavek. Stejný náhled na provoz je pak k dispozici i u *proxy serveru*, jenž požadavky pouze zaznamenává a potom je přeposílá na vaše existující, produkční API. Pomocí testovacího nástroje [Dredd](https://github.com/apiaryio/dredd) pak můžete oproti blueprintu testovat vaši implementaci, což lze pohodlně [zařadit i do CI procesu](http://blog.apiary.io/2013/10/17/How-to-test-api-with-api-blueprint-and-dredd/).

API Blueprint přitom můžete používat i bez Apiary. Celý jazyk, jeho parser a i většina nástrojů kolem něj jsou Open Source.
