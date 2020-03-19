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

# Nástroje a knihovny pro Python

Nedělám si iluze, že by byl tento seznam vyčerpávající. Pokud najdete zajímavý projekt zaměřený na API, [dejte mi o něm prosím vědět](https://github.com/honzajavorek/jakpsatapi#p%C3%ADsmenka).

## Webové frameworky

Protože REST API je založeno na těchtýž principech jako web, můžete klidně použít pro jeho tvorbu klasické webové frameworky. Sem tam vám akorát budou překážet "vhodná výchozí nastavení", jelikož tyto frameworky obvykle nepočítají s tím, že chcete 404 stránku poslat jako JSON apod.

- [Django](https://github.com/django/django) - nejrozšířenější, monolit, všechno (pro tvorbu webu, ne API) si táhne s sebou
- [Flask](https://github.com/mitsuhiko/flask) - mikrojádro, na které se nalepují potřebné doplňky
- [Falcon](https://github.com/racker/falcon) - zajímavý, rychlý framework s pěkným explicitním rozhraním, přímo dělaný pro API
- [Pylons/Pyramid](http://www.pylonsproject.org/) - vybaveností něco mezi Djangem a Flaskem
- [Bottle](https://github.com/defnull/bottle) - úplně minimalistický, vhodný tak možná na školní příklady nebo jednostránkové weby

## API frameworky nebo rozšíření

- [Django REST Framework](https://github.com/tomchristie/django-rest-framework) - spolu s Tastypie jeden z dvou hlavních pro Django
- [Tastypie](https://github.com/toastdriven/django-tastypie) - spolu s DRF jeden z dvou hlavních pro Django
- [Eve](https://github.com/nicolaiarocci/eve) - bohatě vybavená API obálka nad MongoDB, postaveno jako samostatný projekt nad jádrem Flasku
- [Flask-RESTful](https://github.com/twilio/flask-restful) - nejspíš nejpoužívanější pro Flask
- [Flask-RESTless](https://github.com/jfinkels/flask-restless) - nad SQL modely (SQLAlchemy)
- [Flask-MongoREST](https://github.com/elasticsales/flask-mongorest) - nad MongoDB

## Samostatné knihovny

- [Negotiator](https://github.com/CottageLabs/negotiator) - content negotiation
- [Dougrain](https://github.com/wharris/dougrain/) - HAL
- [Hypermedia Resource](https://github.com/the-hypermedia-project/hypermedia-resource-python/) - pokus o obecného hypermedia klienta
- [JSON Schema](https://github.com/Julian/jsonschema)
