# turbo-updates

Servidor de atualização do aplicativo **Turbo.Br PRO**.

Aqui moram dois arquivos, servidos pelo GitHub Pages:

- `version.json` — o manifesto que o app lê para saber se existe versão nova
- `turbo-br-pro-<versão>.apk` — o instalador dessa versão

## Como o app usa

Ao abrir, o app lê o `version.json`. Se o `versionCode` de lá for maior que o dele,
mostra o aviso de versão nova, baixa o APK, **confere o `sha256`** e só então abre o
instalador do Android. Se o hash não bater, ele recusa e apaga o arquivo.

O campo `sha256` é obrigatório: desde a versão 0.11.0 o app recusa manifesto sem ele.
É o que impede alguém de trocar o APK no meio do caminho.

## Por que este repositório é público

O GitHub Pages só serve arquivos de repositório público em conta gratuita, e o APK já
era distribuído abertamente antes. O que protege o aplicativo não é o link ser secreto:
é a assinatura digital, conferida pelo próprio app ao abrir.
