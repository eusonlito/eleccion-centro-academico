## Automatización da selección de centros

ORDE do 2 de xuño de 2016 pola que se ditan normas para a adxudicación de destino provisional para o curso académico 2016/17, entre o persoal docente pertencente aos corpos de catedráticos e profesores de ensino secundario, profesores técnicos de formación profesional, catedráticos e profesores de escolas oficiais de idiomas, profesores de música e artes escénicas, catedráticos e profesores e mestres de taller de artes plásticas e deseño, que non teñan destino definitivo na Comunidade Autónoma de Galicia; aos que resultan desprazados por falta de horario, ao persoal a quen se lle conceda unha comisión de servizos por concelleira ou concelleiro, por motivos de saúde ou por conciliación familiar; ao persoal interino e substituto e ao persoal funcionario de carreira que solicite o reingreso no servizo activo.

http://www.xunta.gal/dog/Publicados/2016/20160620/AnuncioG0164-070616-0004_gl.html

## USO

* Descargar o documento de LibreOffice [centros.ods](https://rawgit.com/eusonlito/eleccion-centro-academico/master/2016/secundaria/centros.ods)
* Cubrir os centros desexados na segunda folla de `Escollidos`, columna de `Escollido`
* O resto dos campos xa se cubren de xeito automático
 * O campo de orde cúbrese según se vaian engadindo códigos
 * Si seleccionamos un código de centro, cubrirá os datos completos
 * Si seleccionamos un código de localidade, cubrirá só os datos da localidade

## APLICACIÓN

Para poder despois usar estes códigos no portal da Xunta ( https://www.edu.xunta.es/cadp/prv/PeticionsIn.do ) debemos realizar os seguintes pasos:

* Copiamos toda a columa de códigos seleccionados e pegámolos na caixa de texto da esquerda en http://delim.co/
* Pulsamos a flecha que sinala para a dereita
* Agora creará un novo texto cos mesmos códigos, pero en vez de un en cada liña, todos en liña separados por comas
* Copiamos ese listado de códigos
* Abrimos o arquivo [javascript.html](https://rawgit.com/eusonlito/eleccion-centro-academico/master/2016/secundaria/javascript.html) en calquera navegador
* Donde pon `// AQUI VAI O LISTADO DE CODIGOS ESCOLLIDOS SEPARADOS POR COMAS`, borramos eso e nesa liña pegamos os códigos, quedando algo como:

```js
var ids = Array.from(new Set([
    15000338,15001070,15001136,15001148,15001239
]));

var $centro = $('input[name="cenloc"]');
var $enviar = $('input[name="DIALOG-EVENT-aplicarCambio"]');

$.each(ids, function(i, id) {
    $centro.attr('value', id);
    aplicarCambio();
});
```

* Hai que fixarse que o listado non acabe en coma
* Agora copiamos o contido dese cadro de texto
* Abrimos a web da Xunta con Google Chrome ( https://www.edu.xunta.es/cadp/prv/PeticionsIn.do ) e vamos á sección donde se engaden os centros ("Peticións")
* Escollemos o `Corpo de participación`, `Especialidade`, `Línguas`, `Afín`, `Itinerante` e a opción de `debe engadirse ao final da lista`
* Debemos ter o listado de selección actualmente baleiro, se xa hai algúns escollidos debemos borralos para evitar problemas
* Agora pulsamos a tecla `F12` e abrirase un apartado no navegador que pon `Consola`
* Pegamos o código anterior aquí e dámoslle a Intro
* Se todo foi ben, veremos todos os centros no listado. Revisamos e gardamos
* Se non foi ben de todo, non hai problema ningún, recargamos a páxina e repetimos o proceso
