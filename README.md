# Promotion-chess.js-chessboard.js
Se crea una mini popup en el tablero de ajedrez con las opciones necesarias para coronar en tiempo real Reina Torre Alfil o Caballo


Este es un pequeño código en JavaScript utilizando las Apis chess.js y chessboard.js

que permite crear una popup o mini ventana sobre el tablero de ajedrez donde te muestra las opciones al coronar un Peón

puedes seleccionar REINA TORRE ALFIL y CABALLO Esto se logró convirtiendo la notación de ajedrez algebraicas y pasándolas

notaciones antiguas 

Las notaciones algebraicas creadas en chess.js de aplican de la siguiente manera

. gxh8 esto quiere decir que Peón toma torre y corona y la corona se debe especificar
 
. gxh8=Q corona reina

. gxh8=Q+ corona reina, pero el rey queda en jaque el signo más significa jaque cuando haces esta notación debes de ser claro

y preciso con la notación porque si no es así NO funciona

Pero con las notaciones antiguas, si funciona la notación antigua se expresan así 

. g7 h8 Y este tipo de notación es más explícita, pero chess.js lo hace automáticamente

. g7 h8 q Aquí se expresa que el Peón toma torre y corona una reina y no hay que pacificar si el rey está o no en jaque

 La expresión antigua queda así {from:’g7’ to:’h8’ promotion:’q’ }
 
 Entonces teniendo en cuenta esto lo que se hiso fue convertir la notación algebraica y notación antigua. de la siguiente
 
 manera
 
 1 se capturan todos los movimientos en una variable cuando el Peón corona se devuelve ultima jugada con la opción undo 
 
 2 esto activa una función que muestra la popup y almacena todos los movimientos
 
 3 de esa variable que guarda todos los movimientos se saca el último movimiento este esta algebraico 
 
 4 Con otra función se convierte en notación antigua y se la asigna ese movimiento al juego
 
 al seleccionar la pieza de corona que está en la popup ese activa la función que convierte la notación y cierra la popup
 
 logrando así la corona que se desea
 

