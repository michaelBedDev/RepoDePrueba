Perfecto. Aquí tienes una guía completa, bien explicada y estructurada en formato Markdown sobre cómo usar `npm` desde cero, instalar paquetes y bloquear versiones de dependencias.

---

````md
### ✅ 3.5 Uso básico de NPM y bloqueo de dependencias

#### 📦 ¿Qué es NPM?

**NPM** (Node Package Manager) es el gestor de paquetes oficial para Node.js. Permite:

- Instalar paquetes (librerías o herramientas).
- Ejecutar scripts definidos en el proyecto.
- Mantener versiones y dependencias de forma controlada mediante los archivos `package.json` y `package-lock.json`.

---

#### 🧱 1. Inicializar un proyecto Node.js

Para iniciar un proyecto y crear un `package.json`, abre una terminal en la carpeta del proyecto y ejecuta:

```bash
npm init -y
```
````

Esto generará un archivo `package.json` con valores por defecto.

---

#### 📥 2. Instalar dependencias

Para instalar una librería (por ejemplo, Express):

```bash
npm install express
```

Esto hará dos cosas:

- Añadirá `express` en la sección `"dependencies"` del `package.json`.
- Creará (o actualizará) el archivo `package-lock.json` con la versión exacta instalada.

Si quieres instalar una dependencia **solo para desarrollo** (como nodemon):

```bash
npm install -D nodemon
```

Esto la añadirá a la sección `"devDependencies"`.

---

#### 📌 3. Bloquear dependencias

El archivo `package-lock.json` **bloquea exactamente las versiones instaladas** de todas las dependencias (y sus subdependencias). Este archivo debe **compartirse** (por ejemplo, subirlo a Git) para garantizar que todos los colaboradores instalen las mismas versiones.

💡 **Nunca lo borres manualmente a menos que sepas lo que haces.**

---

#### 🔧 4. Scripts personalizados

Dentro de `package.json`, puedes definir comandos en la sección `"scripts"`. Ejemplo:

```json
"scripts": {
  "dev": "nodemon index.js",
  "start": "node index.js"
}
```

Y ejecutarlos así:

```bash
npm run dev
npm start
```

---

#### 🔁 5. Reinstalar dependencias

Si clonas un repositorio con `package.json` y `package-lock.json`, puedes reinstalar exactamente todo con:

```bash
npm install
```

Esto crea la carpeta `node_modules` y recupera todo lo necesario.

---

#### 🧹 6. Eliminar y limpiar

Si quieres empezar desde cero (por ejemplo, eliminar todas las dependencias):

```bash
rm -rf node_modules package-lock.json
npm install
```

Esto reconstruirá el árbol de dependencias desde `package.json`.

---

#### 📦 7. Ver dependencias instaladas

```bash
npm list --depth=0
```

O para desarrollo:

```bash
npm list -D --depth=0
```

---

#### 🚫 8. Ignorar node_modules

Recuerda que `node_modules/` **no debe subirse a Git**. Asegúrate de tenerlo en tu `.gitignore`:

```
node_modules/
```

---

Esta guía básica te permitirá trabajar con `npm` de forma controlada, evitando conflictos de versiones y asegurando que tu proyecto sea reproducible en cualquier máquina.

```

```
