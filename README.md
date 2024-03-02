    familia-fuente: Arial, sans-serif;
    Margen: 0;
    Relleno: 0;
    Pantalla: Flex;
    justify-content: centro;
    align-items: centro;
    color de fondo: #ffe6e6;
    Altura: 100VH;
    posición: relativa;
  }

 . background-overlay {
    posición: fija;
    Arriba: 0;
    Izquierda: 0;
    Ancho: 100%;
    Altura: 100%;
    color de fondo: #ffcccc;

  }

 . Rosa {
    Ancho: 100%;
    Altura: 100%;
    color de fondo: #ffcccc;
    posición: relativa;
    desbordamiento: oculto;
  }

 . rosa::antes,
 . rosa::después {
    Contenido: '';
    posición: absoluta;
    Ancho: 100px;
    Altura: 100px;
    color de fondo: #cc0066;
    radio de borde: 50%;
  }

 . rosa::antes {
    Arriba: -40px;
    izquierda: -40px;
    transformar: rotar (45grados);
  }

 . rosa::después {
    Fondo: -40px;
    Derecha: -40px;
    transformar: rotar (-45grados);
  }

  h1 {
    tamaño de fuente: 36px;
    Color: #CC0066;
    text-align: centro;
    font-family: 'Comic Sans MS', cursiva, sans-serif;
  }

 . Boton {
    Pantalla: bloque en línea;
    Relleno: 10px 20px;
    Margen: 0 10px;
    color de fondo: #6C3597; 
    Color: #FFF;
    Frontera: ninguna;
    border-radius: 5px;
    cursor: puntero;
    tamaño de fuente: 16px;
    text-align: centro;
    decoración de texto: ninguna;
    Transición: color de fondo 0,3s;
  }

 . boton:hover {
    color de fondo: #8E44AD; 
  }

 . Contenedor {
    text-align: centro;
  }

 . Imagen {
    Ancho: 200px;
    Altura: 200px;
    Transición: Opacidad 1s;
    color de fondo: blanco;
    borde: 2px sólido #6C3597; 
    border-radius: 20px; 
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2); 
  }   

 . rojo {
    color: rojo;
  }

 . burbuja individual {
    posición: absoluta;
    radio de borde: 100%;
    Fondo: 10px;
    color de fondo: blanco;
    Índice z: 1;
  }

<! DOCTYPE html>
<html lang="es">
<cabeza>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="hoja de estilo" href="./css/main.css"/>
  <título>¿Me perdonas mi amor? </título>
</cabeza>

<cuerpo>
  <div class="background-overlay"></div>
  <div class="rosa">
    <div class="contenedor">
      <Br />
      <img src="/img/inicio.gif" class="imagen imagen-gif" id="imagen">
      <h1 id="mensaje">¿Quieres ser mi novia? </h1>
      <button class="boton" id="btnSi">Sí</button>
      <button class="boton" id="btnNo">No</button>
    </Div>
  </Div>

  <script language="javascript" type="text/javascript" src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>

  <script language="javascript" type="text/javascript" src="./js/main.js"> </script>
</cuerpo>

</HTML>

const btnSi = documento.getElementById('btnSi');
const btnNo = documento.getElementById('btnNo');
const imagen = documento.getElementById('imagen');
const mensaje = documento.getElementById('mensaje');
const imagenes = [
    "1.gif",
    "2.gif",
    "3.gif",
    "4.gif",
    "5.gif",
    "6.gif",
    "7.gif",
    "8.gif"
];
let índice = -1;

btnSi.addEventListener('click', función () {
    Swal.Fuego({
        título: '¡Sabia que dirías que sí!😘 ',
        texto: '¡te amo te amo te amo! 🥰 ',
        imageUrl: 'img/image_SI.gif',
        confirmButtonText: 'Cerrar'
    }).then((resultado) => {
        felicidades();
        clearInterval(intervalo);
        imagen.src = "/img/image_OK.gif";
        btnSi.estilo.display = 'ninguno';
        btnNo.estilo.display = 'ninguno';
        mensaje.textContent = ' ❤ ¡Gracias por perdonarme mi amor hermosa! 🥰❤ ';
    });
});

btnNo.addEventListener('mouseover', función () {
    moverBoton();
});

función moverBoton() {
    const botonRect = btnNo.getBoundingClientRect();
    const width = ventana.innerWidth - botonRect.Ancho;
    const height = ventana.innerHeight - botonRect.altura;

    btnNo.estilo.posición = "absoluto";
    btnNo.estilo.left = (Matemáticas.random() * width) + "px";
    btnNo.estilo.top = (Matemáticas.random() * altura) + "px";
}

const interval = setInterval(() => {
    índice++;

    if (índice >= imágenes.largura) {
        índice = 0;
    }

    imagen.src = '/img/' + imagenes[index];
}, 3000);


function felicidades() {
    var bArray = [];
    var sArray = [2, 4, 6, 8];
    var contenedor = documento.querySelector('.contenedor');
    para (var i = 0;  Yo < contenedor.offsetWidth;  Yo++) {
        bArray.empujar(i);
    }

    setInterval(función () {
        var tamaño = random(sArray);
        var div = documento.createElement('div');
        div.classList.add('burbuja-individual');
        div.estilo.left = random(bArray) + 'px';
        div.estilo.ancho = tamaño + 'px';
        div.estilo.Altura = tamaño + 'px';
        div.estilo.bottom = '10px';
        div.estilo.posición = 'absoluto';
        div.estilo.zIndex = '1';
        contenedor.appendChild(div);

        animar(div);
    }, 150);
}

función animate(div) {
    var inferior = 10;
    var opacidad = 1;

    var animationInterval = setInterval(function () {
        inferior += 2;
        Opacidad -= 0.007;
        div.estilo.bottom = fondo + '%';
        div.estilo.opacidad = opacidad;

        if (> inferior = 100) {
            clearInterval(animationInterval);
            div.eliminar();
        }
    }, 80);
}

función random(datos) {
    return data[Matemáticas.piso(Matemáticas.random() * datos.largura)];
}
--->
