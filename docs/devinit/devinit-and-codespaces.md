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
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

devinit è un complemento ideale per [GitHub Codespaces](https://github.com/features/codespaces) e devinit può essere usato per ottenere una configurazione dello spazio di codice in modo che i collaboratori possano compilare, eseguire ed eseguire il debug immediatamente.

> [!IMPORTANT]
> Prima di integrare devinit con il codespace, è necessario assicurarsi di avere un `.devinit.json` file che definisce le dipendenze. Per altre informazioni su come creare un `.devinit.json` oggetto , vedere la documentazione [introduttiva](getting-started-with-devinit.md).

All'interno di GitHub Codespace, l'applicazione viene compilata ed eseguita nel cloud. Essere nel cloud significa che l'applicazione non ha accesso alle risorse locali nei computer. Sono inclusi strumenti o programmi installati in locale. Se l'applicazione richiede l'installazione o la configurazione di dipendenze a livello di sistema, è necessario eseguire questa operazione in ogni spazio di codice. Il modo più semplice per ottenere questo risultato è usare un `.devinit.json` file.

Per assicurarsi che sia stato creato uno spazio di codice con le dipendenze necessarie per l'applicazione, è necessario eseguire quando viene creato `devinit` il codespace. Questa operazione può essere eseguita `devinit init` chiamando da definito in un file inserito nella radice del `postCreateCommand` `.devcontainer.json` repository. Le stringhe in `postCreateCommand` vengono eseguite nella shell predefinita, dopo che il repo è stato clonato nello spazio di codice. Per altre informazioni, vedere `postCreateCommand` la documentazione sulla personalizzazione GitHub Codespaces . [](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project) Per aggiungere il `devinit` comando , è possibile aggiungere a , come illustrato negli esempi `devinit init` `postCreateCommand` seguenti.

È anche possibile eseguire `devinit init -f <path to .devinit.json>` dall'Visual Studio terminale integrato dopo aver eseguito la connessione al codespace.

## <a name="examples"></a>Esempio

In entrambi gli esempi seguenti, `.devinit.json` si trova nella radice del repository insieme a `.devcontainer.json` .

### <a name="with-a-devcontainerjson-file"></a>Con un .devcontainer.jsnel file

In questo esempio il `.devcontainer.json` file seguente viene inserito nella radice del repo insieme al file `.devinit.json` . I file possono anche essere inseriti in una `.devcontainer` directory.

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

Altri esempi di uso di devinit sono disponibili nella documentazione e in [](https://github.com/microsoft/devinit-example-nodejs) GitHub nell'esempio [.NET Core](https://github.com/microsoft/devinit-example-dotnet-core) eNode.js repository di esempio. [](sample-all-tool.md)

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
