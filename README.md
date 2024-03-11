## Generador de Patrón de Rangoli en PHP

Este código PHP genera un patrón de Rangoli basado en un tamaño dado. El patrón de Rangoli es un patrón decorativo tradicional de la India que se hace en el suelo en ocasiones especiales.

### Descripción:

Este script PHP define una función llamada `generarRangoli()` que toma un parámetro `$tamaño` que especifica el tamaño del patrón de Rangoli que se generará.

### Explicación paso a paso:

1. La función `generarRangoli()` verifica si el tamaño proporcionado es válido. Si el tamaño es menor o igual a cero, muestra un mensaje de error y termina la ejecución del script.
```php
// Función para generar un patrón de Rangoli
function generarRangoli($tamaño) {
    // Verificar que el tamaño sea válido
    if ($tamaño <= 0) {
        echo "El tamaño del patrón de Rangoli debe ser un número positivo.";
        return;
    }
```

2. Se crea un array de letras del alfabeto desde 'a' hasta 'z'. Estas letras se utilizarán para construir el patrón de Rangoli.

```php
    $letras = range('a', 'z');
```

3. Se itera sobre las filas del patrón de Rangoli, comenzando desde la fila superior hasta la fila inferior, para cada fila se reliza el primer for:

```php
    // Generar el patrón de Rangoli
    for ($i = $tamaño - 1; $i >= -$tamaño + 1; $i--) {
        $linea = "";
```

   - Se construye la parte izquierda de la línea del patrón de Rangoli, agregando las letras correspondientes desde 'a' hasta la letra central y separándolas con guiones.
     
```php
        // Construir la parte izquierda de la línea
        for ($j = $tamaño - 1; $j >= abs($i); $j--) {
            $linea .= $letras[abs($j)];
            if ($j != abs($i)) {
                $linea .= "-";
            }
        }
```

   - Se construye la parte derecha de la línea del patrón de Rangoli, agregando las letras correspondientes desde la letra central hasta 'a' y separándolas con guiones. Para las filas         inferiores, las letras se agregan en orden inverso.

```php
        // Construir la parte derecha de la línea hasta llegar a la linea media
        if($i>=0){
            for ($j = $i+1; $j < $tamaño; $j++) {
                
                if ($j != abs($i)) {
                    $linea .= "-";
                }
                $linea .= $letras[abs($j)];
            }

        // Construir la parte derecha de la línea de la linea media hacia abajo
        }else{
            for ($j = $tamaño-1; $j > abs($i); $j--) {
                
                if ($j != abs($i)) {
                    $linea .= "-";
                }
                $linea .= $letras[abs($tamaño-($j+$i))];
                
            }
        }
```

   - Se añaden espacios en blanco a cada lado de la línea para centrarla en el patrón de Rangoli.

```php
        // Añadir espacios a cada lado de la línea
        $espacios = str_repeat("-", abs($i) * 2);
        echo str_repeat($espacios,1);
        echo $linea;
        echo str_repeat($espacios, 1);
        echo PHP_EOL;
  
    }
}
```

4. Finalmente, se muestra el patrón de Rangoli en la salida estándar.

```php
// Ejemplo de uso
generarRangoli(5);

?>
```





   
   
   
   
   


