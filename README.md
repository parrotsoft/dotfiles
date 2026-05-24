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
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
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
echo "alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'" >> $HOME/.zshrc
```

### Bash

```bash
echo "alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'" >> $HOME/.bashrc
```

---

## 5. Ignorar el repositorio bare

```bash
echo ".cfg" >> $HOME/.gitignore
```

---

## 6. Agregar archivos

```bash
config add .gitignore
config add .zshrc
config add .gitconfig
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
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
```

---

## 3. Ignorar el repositorio bare

```bash
echo ".cfg" >> $HOME/.gitignore
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
echo "alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'" >> $HOME/.zshrc
```

### Bash

```bash
echo "alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'" >> $HOME/.bashrc
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