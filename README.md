# BMI Calculator 🏋️‍♂️

¡Bienvenido al proyecto **BMI Calculator**! Esta es una aplicación web sencilla pero poderosa que te permite calcular tu Índice de Masa Corporal (BMI) de manera rápida y eficiente. El BMI es una medida útil para evaluar si tu peso está dentro de un rango saludable en relación con tu altura. 

## Características ✨

- **Interfaz intuitiva**: Diseño limpio y fácil de usar.
- **Cálculo instantáneo**: Obtén tu BMI y categoría de peso al instante.
- **Personalización**: Ingresa tu edad, género, altura y peso para obtener resultados precisos.
- **Responsivo**: Funciona en dispositivos móviles y de escritorio.

## Tecnologías Utilizadas 🛠️

- **HTML**: Estructura básica de la aplicación.
- **CSS**: Estilos y diseño visual.
- **JavaScript**: Lógica de cálculo y manipulación del DOM.

## Funcionamiento 🚀

### Estructura HTML

La aplicación está construida con un archivo HTML que define la estructura básica de la interfaz de usuario. Aquí hay algunos elementos clave:

- **Inputs**: Campos para ingresar la edad, género, altura y peso.
- **Range Sliders**: Deslizadores para ajustar la altura y el peso.
- **Botón de cálculo**: Un botón que activa la función de cálculo del BMI.
- **Resultados**: Área donde se muestra el BMI calculado y la categoría de peso.

```html
<div class="container">
    <h1>BMI Calculator</h1>
    <div class="input-group">
        <h3 for="age">Age:</h3>
        <input type="number" id="age" name="age" min="1" max="120">
    </div>
    <div class="input-group">
        <h3>Gender:</h3>
        <div class="radio-group">
            <input type="radio" name="gender" id="male" value="male">
            <label for="male">Male</label>
            <input type="radio" name="gender" id="female" value="female">
            <label for="female">Female</label>
        </div>
    </div>
    <hr>
    <div class="input-group">
        <h3 for="height">Height (cm):</h3>
        <input type="range" name="height" id="height" min="100" max="250" value="170"
        oninput="updateHeightValue(this.value)">
        <span id="height-value">170</span> cm
    </div>
    <hr>
    <div class="input-group">
        <h3 for="height">Weight (cm):</h3>
        <input type="range" name="weight" id="weight" min="30" max="150" value="70"
        oninput="updateWeightValue(this.value)">
        <span id="weight-value">70</span> kg
    </div>
    <hr>
    <button onclick="calculateBMI()">Calculate BMI</button>
    <div class="output">
        <h2>Your BMI: <span id="bmi-result">0</span></h2>
        <p id="bmi-category"> </p>
    </div>
</div>
```
### Estilos CSS
El archivo `style.css` contiene los estilos que dan vida a la aplicación. Se utiliza un fondo degradado, sombras y bordes redondeados para crear una interfaz atractiva y moderna.

```css
body {
    font-family: sans-serif;
    background: linear-gradient(to right, darkcyan, darkgoldenrod);
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    background: rgba(255, 255, 255, 0.2);
    padding: 20px;
    border-radius: 15px;
    box-shadow: 0 0 15px rgba(0, 0, 0, 0.6);
    text-align: center;
    width: 400px;
}
```

### Lógica en JavaScript
El archivo `script.js` contiene la lógica principal de la aplicación. Aquí se maneja la interacción del usuario, el cálculo del BMI y la actualización dinámica de la interfaz.

Funciones Principales
1. **Actualización de Valores**: Las funciones `updateHeightValue` y `updateWeightValue` actualizan los valores de altura y peso en tiempo real mientras el usuario ajusta los deslizadores.

```javascript
function updateHeightValue(value) {
    document.getElementById('height-value').textContent = value;
}

function updateWeightValue(value) {
    document.getElementById('weight-value').textContent = value;
}
```
2. **Cálculo del BMI**: La función calculateBMI toma los valores de altura, peso, edad y género, y calcula el BMI. Luego, clasifica el resultado en una categoría de peso.

```javascript
function calculateBMI() {
    const height = document.getElementById('height').value;
    const weight = document.getElementById('weight').value;
    const age = document.getElementById('age').value;
    const gender = document.querySelector("input[name='gender']:checked");

    if(!age || !gender) {
        alert('Please fill all the fields');
        return;
    }

    const bmi = (weight / ((height / 100) ** 2)).toFixed(1);

    document.getElementById('bmi-result').textContent = bmi;

    let category = '';

    if(bmi < 18.5) {
        category = 'Underweight';
    }else if(bmi < 24.9) {
        category = 'Normal weight';
    }else if(bmi < 29.9) {
        category = 'Overweight';
    }else {
        category = 'Obesity';
    }

    document.getElementById('bmi-category').textContent = category;
}
```

## Manejo del DOM 🌐
La aplicación utiliza JavaScript para manipular el DOM y actualizar dinámicamente la interfaz de usuario. Aquí hay algunos conceptos clave aplicados:

- **Selección de Elementos**: Se utilizan métodos como `getElementById` y `querySelector` para seleccionar elementos del DOM.

- **Actualización de Contenido**: Se actualiza el contenido de los elementos HTML usando propiedades como `textContent`.

- **Eventos**: Se utilizan eventos como `oninput` y `onclick` para capturar la interacción del usuario y ejecutar funciones en respuesta.

## Cómo Usar la Aplicación 📝
1. **Ingresa tu Edad**: Introduce tu edad en el campo correspondiente.

1. **Selecciona tu Género**: Elige entre "Male" (Hombre) o "Female" (Mujer).

1. **Ajusta tu Altura**: Utiliza el deslizador para seleccionar tu altura en centímetros.

1. **Ajusta tu Peso**: Utiliza el deslizador para seleccionar tu peso en kilogramos.

1. **Calcula tu BMI**: Haz clic en el botón "Calculate BMI" para obtener tu Índice de Masa Corporal y la categoría de peso correspondiente.