# 🔐 PS.Sudo — PeekSecurity

> Wrapper sudo moderno para Termux — compatível com Magisk, KernelSU e APatch.

---

## 📖 Sobre

O **PS.Sudo** é um wrapper de acesso root para o Termux, reescrito para funcionar nos dispositivos Android modernos (Android 10+).

O `sudo` original do Termux dependia de `remount /system` e caminhos de Magisk antigo — o que não funciona mais na maioria dos dispositivos hoje. O PS.Sudo resolve isso com uma detecção inteligente do `su` disponível, sem precisar remontar partições do sistema.

---

## 📱 Compatibilidade

| Root Manager | Suporte |
|---|---|
| Magisk (moderno) | ✅ |
| KernelSU | ✅ |
| APatch | ✅ |
| Magisk (legado) | ✅ |
| Sem root | ❌ |

**Android:** 8.0+  
**Termux:** Qualquer versão atual (F-Droid recomendado)

---

## 🚀 Instalação

Clone o repositório:

```bash
git clone https://github.com/PSecurity/ps.sudo
```

Entre na pasta:

```bash
cd ps.sudo
```

Instale o script no PATH do Termux:

```bash
cp sudo $PREFIX/bin/sudo
chmod +x $PREFIX/bin/sudo
```

---

## 💡 Uso

```bash
sudo <comando>       # Executa comando como root
sudo su              # Abre shell root interativo
sudo --check         # Verifica se root está funcionando
sudo --info          # Mostra informações do ambiente root
```

### Exemplos

```bash
# Verificar se o root está ativo e funcional
sudo --check

# Ver qual gerenciador de root está sendo usado
sudo --info

# Abrir shell root
sudo su

# Executar nmap com root (necessário para SYN scan)
sudo nmap -sS 192.168.1.1

# Ver arquivos protegidos
sudo ls /data/data
```

---

## ⚙️ Como funciona

O PS.Sudo detecta automaticamente o binário `su` disponível, nessa ordem de prioridade:

1. `su` no PATH (Magisk moderno)
2. `/data/adb/ksu/bin/su` (KernelSU)
3. `/data/adb/ap/bin/su` (APatch)
4. Caminhos legados (`/sbin/su`, `/system/xbin/su`, etc.)

Após localizar o `su`, executa o comando herdando o PATH e as variáveis do Termux — sem precisar remontar o sistema.

---

## 🔍 Flags disponíveis

| Flag | Descrição |
|---|---|
| `--check` | Testa se root está disponível e funcional |
| `--info` | Exibe detalhes do ambiente root (su, UID, kernel) |
| `--help` | Mostra instruções de uso |
| `su` | Abre shell root interativo com bash do Termux |

---

## ⚠️ Requisitos

- Dispositivo com root ativo (Magisk, KernelSU ou APatch)
- Permissão de root concedida ao Termux no gerenciador de root
- Termux instalado via F-Droid (recomendado)

> **Atenção:** Este script não faz root no dispositivo. Ele apenas facilita o uso do root já existente dentro do Termux.

---

## 🧩 Parte do PS.Toolkit

O PS.Sudo faz parte do **PS.Toolkit**, o toolkit central da PeekSecurity para Termux e Kali Linux.

```bash
git clone https://github.com/PSecurity/ps.toolkit
```

---

## 👨‍💻 Autor

**PeekSecurity** — Peek  
🎵 TikTok: [@PeekSecurity](https://www.tiktok.com/@peeksecurity)  
📺 YouTube: [@PeekSecurity](https://m.youtube.com/channel/UC-EKtzSnSUZ8b0CgyUY-hvw)  
🌐 Blog: [psecurity.github.io/PSecurity](https://psecurity.github.io/PSecurity)  
📝 WordPress: [peeksecurity.wordpress.com](https://peeksecurity.wordpress.com)

---

## 📜 Licença

Este projeto está sob a licença Apache 2.0.

---

> ⚠️ Use apenas em dispositivos que você possui e tem autorização. Este script é destinado a fins educacionais e de desenvolvimento pessoal.
