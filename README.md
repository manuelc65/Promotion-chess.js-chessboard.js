https://github.com/manuelc65/Promotion-chess.js-chessboard.js/blob/master/promo1.png
**********************************************************************************************************************************
https://github.com/manuelc65/Promotion-chess.js-chessboard.js/blob/master/promo2.png


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
 
Este es el primer script pagina index 
## Ejemplo
```js
/////////////////////////////////////////////////////////////	 
  function promo (){	                                      //   
	       um = document.getElementById('promote').value;     //   
		   bf = um.toUpperCase();                                // 	
/////////////////////////////////////////////////////////////  
	       nc = a.pop();                                      //   
		   tr = nc.split('');                                    //   
		   jp = tr.pop();                                        //   
		   md = tr.join('');                                     //   
		   ct = md + bf;                                         //   	  
	       game.move(ct);                                     //
	       board.position(game.fen());                        //    
		   $("#coronar").hide();                                 //   
	  }                                                       //   
 ////////////////////////////////////////////////////////////  

```
Este es el segundo script pagina index2 no hay combios de funcionamiento solo se mejora el diseño de popup mas
amigable para la selecion de la pieza a coronar
```js
/////////////////////////////////////////////////////////////	 
   function promo (){	  
	       um = document.getElementById('promote').value;     
		   bf = um.toUpperCase();		
	  
	       nc = a.pop();
		   tr = nc.split('');
		   jp = tr.pop();
		   md = tr.join('');
		   ct = md + bf;	  
	       game.move(ct);
	       board.position(game.fen());
		   $("#coronar").hide();
		   pws();
		   pbs();
	  }
 ////////////////////////////////////////////////////////////  
```
Este es el tercer script de la pagina  index3 a se traja de cofigurar el problema con la corona si hay o no jaque 
funciona todo bien solo si caronas jaque con alfil o con caballo No funciona 
```js
function promo(){	  // aqui  en esta funcion se captura la piese que se quiere coronar q, r, n, b
	       um = document.getElementById('promote').value; 
		   bf = um.toUpperCase();	// esta se cambia a mayuscula pa piesa que se quiere coronar	
	  
	       nc = a.pop();  // aqui se catura el ultimo movimiento 
    nu = nc.length; // se cuentan la letras del ultimo movimiento so corona co jake 7 y si jake 6 
	  if (nu === 7){  // por que ala funcion jake le agrgasn un '+'			    
			     tr = nc.substring(0, nc.length-3);
				 ct = tr + '=' + bf + '+';								
			alert(ct + ' -a')
             }
			 if (nu === 6){      			    
			     tr = nc.substring(0, nc.length-2);			 
				 ct = tr + bf ;
				alert(ct + ' -b')  		
      } 
			 if (nu === 5){   // por que ala funcion jake le agrgasn un '+'			    
			     tr = nc.substring(0, nc.length-2);			 
				 ct =   tr + bf + '+' ; 
				 alert(ct + ' -c')		
             }   
			 if (nu === 4){   // por que ala funcion jake le agrgasn un '+'			    
			     tr = nc.substring(0, nc.length-1);			 
				 ct =   tr + bf  ; 
				 alert(ct + ' -d')		
             } 
//alert(nu)

		   game.move(ct); // aqui  ejecuto el movimiento es decir aqui le digo que piesa coronar
	       board.position(game.fen()); // esto opcio es muy importante si no la agregas no se mueve pa piesa 
		   $("#coronar").hide();// esta hace que al terminar la seleccion de la piesa la popu se oculte  
		   pws(); // esta funcio hace vible las piesas blancas de la popup  solo muestra una por que la optra la oculta pwh 
		   pbs();   //esta funcio hace vible las piesas negras  de la popu 
		   c1.innerHTML = nc + ' el ultimo valor de promotion';
		   c2.innerHTML = ct + ' el valor que se cambio';
		   //c3.innerHTML = nc;						
 } 	       


```

Este es el cuarto script pagina index4 a qui se resuebe el problema y la corona se realiza con exito lo malo es que el codigo se estendio por que hay que hacer esto mismo para la corona con las negras 
```js
//////////////////////////////////////////////////////////////////////////////////////////////////	
	function mover(){    // se combierte la notacion algebraica a antigua de la blancas 
		nu = a.pop();
		tp = nu.length;
		if (tp === 7){
			ab = nu.substring(2, nu.length -3); //= h8
			cd = nu.substring(0, nu.length -6); //= g
			ef = nu.substring(3, nu.length -3);// =8			                                  
			res = ef - 1;                       //= 7
			a_from = cd + res;
			b_to = ab;
			c_promotion = document.getElementById('promote').value;			 
			}else{if (tp === 5){
			ab = nu.substring(0, nu.length -3); //= g8
			cd = nu.substring(0, nu.length -4); //= g
			ef = nu.substring(1, nu.length -3);// =8			                                  
			res = ef - 1;                       //= 7
			a_from = cd + res;
			b_to = ab;
			c_promotion = document.getElementById('promote').value;			 
			}else{if (tp === 6){
			ab = nu.substring(2, nu.length -2); //= h8
			cd = nu.substring(0, nu.length -5); //= g
			ef = nu.substring(3, nu.length -2);// =8			                                  
			res = ef - 1;                       //= 7
			a_from = cd + res;
			b_to = ab;
			c_promotion = document.getElementById('promote').value;			 
			}else{if (tp === 4){
			ab = nu.substring(0, nu.length -2); //= f8
			cd = nu.substring(0, nu.length -3); //= g
			ef = nu.substring(1, nu.length -2);// =8			                                  
			res = ef - 1;                       //= 7
			a_from = cd + res;
			b_to = ab;
			c_promotion = document.getElementById('promote').value;			 
			}}}}				
		    a = game.move({from:a_from, to:b_to, promotion:c_promotion} );		
		    board.position(game.fen());			
			$("#coronar").hide();
		    pws(); 
		    pbs();			
			//c1.innerHTML = a;
		    //c2.innerHTML = ng;
	}
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////


```

Este es el  script pagina text a qui  ya se logra coseguir lo que se queria no hay problemas y se resumio el codigo solo tendria  que mejorar el diseño de la popup y mirar si puedo quitar codigo  
```js
//////////////////////////////////////////////////////////////////////////////////////////////////	
	function promo(){
		nu = a.pop();
		tp = nu.length;
		if (tp === 7){
			ab = nu.substring(2, nu.length -3); //= h8
			cd = nu.substring(0, nu.length -6); //= g
			ef = nu.substring(3, nu.length -3);// =8
			
			if(game.turn() === 'w'){res = ef - 1;}else{res = parseInt(ef) +parseInt(1); }                             
			 
			a_from = cd + res;
			b_to = ab;
			c_promotion = document.getElementById('promote').value;			 
			}else{if (tp === 5){
			ab = nu.substring(0, nu.length -3); //= g8
			cd = nu.substring(0, nu.length -4); //= g
			ef = nu.substring(1, nu.length -3);// =8
						                                  
			if(game.turn() === 'w'){res = ef - 1;}else{res = parseInt(ef) +parseInt(1); }
			 
			a_from = cd + res;
			b_to = ab;
			c_promotion = document.getElementById('promote').value;			 
			}else{if (tp === 6){
			ab = nu.substring(2, nu.length -2); //= h8
			cd = nu.substring(0, nu.length -5); //= g
			ef = nu.substring(3, nu.length -2);// =8
						                                  
			if(game.turn() === 'w'){res = ef - 1;}else{res = parseInt(ef) +parseInt(1); }
			 
			a_from = cd + res;
			b_to = ab;
			c_promotion = document.getElementById('promote').value;			 
			}else{if (tp === 4){
			ab = nu.substring(0, nu.length -2); //= f8
			cd = nu.substring(0, nu.length -3); //= g
			ef = nu.substring(1, nu.length -2);// =8
						                                  
			if(game.turn() === 'w'){res = ef - 1;}else{res = parseInt(ef) +parseInt(1); }
			 
			a_from = cd + res;
			b_to = ab;
			c_promotion = document.getElementById('promote').value;			 
			}}}}				
		    a = game.move({from:a_from, to:b_to, promotion:c_promotion} );		
		    board.position(game.fen());			
			$("#coronar").hide();
		    pws(); 
		    pbs();			
			//c1.innerHTML = a;
		    //c2.innerHTML = ng;
	}
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////	


```
Disculpen el diseño de esta web y mi ortografia y apenas estoy aprendiendo a usar GITHUB 
este codigo es 100% free libre gratis puedes hacer lo que quieras con el por supuesto esto no icluye las api estas no son de mi propieda



