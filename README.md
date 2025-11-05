# 🔒 Simulador de Vulnerabilidades XSS

**Trabajo de la asignatura:** Sistemas Distribuidos  
**Autores:** Andrés Palacio y Carlos Cochero

Una herramienta educativa interactiva para demostrar y entender las vulnerabilidades de Cross-Site Scripting (XSS) en aplicaciones web.

## 📋 ¿Qué es esto?

Este es un simulador educativo que demuestra cómo funcionan los ataques XSS (Cross-Site Scripting) y por qué es crucial sanitizar las entradas de usuario en aplicaciones web. La herramienta permite alternar entre un modo **vulnerable** y un modo **protegido** para comparar el comportamiento.

## 🚀 Cómo usar

### Instalación

1. Descarga el archivo `index.html`
2. Abre el archivo directamente en tu navegador web (Chrome, Firefox, Safari, Edge, etc.)
3. No requiere servidor web ni instalación adicional

### Uso básico

1. **Selecciona el modo:**
   - **Modo Vulnerable** (rojo): Permite la ejecución de scripts maliciosos
   - **Modo Protegido** (verde): Sanitiza el input y previene XSS

2. **Prueba los ejemplos:**
   - Haz clic en cualquiera de los 8 ejemplos de payloads XSS
   - El código se cargará automáticamente en el campo de entrada
   - Presiona "Submit Comment" para ejecutar

3. **Observa los resultados:**
   - En modo vulnerable: Los scripts se ejecutarán
   - En modo protegido: Los scripts se mostrarán como texto plano
   - Revisa el panel de logs para ver el historial de acciones

## 🎯 Características

### Panel de Estadísticas
- **Total Attacks**: Contador de intentos de XSS detectados
- **Blocked**: Ataques bloqueados en modo protegido
- **Executed**: Scripts ejecutados en modo vulnerable

### 8 Ejemplos de Payloads XSS

1. **Basic Alert XSS**: `<script>alert("XSS Attack!")</script>`
   - El payload XSS más básico usando la etiqueta script

2. **Image Error XSS**: `<img src=x onerror=alert('XSS')>`
   - Explota el evento onerror de imágenes

3. **SVG Onload XSS**: `<svg onload=alert('SVG XSS')>`
   - Usa elementos SVG para ejecutar código

4. **Input Autofocus XSS**: `<input autofocus onfocus=alert('Focus XSS')>`
   - Explota eventos de enfoque automático

5. **Body Onload XSS**: `<body onload=alert('Body Onload')>`
   - Intenta inyectar una etiqueta body maliciosa

6. **Iframe XSS**: `<iframe src="javascript:alert('Iframe XSS')">`
   - Usa iframes con protocolo javascript:

7. **Marquee XSS**: `<marquee onstart=alert('Marquee XSS')>`
   - Explota la etiqueta marquee obsoleta

8. **Details/Summary XSS**: `<details open ontoggle=alert('Details XSS')>`
   - Usa elementos HTML5 interactivos

### Sistema de Logs
- Registra cada acción realizada
- Muestra timestamp de cada evento
- Indica si el ataque fue bloqueado o ejecutado
- Código de colores para fácil identificación

### Sección Educativa
Incluye información sobre:
- Qué es XSS
- Tipos de ataques XSS
- Cómo protegerse contra XSS

## 🔧 Cómo funciona técnicamente

### Modo Vulnerable
\`\`\`javascript
// El input se inserta directamente en el DOM sin sanitización
outputDiv.innerHTML = userInput;
\`\`\`

### Modo Protegido
\`\`\`javascript
// El input se sanitiza usando textContent
const safeDiv = document.createElement('div');
safeDiv.textContent = userInput;
outputDiv.innerHTML = safeDiv.innerHTML;
\`\`\`

### Sanitización
El modo protegido convierte caracteres especiales en entidades HTML:
- `<` se convierte en `&lt;`
- `>` se convierte en `&gt;`
- `"` se convierte en `&quot;`
- `'` se convierte en `&#39;`

Esto previene que el navegador interprete el input como código HTML/JavaScript.

## ⚠️ Advertencias importantes

### ⚡ Solo para fines educativos
- Esta herramienta es **exclusivamente educativa**
- Está diseñada para enseñar sobre seguridad web
- **NUNCA** uses estos conocimientos para atacar sitios web reales

### 🚫 Uso ético
- No uses estos payloads en sitios web que no te pertenezcan
- No intentes explotar vulnerabilidades sin autorización
- El hacking no autorizado es ilegal

### 📚 Propósito educativo
Esta herramienta te ayuda a:
- Entender cómo funcionan los ataques XSS
- Aprender a proteger tus aplicaciones web
- Desarrollar código más seguro
- Concientizar sobre la importancia de la sanitización de inputs

## 🛡️ Mejores prácticas de seguridad

### Para desarrolladores:

1. **Nunca confíes en el input del usuario**
   - Siempre valida y sanitiza todas las entradas

2. **Usa las herramientas correctas**
   - Frameworks modernos (React, Vue, Angular) sanitizan por defecto
   - Usa librerías como DOMPurify para sanitización avanzada

3. **Implementa Content Security Policy (CSP)**
   - Restringe las fuentes de scripts permitidas
   - Previene la ejecución de scripts inline

4. **Escapa el output**
   - Usa `textContent` en lugar de `innerHTML` cuando sea posible
   - Escapa caracteres especiales en HTML

5. **Valida en el servidor**
   - La validación del cliente puede ser bypasseada
   - Siempre valida y sanitiza en el backend

## 📖 Recursos adicionales

- [OWASP XSS Guide](https://owasp.org/www-community/attacks/xss/)
- [MDN Web Security](https://developer.mozilla.org/en-US/docs/Web/Security)
- [Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)

## 🤝 Contribuciones

Este es un proyecto educativo. Si encuentras formas de mejorarlo o agregar más ejemplos educativos, las sugerencias son bienvenidas.

## 📄 Licencia

Este proyecto es de código abierto y está disponible para fines educativos.

---

**Recuerda**: La seguridad web es responsabilidad de todos. Usa este conocimiento para construir aplicaciones más seguras. 🔐
