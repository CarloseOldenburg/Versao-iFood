## ⚙️ Funcionalidades

- 📥 Baixa e instala o `vsd-launcher` (ferramenta de utilitários para manutenção).
- 🧹 Remove versões antigas dos módulos `vsd-payment` e `pinpad-server`.
- 📦 Baixa as versões mais recentes de:
  - `vs-os-interface` 
  - `pinpad-server` 
  - `vsd-payment` 
- 🛠 Realiza a instalação dos pacotes `.deb` via `dpkg`.
- 📄 Gera log de instalação no arquivo `install_log.txt`.
- 🔁 Reinicia o sistema automaticamente ao final do processo.

---

## 📥 Instalação

Execute o script diretamente com o comando:

```bash
sudo wget --inet4-only -O- https://raw.githubusercontent.com/CarloseOldenburg/Versao-iFood/refs/heads/main/versao-ifood | bash
````

---

## 🧱 Pré-requisitos

* Distribuição baseada em Debian (ex: Ubuntu)
* Permissões de superusuário (`sudo`)
* Internet ativa com acesso via IPv4
* Ferramentas:

  * `wget`
  * `dpkg`
  * `apt`

---

## 📂 Estrutura do Script

### 1. Instalação do `vsd-launcher`

```bash
wget https://raw.githubusercontent.com/wilker-santos/VSDImplantUpdater/main/vsd-launcher.sh
chmod 755 vsd-launcher
mv vsd-launcher /usr/bin/
```

### 2. Limpeza de tokens

```bash
vsd-launcher --clear-token
```

### 3. Remoção de módulos antigos

```bash
apt purge -y vsd-payment
apt purge -y pinpad-server
rm -rf ~/.pinpad_server
rm -f ~/DesktopPlugin.db
```

### 4. Instalação dos novos módulos

```bash
dpkg -i vs-os-interface_2.24.0_amd64.deb
dpkg -i pinpad-server-installer_linux_3.10.0-beta.deb
dpkg -i vsd-payment_1.2.1_amd64.deb
```

---

## 🚨 Avisos

* O script força um **reboot do sistema ao final**, com contagem regressiva.
* Toda a execução é **registrada no arquivo `install_log.txt`** no diretório atual.
* O script usa `set -e`, ou seja, **interrompe a execução ao primeiro erro** crítico.

---

## 👨‍💻 Suporte

Para dúvidas, melhorias ou contribuições, entre em contato com o mantenedor ou abra uma issue no repositório:

* [GitHub - Carlos Eduardo Oldenburg](https://github.com/CarloseOldenburg)

---

## 📜 Licença

Distribuído sob licença livre para uso interno corporativo e manutenção de terminais com sistemas VideoSoft.

