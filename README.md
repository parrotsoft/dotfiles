# 🏃‍♂️ Cómo ejecutar la configuración

## 🐧 Mac / Linux

Ejecuta el siguiente comando para aplicar los cambios en tu terminal:

```bash
source ~/.zshrc
```

---

## 🪟 Windows (Git Bash)

1. **Crear el archivo `.bashrc`**  
   En el directorio de tu usuario, crea el archivo:

   ```
   C:\Users\{TU_USUARIO}\.bashrc
   ```

2. **Agregar configuración de Oh My Posh**  
   Dentro del archivo `.bashrc`, agrega la siguiente línea:

   ```bash
   eval "$(oh-my-posh --init --shell bash --config ~/easy-term.omp.json)"
   ```

3. **Copiar el tema `easy-term.omp.json`**  
   Copia el archivo del tema desde:

   ```
   C:\Users\{TU_USUARIO}\AppData\Local\Programs\oh-my-posh\themes\easy-term.omp.json
   ```

   Hacia el directorio de tu usuario (donde está el `.bashrc`), es decir:

   ```
   C:\Users\{TU_USUARIO}\
   ```

---

> 💡 Reemplaza `{TU_USUARIO}` por el nombre real de tu usuario en Windows.
