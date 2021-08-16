---
title: devinit e GitHub Codespaces
description: Informazioni su come personalizzare uno spazio di codice per Visual Studio usando devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 377eb08e7255775b9d4bf187b0eb79c53499fe412b37c13ad6f1269d5a453c88
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343394"
---
# <a name="devinit-and-github-codespaces"></a>devinit e GitHub Codespaces

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

devinit è un ottimo complemento GitHub [Codespaces](https://github.com/features/codespaces) e devinit può essere usato per ottenere una configurazione dello spazio di codice in modo che i collaboratori possano compilare, eseguire ed eseguire il debug immediatamente.

> [!IMPORTANT]
> Prima di integrare devinit con lo spazio di codice, è necessario assicurarsi di avere un file che definisce `.devinit.json` le dipendenze. Per altre informazioni su come creare un `.devinit.json` oggetto , vedere la documentazione [introduttiva](getting-started-with-devinit.md).

All'interno di GitHub Codespace, l'applicazione viene compilata ed eseguita nel cloud. Essere nel cloud significa che l'applicazione non ha accesso alle risorse locali nei computer. Sono inclusi gli strumenti o i programmi installati in locale. Se l'applicazione richiede l'installazione o la configurazione di dipendenze a livello di sistema, deve essere eseguita in ogni spazio di codice. Il modo più semplice per ottenere questo risultato è usare un `.devinit.json` file.

Per assicurarsi che uno spazio di codice sia creato con le dipendenze necessarie per l'applicazione, deve essere eseguito quando viene creato `devinit` lo spazio di codice. Questa operazione può essere eseguita chiamando `devinit init` dalla classe definita in un file inserito nella radice del `postCreateCommand` `.devcontainer.json` repository. Le stringhe in `postCreateCommand` vengono eseguite nella shell predefinita, dopo che il repo è stato clonato nello spazio di codice. Per altre informazioni, vedere `postCreateCommand` la documentazione sulla personalizzazione GitHub Codespaces . [](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project) Per aggiungere il `devinit` comando , è possibile aggiungere a come illustrato negli esempi `devinit init` `postCreateCommand` seguenti.

È anche possibile eseguire dal terminale Visual Studio integrato una volta `devinit init -f <path to .devinit.json>` connessi al codespace.

## <a name="examples"></a>Esempio

In entrambi gli esempi seguenti si `.devinit.json` trova nella radice del repository insieme a `.devcontainer.json` .

### <a name="with-a-devcontainerjson-file"></a>Con un .devcontainer.jssu file

In questo esempio il `.devcontainer.json` file seguente viene inserito nella radice del repo insieme al `.devinit.json` file. I file possono anche essere inseriti in una `.devcontainer` directory.

```json
{
  "postCreateCommand": "devinit init"
}
```

Quando si `.devinit.json` trova in un'altra directory, è possibile usare il flag -f.

```json
{
  "postCreateCommand": "devinit init -f path\\to\\.devinit.json"
}

```

```json
{
  "postCreateCommand": ["<some other command>", "devinit init"]
}
```

Altri esempi di uso di devinit sono disponibili nella documentazione e GitHub [](https://github.com/microsoft/devinit-example-nodejs) nell'esempio [.NET Core](https://github.com/microsoft/devinit-example-dotnet-core) eNode.js repository di esempio. [](sample-all-tool.md)

### <a name="as-commands"></a>Come comandi

In questo esempio il file seguente viene inserito nella radice del repo e viene chiamato direttamente dalla riga di comando `.devcontainer.json` per eseguire un singolo `devinit run` strumento.  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>Da un prompt del terminale

Quando la directory di lavoro corrente contiene un `.devinit.json` file.

```console
devinit init
```

Quando si `.devinit.json` trova in un'altra directory.

```console
devinit init -f path/to/.devinit.json
```
