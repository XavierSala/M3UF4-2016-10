Introducció
--------------------

### La classe URL

El JDK de Java proporciona una classe anomenada URL que es fa servir per representar i manipular adreces en forma de Uniform Resource Identifiers:

	 	 http://www.iescendrassos.net/index.html


URL disposa de diferents constructors però bàsicament consisteix en que l'objecte es crea a partir d'alguna forma de representar la URL...


    URL web = new URL(“http://www.iescendrassos.net”);


Es poden recuperar dades de un objecte URL a partir de dos mètodes:


* openStream()
* openConnection()
* getContent()

Obtenir un stream directament
------------------------------

Un cop tenim una URL es pot obtenir un Stream per recuperar-ne les dades de la mateixa forma que es faria amb qualsevol altra font de dades. El mètode se n'encarrega de fer tot el necessari entre client i servidor fins que obté el flux de dades.

S'obté un InputStream que es pot usar de la mateixa forma que es fa servir en altres fonts de dades

    InputStream stream = web.openStream();

Amb aquest mètode només s'obté el contingut de la URL però no hi haurà res relacionat amb el protocol de transmissió (com per exemple les capçaleres HTTP)

Fer servir URLConnection
-------------------------------

El mètode openConnection retorna un objecte URLConnection que representa una connexió oberta amb un recurs de xarxa. De la mateixa forma que URL aquest objecte també permet obtenir un flux de dades amb la funció getInputStream() que podrem llegir de la forma habitual

    URL web = new URL(“http://www.iescendrassos.net”);

    URLConnection con = web.openConnection();
    InputStream in = con.getInputStream()
    ...

La diferència està en que a un URLConnection permet més control en la connexió amb el servidor: se li poden passar paràmetres extres per la connexió (afegir capçaleres, etc...) es poden obtenir dades del protocol, enviar dades al servidor (POST per exemple)..

Té un descendent molt usat que és HttpURLConnection que es fa servir per fer connexions específiques en HTTP

Activitat
-----------------------------------
En el servidor web que fa falta per fer aquesta tasca el podeu descarregar [des d’aquí](https://drive.google.com/file/d/0B1USLpQ7TipGUFNSSTB3aWRTemc/view?usp=sharing). Podeu executar-lo en local amb Java:

    $ java -jar Lluitadors.jar

Podeu accedir a la web amb [http://localhost:8080](http://localhost:8080) o [http://localhost:8080/Lluitadors](http://localhost:8080/Lluitadors)

En la web hi trobareu les URL que us faran falta per treballar.

L'aplicació emmagatzema les dades a memòria de manera que cada vegada que l’executeu hi haurà dades diferents.

### Campionat del món de Lluitadors

En el servidor hi ha les dades del campionat de Lluita conegut com el “Campionat del món de lluitadors!”.

En aquests tipus de combats s’enfronten dos lluitadors sense seguir cap norma fins que un dels dos es rendeix.

![Baralla](imatges/baralla.png)

Com que volen que els combats siguin el màxim de justos, des del dia en que s'inscriuen,  als lluitadors ja no els deixen entrenar més i només els donen bledes per menjar per evitar que se’ls hi incrementi la força (haurien d’haver entrenat abans d’apuntar-se!)

Un apostador us ha contractat perquè li feu un programa que li permeti fer apostes segures:

* El programa ha de calcular quin dels lluitadors és el més fort (el que guanya a tots els altres)
