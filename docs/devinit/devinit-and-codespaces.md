---
title: devinit e GitHub Codespaces
description: Informazioni su come personalizzare un codespace per Visual Studio usando devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 5697237c1bce719a4658e84435db0426f363f746
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005538"
---
# <a name="devinit-and-github-codespaces"></a>devinit e GitHub Codespaces

devinit è un ottimo complimento per i [codespace di GitHub](https://github.com/features/codespaces) e il devinit può essere usato per ottenere una configurazione dello spazio di codebase, in modo che i collaboratori possano creare, eseguire ed eseguire il debug immediatamente.

Per l'integrazione con gli spazi dei codebase di GitHub, `devinit` deve essere chiamato da `postCreateCommand` definito in un `.devcontainer.json` file inserito nella radice del repository. Le stringhe in `postCreateCommand` vengono eseguite nella shell predefinita, dopo la clonazione del repository nello spazio dei valori. Per altre informazioni, vedere `postCreateCommand` la [documentazione di personalizzazione](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project)di GitHub codespaces. Per aggiungere il `devinit` comando, è possibile aggiungere `devinit init` a `postCreateCommand` come illustrato negli esempi seguenti.

È anche possibile eseguire `devinit init -f <path to .devinit.json>` dal terminale integrato di Visual Studio dopo essersi connessi al codespace.

## <a name="examples"></a>Esempi

### <a name="with-a-devinitjson-file"></a>Con un .devinit.jssu file
In questo esempio, il _.devcontainer.js_ nel file seguente viene inserito nella radice del repository insieme al _.devinit.jssu_ file. I file possono essere inseriti anche in una directory con _estensione devcontainer_ .

```json
{
  "postCreateCommand": "devinit init"
}
```

```json
{
  "postCreateCommand": ["<some other command>", "devinit init"]
}
```

### <a name="as-commands"></a>Come comandi
In questo esempio _.devcontainer.js_ nel file seguente viene inserito nella radice del repository e `devinit run` viene chiamato a livello di codice per eseguire uno strumento  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>Da un prompt dei terminali

Quando la directory di lavoro corrente contiene un _.devinit.jssu_ file.

```console
> devinit init
```

Quando il _.devinit.js_ si trova in un'altra directory.

```console
> devinit init -f path/to/.devinit.json
```
