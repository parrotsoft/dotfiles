# Dotfiles

Repositorio para gestionar mis dotfiles usando un repositorio Git bare.

---

# Crear el repositorio por primera vez

## 1. Crear el repositorio bare

```bash
git init --bare $HOME/.cfg
```

---

## 2. Crear alias `config`

```bash
alias config="/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME"
```

---

## 3. Ocultar archivos no rastreados

```bash
config config --local status.showUntrackedFiles no
```

Esto evita que Git muestre todos los archivos del HOME.

---

## 4. Persistir el alias

### Zsh

```bash
echo 'alias config="/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME"' >> $HOME/.zshrc
```

### Bash

```bash
echo 'alias config="/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME"' >> $HOME/.bashrc
```

---

## 5. Ignorar el repositorio bare

```bash
echo ".cfg/" >> $HOME/.gitignore
```

---

## 6. Agregar archivos

```bash
config add .gitignore
config add .zshrc
config add .gitconfig
config add .gitconfig.local.example
```

---

## 7. Realizar commit

```bash
config commit -m "Initial dotfiles commit"
```

---

## 8. Conectar repositorio remoto

```bash
config remote add origin git@github.com:parrotsoft/dotfiles.git
```

---

## 9. Subir cambios

```bash
config push -u origin master
```

---

# Configurar otra máquina

## 1. Clonar el repositorio bare

```bash
git clone --bare git@github.com:parrotsoft/dotfiles.git $HOME/.cfg
```

---

## 2. Crear alias temporal

```bash
alias config="/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME"
```

---

## 3. Ignorar el repositorio bare

```bash
echo ".cfg/" >> $HOME/.gitignore
```

---

## 4. Hacer checkout de los archivos

```bash
config checkout
```

---

## 5. Ocultar archivos no rastreados

```bash
config config --local status.showUntrackedFiles no
```

---

## 6. Persistir el alias

### Zsh

```bash
echo 'alias config="/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME"' >> $HOME/.zshrc
```

### Bash

```bash
echo 'alias config="/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME"' >> $HOME/.bashrc
```

---

# Uso diario

## Ver estado

```bash
config status
```

---

## Agregar cambios

```bash
config add .zshrc
```

---

## Commit

```bash
config commit -m "Update zsh config"
```

---

## Push

```bash
config push
```

---

# Configuración de Git

Este repositorio utiliza una configuración híbrida para Git:

- `.gitconfig` → configuración común versionada
- `.gitconfig.local` → configuración privada/local NO versionada
- `.gitconfig.local.example` → ejemplo de configuración local

---

## `.gitconfig`

Archivo principal compartido entre todas las máquinas.

```ini
[filter "lfs"]
	required = true
	clean = git-lfs clean -- %f
	smudge = git-lfs smudge -- %f
	process = git-lfs filter-process

[user]
	name = Miguel Lopez Ariza

[init]
	defaultBranch = master

[include]
	path = .gitconfig.local
```

---

## `.gitconfig.local`

Archivo local privado para cada máquina.

Ejemplo:

```ini
[user]
	email = lopezarizamiguel@gmail.com
```

Este archivo NO debe versionarse.

---

## `.gitconfig.local.example`

Archivo de referencia incluido en el repositorio.

```ini
[user]
	email = lopezarizamiguel@gmail.com
```

---

# Configurar Git en una nueva máquina

## 1. Copiar archivo de ejemplo

```bash
cp ~/.gitconfig.local.example ~/.gitconfig.local
```

---

## 2. Ajustar email

Editar:

```bash
nano ~/.gitconfig.local
```

---

## 3. Verificar configuración cargada

```bash
git config user.email
```

---

## 4. Ver configuración completa y origen

```bash
git config --list --show-origin
```

---

# Ignorar configuración privada

Agregar al `.gitignore`:

```gitignore
.gitconfig.local
```


---

# Configuración de Visual Studio Code

Configuración de :contentReference[oaicite:0]{index=0} incluida dentro de los dotfiles.

---

# Ubicación de la configuración en macOS

```bash
cd "$HOME/Library/Application Support/Code/User"
```

---

# Agregar configuración al repositorio

## Settings

```bash
config add "$HOME/Library/Application Support/Code/User/settings.json"
```

---

## Keybindings

```bash
config add "$HOME/Library/Application Support/Code/User/keybindings.json"
```

---

# Exportar extensiones instaladas

```bash
code --list-extensions > ~/vscode-extensions.txt
```

Agregar archivo al repositorio:

```bash
config add ~/vscode-extensions.txt
```

---

# Instalar extensiones en otra máquina

```bash
cat ~/vscode-extensions.txt | xargs -L 1 code --install-extension
```

---

# Verificar comando `code`

Si el comando `code` no existe:

```bash
code --version
```

Abrir Visual Studio Code y ejecutar:

```plaintext
Cmd + Shift + P
```

Buscar:

```plaintext
Shell Command: Install 'code' command in PATH
```

---

# Archivos recomendados para versionar

```plaintext
settings.json
keybindings.json
vscode-extensions.txt
```

---

# Archivos NO recomendados para versionar

```plaintext
workspaceStorage
globalStorage
logs
```

---

# Configuración de Homebrew

Configuración y respaldo de paquetes instalados con :contentReference[oaicite:0]{index=0} usando `Brewfile`.

---

# Exportar configuración actual

```bash
brew bundle dump --force
```

Esto genera automáticamente:

```plaintext
~/Brewfile
```

---

# Restaurar paquetes en otra máquina

```bash
brew bundle
```