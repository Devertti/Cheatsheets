# 👤 Usuários e Permissões no Linux

## 🔑 Comandos Essenciais de Usuários

| Comando      | Função                                      | Exemplo                     |
|--------------|---------------------------------------------|-----------------------------|
| `whoami`     | Mostra usuário atual                        | `whoami` → `derick`         |
| `adduser`    | Cria novo usuário                           | `sudo adduser ana`          |
| `su`         | Troca para outro usuário                    | `su - ana`                  |
| `sudo`       | Executa comandos como superusuário          | `sudo apt update`           |
| `passwd`     | Altera senha do usuário                     | `sudo passwd ana`           |
| `id`         | Exibe UID, GID e grupos                     | `id` → `uid=1000(derick)`   |
| `usermod`    | Modifica propriedades do usuário            | `usermod -aG sudo ana`      |
| `userdel`    | Remove usuário                              | `sudo userdel -r ana`       |

---

## 🔒 Sistema de Permissões

### 🧩 Estrutura Básica
```bash
-rwxr-xr-x 1 user group 4096 Aug  5 10:00 arquivo
├─┬─┬─┬─── ┬ ┬──── ┬────── ┬───────────────
│ │ │ │    │ │     │       └── Nome
│ │ │ │    │ │     └────────── Grupo
│ │ │ │    │ └──────────────── Dono (Owner)
│ │ │ │    └────────────────── Tamanho (bytes)
│ └─┴─┴────────────────────── Permissões (10 caracteres)
└──────────────────────────── Tipo:
  - = Arquivo regular
  d = Diretório
  l = Link simbólico
```

### 🔢 Sistema de Tríades
| Posição | Público        | Permissões          |
|---------|----------------|---------------------|
| 2-4     | Dono (Owner)   | `rwx` = Leitura/Escrita/Execução |
| 5-7     | Grupo (Group)  | `r-x` = Leitura/Execução         |
| 8-10    | Outros (Others)| `r-x` = Leitura/Execução         |

---

## 🔢 Sistema Numérico (Octal)

### 📊 Tabela de Valores
| Permissão | Símbolo | Valor | Exemplo Combinado |
|-----------|---------|-------|-------------------|
| Leitura   | r       | 4     | rw- = 4+2 = 6     |
| Escrita   | w       | 2     | r-x = 4+1 = 5     |
| Execução  | x       | 1     | --- = 0           |

### 🎯 Exemplos Comuns
```bash
chmod 755 script.sh    # rwxr-xr-x (Executável público)
chmod 600 secret.txt   # rw------- (Acesso restrito ao dono)
chmod 644 config.conf  # rw-r--r-- (Leitura pública)
chmod 777 temp/        # PERIGOSO! Acesso total a todos
```

---

## 🛠️ Comandos de Controle de Acesso

| Comando | Função                                      | Exemplo de Uso                 |
|---------|---------------------------------------------|--------------------------------|
| `chmod` | Altera permissões                           | `chmod +x script.sh`           |
|         |                                             | `chmod u=rw,g=r,o= file`       |
| `chown` | Altera dono/grupo                           | `chown www-data:www-data site/`|
| `chgrp` | Altera grupo                                | `chgrp devs projeto/`          |
| `umask` | Define permissões padrão para novos arquivos| `umask 022` → perms 644        |

---

## ⚠️ Permissões Especiais (Avançado)

| Permissão | Símbolo | Valor | Função                                           | Exemplo        |
|-----------|---------|-------|--------------------------------------------------|----------------|
| **SUID**  | s       | 4000  | Executa com permissões do dono                   | `chmod u+s /usr/bin/passwd` |
| **SGID**  | s       | 2000  | Herda grupo do diretório pai                     | `chmod g+s /shared/`        |
| **Sticky Bit** | t | 1000 | Só o dono pode apagar seus arquivos              | `chmod +t /tmp/`            |

```bash
# Exemplo combinado:
chmod 4755 programa   # SUID ativado (rwsr-xr-x)
```

---

## 🧪 Laboratório Prático

1. Criar arquivo teste:
   ```bash
   touch teste.txt
   ls -l teste.txt    # Permissões padrão: -rw-r--r--
   ```

2. Restringir acesso:
   ```bash
   chmod 700 teste.txt
   ls -l              # Agora: -rwx------
   ```

3. Mudar proprietário:
   ```bash
   sudo chown root:root teste.txt
   ```

4. Testar acesso:
   ```bash
   cat teste.txt      # Permitido para dono
   su outro_user -c "cat teste.txt"  # Negado!
   ```

---

## 📚 Resumo Visual de Permissões

```bash
drwxr-xr-t 2 root root 4096 Aug  5 12:00 diretorio/
││││││││││ 
│└┴┴┴┴┴┴┴┴── Permissões (d = diretório)
 │ │ │ └─── Sticky Bit (t)
 │ │ └───── Outros: r-x
 │ └─────── Grupo: r-x
 └───────── Dono: rwx
```

> **Dica de Segurança:** Nunca use `chmod 777`! Prefira grupos de usuários para compartilhamento seguro.

## ✨ Melhorias Implementadas:

1. **Organização Hierárquica**
   - Separação clara entre usuários e permissões
   - Tabelas comparativas com exemplos práticos
   - Fluxo lógico do básico ao avançado

2. **Visualização Didática**
   - Diagramas explicativos da estrutura de permissões
   - Sistema de cores e símbolos para diferentes níveis de acesso
   - Exemplos numéricos e simbólicos lado a lado

3. **Elementos Práticos**
   - Laboratório passo-a-passo para testar conceitos
   - Alertas de segurança para práticas perigosas
   - Dicas profissionais de configuração segura

4. **Otimização para GitHub**
   - Sintaxe Markdown validada
   - Destaques de código com realce de sintaxe
   - Ícones visuais para categorização rápida
