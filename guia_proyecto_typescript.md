# 🛠 Guía para Iniciar un Proyecto Web (Vite + React + Express + TypeScript)

---

## 📦 Parte 1: Instalación de herramientas básicas

### ✅ 1.1 Instalar Node.js (v18+)

- https://nodejs.org/
- Verificar instalación:

```bash
node -v
npm -v
```

### ✅ 1.2 Instalar Git

- https://git-scm.com/downloads
- Verificar instalación:

```bash
git --version
```

### ✅ 1.3 Instalar VSCode

- https://code.visualstudio.com/

### ✅ 1.4 (Windows) Instalar WSL2 y Ubuntu

- [Guía oficial WSL](https://learn.microsoft.com/en-us/windows/wsl/install)
- Abrir Ubuntu y configurar usuario
- Instalar Node.js y Git también dentro de WSL

---

## 🧩 Parte 2: Configuración inicial de VSCode

### ✅ 2.1 Crear y usar un perfil personalizado

- Abre VSCode
- `Ctrl+Shift+P` → "Preferences: Open Profiles (UI)"
- Crea un nuevo perfil
- Importa configuraciones, snippets y extensiones

> Puedes exportar tus extensiones con:

```bash
code --list-extensions > extensions.txt
```

> Para importar:

```bash
cat extensions.txt | xargs -L 1 code --install-extension
```

---

## 🌐 Parte 3: Crear cuenta y configurar GitHub

### ✅ 3.1 Crear cuenta en GitHub

- https://github.com/

### ✅ 3.2 Configurar Git en local

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@ejemplo.com"
```

### ✅ 3.3 Crear un nuevo repositorio en GitHub

- Dale un nombre, descripción y configura si es público o privado.
- (Opcional) Añadir README y archivo `.gitignore`.

---

### ✅ 3.4 Clonar repositorio y configurar SSH

#### 🗝 Paso 1: Verificar si ya tienes una clave SSH

```bash
ls -la ~/.ssh
```

Si ves archivos como `id_ed25519` y `id_ed25519.pub`, ya tienes una clave.

#### 🔐 Paso 2: Generar clave SSH (si no tienes)

```bash
ssh-keygen -t ed25519 -C "tuemail@ejemplo.com"
```

#### 📋 Paso 3: Copiar clave pública

```bash
cat ~/.ssh/id_ed25519.pub
```

#### 🔗 Paso 4: Añadir clave a GitHub

- https://github.com/settings/keys → **New SSH Key**

#### 🔍 Paso 5: Probar conexión

```bash
ssh -T git@github.com
```

Deberías ver:

```
Hi tuusuario! You've successfully authenticated...
```

#### ⬇ Paso 6: Clonar repositorio

```bash
git clone git@github.com:tuusuario/turepo.git
cd turepo
code .
```

---

## ⚙️ Parte 4: Crear proyecto frontend con Vite + React + TypeScript

### ✅ 4.1 Crear nuevo proyecto

```bash
npm create vite@latest
```

Selecciona:

- Framework: `React`
- Variante: `TypeScript`

### ✅ 4.2 Instalar dependencias y ejecutar

```bash
cd mi-proyecto
npm install
npm run dev
```

---

## 🖥️ Parte 5: Crear backend con Express + TypeScript

### ✅ 5.1 Crear proyecto backend

```bash
mkdir backend
cd backend
npm init -y
npm install express cors
npm install -D typescript ts-node-dev @types/node @types/express
npx tsc --init
```

### ✅ 5.2 Crear archivo `index.ts`

```ts
import express from "express";
import cors from "cors";

const app = express();
const PORT = 3001;

app.use(cors());
app.use(express.json());

app.get("/", (_req, res) => {
  res.send("Servidor Express con TypeScript funcionando");
});

app.listen(PORT, () => {
  console.log(`Servidor en http://localhost:${PORT}`);
});
```

### ✅ 5.3 Ejecutar servidor en desarrollo

```bash
npx ts-node-dev index.ts
```

---

## 🧠 Parte 6: Uso de NPM y bloqueo de dependencias

### ✅ 6.1 Iniciar proyecto (si aún no tienes package.json)

```bash
npm init -y
```

### ✅ 6.2 Instalar dependencias

```bash
npm install react
npm install -D typescript @types/react @types/node
npm install -D nodemon
```

### ✅ 6.3 Bloquear versiones (automático con package-lock.json)

Este archivo asegura que todos usen las mismas versiones.

> Para una instalación limpia:

```bash
npm ci
```

### ✅ 6.4 Ejecutar scripts

Define en `package.json`:

```json
"scripts": {
  "dev": "vite",
  "backend": "ts-node-dev backend/index.ts"
}
```

Y corre con:

```bash
npm run dev
npm run backend
```

### ✅ 6.5 Usar `npx` para herramientas sin instalar globalmente

```bash
npx eslint .
npx create-react-app my-app
```

---

## 🚀 Parte 7: Subir proyecto a GitHub

```bash
git init
git add .
git commit -m "init vite + react + express + typescript"
git remote add origin git@github.com:tuusuario/turepo.git
git push -u origin main
```

---

## 🎁 Parte 8: Buenas prácticas

### ✅ 8.1 Commits claros

```bash
git commit -m "feat: navbar responsive"
```

### ✅ 8.2 Usar `.env` para variables sensibles

Archivo `.env.local`:

```
API_KEY=abc123
```

```ts
// Usando variables de entorno en Vite (frontend)
console.log(import.meta.env.VITE_API_KEY);
```

```ts
// Usando variables de entorno en Node.js (backend)
// Necesitas instalar dotenv: npm install dotenv
import dotenv from "dotenv";
dotenv.config();

console.log(process.env.API_KEY);
```

---

**Explicación:**

- En **Vite (frontend)**, las variables de entorno se acceden mediante `import.meta.env.VITE_...` y deben empezar con `VITE_`.
- En **Node.js (backend)**, se usa el paquete [`dotenv`](https://www.npmjs.com/package/dotenv) para cargar variables del archivo `.env`, que se acceden con `process.env.NOMBRE_VARIABLE`.

¿Quieres que te ayude a incluir esto en tu guía?

> ⚠️ Agrega `.env*` a tu `.gitignore`

---

¿Qué es .gitignore?
El archivo .gitignore es un fichero especial en tu repositorio Git que indica qué archivos o carpetas no deben ser incluidos en los commits ni subidos al repositorio remoto (GitHub, GitLab, etc). Esto es muy útil para proteger información sensible o archivos que no son necesarios compartir.
