# 📋 Instrucciones: Subir CV a GitHub
## InfraestructuraIT — Hoja de Vida 2025

---

## PASO 1 — Preparar la carpeta local

Abre **PowerShell** y crea la carpeta del proyecto:

```powershell
# Navegar a tu directorio de proyectos
cd "C:\Users\User01\OneDrive\2026-proyectos"

# Crear carpeta para el CV
mkdir cv-iit-2025
cd cv-iit-2025
```

Copia los archivos descargados de Claude a esa carpeta:

```
cv-iit-2025/
├── hoja_de_vida_jairo_sepulveda_2025.html   ← el CV con seguridad
└── foto_jairo_cv.jpg                         ← foto (respaldo, ya embebida)
```

---

## PASO 2 — Inicializar Git

```powershell
# Inicializar repositorio local
git init

# Configurar identidad (si no está configurada)
git config user.name "infraestructura-it"
git config user.email "proyectosing@infraestructura-it.com"
```

---

## PASO 3 — Crear .gitignore

```powershell
# Crear .gitignore para excluir archivos innecesarios
@"
.DS_Store
Thumbs.db
*.log
node_modules/
"@ | Out-File -Encoding utf8 .gitignore
```

---

## PASO 4 — Primer commit

```powershell
# Agregar todos los archivos al staging
git add .

# Ver qué archivos se van a subir
git status

# Hacer el commit inicial
git commit -m "feat: CV Jairo Sepúlveda 2025 — IIT con seguridad por cédula y QR"
```

---

## PASO 5 — Crear el repositorio en GitHub (con gh CLI)

```powershell
# Asegúrate de estar autenticado (si no, ejecuta: gh auth login)
gh auth status

# Crear repo PRIVADO en la org infraestructura-it y hacer push en un solo comando
gh repo create infraestructura-it/cv-iit-2025 `
  --private `
  --source=. `
  --remote=origin `
  --push `
  --description "Hoja de vida Jairo Sepúlveda Cortes — InfraestructuraIT SAS 2025"
```

> ⚠️ **Nota:** El repo es `--private` porque el CV tiene información personal.
> Si lo quieres público, cambia a `--public`.

---

## PASO 6 — Verificar el push

```powershell
# Verificar que el push fue exitoso
git log --oneline

# Ver el remoto configurado
git remote -v

# Abrir el repo en el navegador
gh repo view --web
```

Deberías ver algo como:
```
origin  https://github.com/infraestructura-it/cv-iit-2025 (fetch)
origin  https://github.com/infraestructura-it/cv-iit-2025 (push)
```

---

## PASO 7 — Actualizaciones futuras

Cada vez que hagas cambios al CV:

```powershell
# Agregar cambios
git add .

# Commit con mensaje descriptivo
git commit -m "update: [describe el cambio]"

# Push al repositorio
git push origin main
```

---

## 🔑 Si el PAT expira o pide autenticación

```powershell
# Re-autenticar con GitHub CLI
gh auth login

# Seleccionar:
#   → GitHub.com
#   → HTTPS
#   → Login with a web browser (o pegar token)
```

El PAT debe tener los scopes: `repo`, `workflow`, `write:packages`

---

## 📌 Estructura final del repo

```
infraestructura-it/cv-iit-2025
├── hoja_de_vida_jairo_sepulveda_2025.html
├── foto_jairo_cv.jpg
├── .gitignore
└── README.md  (opcional)
```

---

## 💡 Opcional — Agregar README

```powershell
@"
# CV — Jairo Sepúlveda Cortes

Hoja de vida profesional con protección por número de cédula.

**Empresa:** InfraestructuraIT SAS  
**Rol:** Director General  
**Contacto:** proyectosing@infraestructura-it.com

> Documento de acceso restringido.
"@ | Out-File -Encoding utf8 README.md

git add README.md
git commit -m "docs: agregar README"
git push origin main
```

---

*Generado por IIT · infraestructura-it.github.io*
