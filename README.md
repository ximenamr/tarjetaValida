Algoritmo de Luhn
____________________________
Este programa te permite validar que el número ingresado de tarjeta sea válido

 


 
El número ingresado en la caja de texto  debe :
1. Ser de longitud igual a 16
2. Contener solo números sin espacios ni letras ni carácteres especiales.

Presentamos el diagrama de flujo:
![recursos](assets/docs/diagramaDeFlujo.jpg)


 
Procedemos a explicar el pseudocódigo
```[javascript]

var cardNumber = prompt('Ingrese el número de su tarjeta sin espacios ni guiones');//Solicitamos que ingrese el número de tarjeta

function isValidCard(cardNumber)
{
  var sum = 0;
  var size = cardNumber.length;//Calcula la longitud de la tarjeta
  
  if (size===16){//Validamos que la longitud sea igual a 16 digitos 
    
    for(var i=size-1; i >= 0 ; i--) { //Recorre en forma inversa el número de la tarjeta
      
      var digit = parseInt(cardNumber.charAt(i));//Obtiene cada uno de los digitos de la tarjeta
      
      
      if(i % 2 ===0){
        digit *= 2; //multiplica por 2 las posiciones pares de la tarjeta y almacena la cantidad en la variable digit 
        
      }
      if(digit > 9){//luego de multiplicar verifica si es mayor a 9 y le resta si es el caso para obtener la suma de cifras
        digit -= 9;
        
      }
      sum += digit;//Suma los digitos pares que han sido operados y los impares
      
    }
     
    if (sum%10===0){//Si el residuo de sum entre 10 es 0 entonces la tarjeta es correcta
      console.log('El número de tarjeta ingresada es correcta'); 
    }
    else //Si el residuo de sum entre 10 es 0 entonces la tarjeta es incorrecta
    {
       console.log('El número de tarjeta ingresada es incorrecta');
    }
  }
  else
  {
    console.log('El número de tarjeta ingresada es incorrecta la longitud es diferente a 16');
  }
  
}

isValidCard(cardNumber);
