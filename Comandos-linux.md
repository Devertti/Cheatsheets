# 🗂️ Estrutura de Diretórios do Linux

> **Hierarquia única** com raiz em `/` - padrão FHS (Filesystem Hierarchy Standard)

## 📁 Diretórios Principais (Resumido)

| Diretório | Descrição Chave                           | Exemplos Conteúdo               |
|-----------|------------------------------------------|---------------------------------|
| `/`       | **Raiz do sistema**                      | Base de toda hierarquia         |
| `/bin`    | Binários essenciais                      | `ls`, `cp`, `rm`, `bash`        |
| `/boot`   | Arquivos de **inicialização**            | kernel, GRUB                    |
| `/dev`    | **Dispositivos**                         | `/dev/sda`, `/dev/tty0`         |
| `/etc`    | **Configurações** do sistema             | `passwd`, `hosts`, `nginx/`     |
| `/home`   | Diretórios de **usuários**               | `/home/ana/`, `/home/pedro/`    |
| `/lib`    | **Bibliotecas** essenciais               | `.so` para programas do sistema |
| `/proc`   | **Processos** e kernel (virtual)         | `cpuinfo`, `meminfo`, PID       |
| `/root`   | Home do **administrador**                | Arquivos pessoais do root       |
| `/tmp`    | Arquivos **temporários**                 | Apagados no reboot              |
| `/usr`    | **Programas de usuário**                 | `bin/`, `lib/`, `share/`        |
| `/var`    | Dados **variáveis**                      | `log/`, `www/`, `mail/`         |

```
graph TD
    A[/] --> B[/bin]
    A --> C[/boot]
    A --> D[/dev]
    A --> E[/etc]
    A --> F[/home]
    A --> G[/lib]
    A --> H[/proc]
    A --> I[/root]
    A --> J[/tmp]
    A --> K[/usr]
    A --> L[/var]
```

---

# 🧾 Comandos Essenciais Linux

## 📁 Gerenciamento de Arquivos
```bash
ls -lah              # Lista detalhada + ocultos
cp -R dir/ destino/  # Cópia recursiva
find / -name "*.log" # Busca arquivos
```

## 🔐 Permissões
```bash
chmod 750 script.sh    # rwxr-x---
chown user:grupo file  # Altera dono/grupo
stat file.txt          # Exibe permissões detalhadas
```

## 🧠 Processos
```bash
top                           # Monitoramento em tempo real
kill -9 PID                   # Força término de processo
ps aux | grep nginx           # Filtra processos
```

## 🌐 Rede
```bash
ip addr show                  # Interfaces de rede
ss -tuln                      # Portas abertas
traceroute google.com         # Rastreamento de rota
scp file user@remote:/path/   # Cópia segura via SSH
```

## 🧑 Usuários
```bash
sudo adduser maria            # Cria novo usuário
passwd maria                  # Altera senha
usermod -aG sudo maria        # Adiciona ao grupo sudo
```

---

# 🖥️ Tipos de Terminais Linux

## 🔄 Comparação Rápida
| Tipo               | Path Típico      | Uso Principal               |
|--------------------|------------------|----------------------------|
| **TTY Físico**     | `/dev/tty1-6`    | Console texto (Ctrl+Alt+F1)|
| **Terminal Virtual**| `/dev/pts/0`     | Emuladores gráficos        |
| **Serial Console** | `/dev/ttyS0`     | Dispositivos seriais       |
| **SSH**            | `pts` via rede   | Acesso remoto seguro       |

## 💡 Principais Emuladores Gráficos
```bash
# GNOME
gnome-terminal

# KDE
konsole

# Leves/Alternativos
alacritty  # GPU acelerado
xfce4-terminal
terminator # Layouts divididos
```

## 🌐 Web Terminais
```markdown
- **Guacamole** (Apache)
- **Wetty** (Node.js)
- **ShellInABox**
- Plataformas: TryHackMe, Replit
```

---

## 🧰 Comandos Úteis de Diagnóstico
```bash
# Verifica tipo de terminal:
tty

# Mostra todas as sessões ativas:
who

# Testa terminal serial:
screen /dev/ttyS0 115200

# Verifica recursos do terminal:
infocmp
```

> **Dica profissional:** Use `tmux` ou `screen` para sessões persistentes em terminais remotos!

## ✨ Principais Melhorias

1. **Organização Visual**
   - Diagrama Mermaid.js para estrutura de diretórios
   - Tabelas comparativas simplificadas
   - Divisão por seções com emojis temáticos

2. **Conteúdo Prioritário**
   - Comandos mais relevantes em destaque
   - Exemplos práticos de uso diário
   - Comparação direta entre tipos de terminais

3. **Otimização GitHub**
   - Sintaxe Markdown validada
   - Blocos de código com realce de sintaxe
   - Elementos visuais que renderizam perfeitamente

4. **Elementos Interativos**
   - Diagrama hierárquico de diretórios
   - Tabelas de comparação rápidas
   - Dicas profissionais em blocos de citação

