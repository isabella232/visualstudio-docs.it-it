---
title: Esercitazione
description: Esercitazione per devinilt.
ms.date: 11/18/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 32d407c4803c2b50276145a2c9a66c2c501f05ab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874420"
---
# <a name="tutorial"></a>Esercitazione

In questa esercitazione verrà illustrata la configurazione del [repository eShopOnWeb](https://github.com/andysterland/eShopOnWeb) con i devinit e i codespace. In questa esercitazione si presuppone che devinit sia già disponibile, come descritto nella [pagina](getting-started-with-devinit.md)introduttiva.

## <a name="step-1-determining-setup-steps"></a>Passaggio 1: determinazione delle procedure di installazione

Come indicato nella [pagina](getting-started-with-devinit.md)introduttiva, il primo passaggio consiste sempre nel determinare le dipendenze e i passaggi di configurazione del progetto. Questa operazione può variare in base al progetto specifico, ma è necessario prendere in considerazione alcune domande:

- Da quali Runtime o SDK dipende il progetto?
- Il progetto richiede tutti i pacchetti (ad esempio, da cioccolato)?
- Il processo di installazione richiede l'esecuzione di azioni, ad esempio l'esecuzione di uno script.
- Il progetto ha dipendenze implicite da qualsiasi elemento installato insieme a Visual Studio?
  - In tal caso, è consigliabile includere anche questi nel programma di installazione di devinit. In questo modo, è possibile evitare l'accoppiamento all'installazione di Visual Studio.

Uno dei modi migliori per determinare queste informazioni consiste nell'esplorare le procedure di configurazione manuale attualmente disponibili per il repository. Per eShopOnWeb, è necessario gestire alcuni aspetti:

- Installazione della versione più recente del .NET Core SDK
- Installazione della versione più recente dell'interfaccia della riga di comando di .NET Entity Framework Core Tools
- Installazione di SQL Server 2019 Express
- Uso dell'interfaccia della riga di comando di .NET Entity Framework per aggiornare il database locale alla migrazione più recente

Si esaminerà quindi come eseguire tutte queste procedure nel contesto di devinit.

## <a name="step-2-the-devinitjson"></a>Passaggio 2: il .devinit.js

Prima di tutto, è necessario creare un [.devinit.jssul file](devinit-json.md) e inserirlo nella radice del repository. In questo file sarà inclusa una serie di passaggi che verranno eseguiti successivamente come parte di un `devinit init` comando. Per determinare gli elementi che devono essere inclusi nel `.devinit.json` file, è possibile eseguire l'elenco dei passaggi di configurazione e confrontarli con l'elenco degli [strumenti devinit](devinit-tool-list.md). Ora è possibile procedere con i passaggi di configurazione descritti in precedenza.

| Passaggio                                                              | È possibile gestire questa operazione per noi?                                                                        |
| :---------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------  |
| Installare la .NET Core SDK più recente                                      | **Sì**. È possibile usare lo [ `require-dotnetcoresdk` strumento](tool-require-dotnetcoresdk.md)                  |
| Installare l'interfaccia della riga di comando di .NET Entity Framework Core Tools                      | **Sì**. È possibile usare lo [ `dotnet-toolinstall` strumento](tool-dotnet-toolinstall.md)                        |
| Installare SQL Server 2019 Express                                   | **Sì**. È possibile usare lo [ `choco-install` strumento](tool-choco-install.md)                                  |
| Aggiornare il database locale con .NET Entity Framework                 | **No**, ma questa operazione viene comunque eseguita combinando devinit con uno script.                               |

Ora che è stato capito, iniziamo con una base `.devinit.json` . Verrà incluso un riferimento allo [ `.devinit.json` schema](https://json.schemastore.org/devinit.schema-2.0)e una `run` sezione vuota:

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": []
}
```

Verranno ora aggiunti alcuni strumenti.

In primo luogo, verrà aggiunto [`require-dotnetcoresdk`](tool-require-dotnetcoresdk.md) . Dalla documentazione di questo strumento, è possibile notare che il comportamento predefinito prevede l'installazione della versione più recente dell'SDK. Questo è esattamente ciò che vogliamo, quindi aggiungiamo al nostro `.devinit.json` :

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    }
  ]
}
```

In secondo luogo, si aggiungerà [`dotnet-toolinstall`](tool-dotnet-toolinstall.md) per installare lo `dotnet-ef` strumento a livello globale. Dalla documentazione si noterà che è possibile usare il `input` campo per specificare il nome dello strumento e il `additionalOptions` campo per specificare l'ambito globale:

```json
{
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    },
    {
      "comments": "Install latest version of the .NET Entity Framework Core Tools CLI.",
      "tool": "dotnet-toolinstall",
      "input": "dotnet-ef",
      "additionalOptions": "--global"
    }
  ]
}
```

Infine, aggiungeremo [`choco-install`](tool-choco-install.md) per installare il `sql-server-express` pacchetto.

```json
{
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    },
    {
      "comments": "Install latest version of the .NET Entity Framework Core Tools CLI.",
      "tool": "dotnet-toolinstall",
      "input": "dotnet-ef",
      "additionalOptions": "--global"
    },
    {
      "comments": "Install SQL Server 2019 Express",
      "tool": "choco-install",
      "input": "sql-server-express"
    }
  ]
}
```

Ora che il nostro `.devinit.json` è completo, possiamo lavorare a uno script di configurazione che eseguirà l'esecuzione di devinit e aggiornerà il database locale.

## <a name="step-3-the-setup-script"></a>Passaggio 3: script di installazione

Per gestire sia l'esecuzione di devinit che l'aggiornamento del database locale, verrà creato uno script che esegue i comandi necessari. Viene ora creato uno script di PowerShell vuoto nella radice del repository, denominato `PostCloneSetup.ps1` . Prima di tutto, verrà aggiunta una chiamata a `devinit init` :

```powershell
devinit init
```

Quando viene eseguito, `devinit init` eseguirà tutti gli strumenti definiti nella `run` sezione di `.devinit.json` .

Infine, si vuole richiamare `dotnet ef database update` per l'aggiornamento del database locale:

```powershell
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

Ora che lo script di installazione è stato completato, è necessario aggiungere un `.devcontainer.json` file che lo eseguirà durante l'installazione dello spazio dei file.

## <a name="step-4-the-devcontainerjson"></a>Passaggio 4: .devcontainer.js

Per assicurarsi che lo script di configurazione venga eseguito durante la creazione del nostro codespace, verrà usato un `.devcontainer.json` file. Analogamente agli altri file, questa deve essere inserita nella radice del repository.

Nel `.devcontainer.json` file è sufficiente chiamare lo script di installazione come parte di `postCreateCommand` . Questa operazione verrà eseguita come parte del processo di creazione codespace:

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```

Ecco fatto!

## <a name="step-5-trying-it-out"></a>Passaggio 5: prova

Ora che sono state apportate le procedure di installazione, provare a eseguire questa operazione in un codespace attivo usando il [repository reale](https://github.com/andysterland/eShopOnWeb).

In primo luogo, verrà creato un codespace con Visual Studio:

:::image type="content" source="media/eshoponweb-github-codespaces-prompt.png" alt-text="Creazione di un codespace":::

Una volta avviata la creazione di codespace, è possibile controllare lo stato di avanzamento del processo di configurazione in `C:\.vsonline\.vsoshared\vmTerminal.dat` :

:::image type="content" source="media/eshoponweb-watching-progress.png" alt-text="Visualizzazione dello stato di avanzamento dell'installazione":::

Al termine, eseguire l'app tramite `Web.csproj` per verificare che tutto funzioni correttamente:

:::image type="content" source="media/eshoponweb-csproj.png" alt-text="Esecuzione del progetto":::

Dopo che l'app è stata compilata e avviata, è possibile visualizzare il negozio nel Web browser:

:::image type="content" source="media/eshoponweb-live.png" alt-text="Visualizzazione del sito":::

Quindi, il processo di installazione funzionava correttamente e ora è possibile sviluppare il progetto eShopOnWeb.
