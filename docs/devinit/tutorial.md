---
title: Esercitazione
description: Esercitazione per devinit.
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
ms.openlocfilehash: 18703ca0b438bcb0724bb8b94002a964366003c2cbe1b60fedf998e580e9d95b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403542"
---
# <a name="tutorial"></a>Esercitazione

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

In questa esercitazione verrà esaminata la configurazione del [repository eShopOnWeb](https://github.com/andysterland/eShopOnWeb) con devinit e Codespaces. Questa esercitazione presuppone che devinit sia già disponibile, come descritto nella [pagina introduttiva](getting-started-with-devinit.md).

## <a name="step-1-determining-setup-steps"></a>Passaggio 1: Determinazione dei passaggi di configurazione

Come accennato nella [pagina introduttiva,](getting-started-with-devinit.md)il primo passaggio consiste sempre nel determinare le dipendenze e i passaggi di configurazione del progetto. Questo può variare in base al progetto specifico, ma è necessario considerare alcune domande:

- Da quali runtime o SDK dipende il progetto?
- Il progetto richiede pacchetti (ad esempio, da Chocolatey)?
- Il processo di installazione richiede azioni da eseguire (ad esempio, l'esecuzione di uno script)?
- Il progetto ha dipendenze implicite da qualsiasi elemento installato insieme Visual Studio?
  - In tal caso, è buona idea includerlo anche nella configurazione devinit. In questo modo, è possibile evitare l'accoppiamento al Visual Studio installazione.

Uno dei modi migliori per determinare queste informazioni è esplorare i passaggi di configurazione manuale attualmente disponibili per il repository. Per eShopOnWeb, è necessario gestire alcuni aspetti:

- Installazione della versione più recente del .NET Core SDK
- Installazione della versione più recente dell'interfaccia della riga di comando di .NET Entity Framework Core Tools
- Installazione di SQL Server 2019 Express
- Uso dell'interfaccia della Entity Framework .NET per aggiornare il database locale alla migrazione più recente

Verrà ora illustrato come eseguire tutte queste attività nel contesto di devinit.

## <a name="step-2-the-devinitjson"></a>Passaggio 2: La .devinit.jsin

Prima di tutto, è necessario creare un [.devinit.jssul file](devinit-json.md) e posizionarlo nella radice del repository. Questo file includerà una serie di passaggi che verranno eseguiti in un secondo momento come parte di un `devinit init` comando. Per determinare cosa includere nel file, è possibile eseguire l'elenco dei passaggi di installazione e confrontare con `.devinit.json` l'elenco degli [strumenti devinit](devinit-tool-list.md). A questo punto, è possibile eseguire la procedura di configurazione descritta in precedenza.

| Passaggio                                                              | Devinit può gestire questo problema?                                                                        |
| :---------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------  |
| Installare la versione .NET Core SDK                                      | **Sì**! È possibile usare lo [ `require-dotnetcoresdk` strumento](tool-require-dotnetcoresdk.md)                  |
| Installare l'interfaccia della riga di comando di .NET Entity Framework Core Tools                      | **Sì**! È possibile usare lo [ `dotnet-toolinstall` strumento](tool-dotnet-toolinstall.md)                        |
| Installare SQL Server 2019 Express                                   | **Sì**! È possibile usare lo [ `choco-install` strumento](tool-choco-install.md)                                  |
| Aggiornare il database locale usando .NET Entity Framework                 | **No,** ma questa operazione viene comunque eseguita combinando devinit con uno script.                               |

Ora che è stato possibile capirlo, si inizierà con una classe di `.devinit.json` base. Verranno inclusi un riferimento allo [ `.devinit.json` schema](https://json.schemastore.org/devinit.schema-2.0)e una sezione `run` vuota:

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": []
}
```

Aggiungere ora alcuni strumenti.

In primo luogo, si [`require-dotnetcoresdk`](tool-require-dotnetcoresdk.md) aggiungerà . Dalla documentazione di tale strumento è possibile vedere che il comportamento predefinito è installare la versione più recente dell'SDK. Questo è esattamente ciò che si vuole, quindi è possibile aggiungerlo a `.devinit.json` :

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

In secondo momento, si [`dotnet-toolinstall`](tool-dotnet-toolinstall.md) aggiungerà per installare lo `dotnet-ef` strumento a livello globale. Nella documentazione è possibile usare il campo per specificare il nome dello strumento e il campo `input` `additionalOptions` per specificare l'ambito globale:

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

Infine, si aggiungerà [`choco-install`](tool-choco-install.md) per installare il `sql-server-express` pacchetto.

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

Ora che è stato completato, è possibile usare uno script di installazione che si occuperà dell'esecuzione `.devinit.json` di devinit e dell'aggiornamento del database locale.

## <a name="step-3-the-setup-script"></a>Passaggio 3: Script di installazione

Per gestire sia l'esecuzione di devinit che l'aggiornamento del database locale, si creerà uno script che esegue i comandi necessari. Verrà ora creato uno script di PowerShell vuoto nella radice del repository, denominato `PostCloneSetup.ps1` . In primo luogo, si aggiungerà una chiamata a `devinit init` :

```powershell
devinit init
```

Quando viene `devinit init` eseguito, eseguirà tutti gli strumenti definiti nella `run` sezione di `.devinit.json` .

Infine, si vuole richiamare per `dotnet ef database update` aggiornare il database locale:

```powershell
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

Ora che lo script di installazione è completo, è necessario aggiungere un `.devcontainer.json` file che lo eseguirà durante l'installazione dello spazio di codice.

## <a name="step-4-the-devcontainerjson"></a>Passaggio 4: Il .devcontainer.jssu

Per assicurarsi che lo script di installazione sia eseguito durante la creazione dello spazio di codice, si userà un `.devcontainer.json` file. Analogamente agli altri file, questo deve essere inserito nella radice del repository.

Nel `.devcontainer.json` file è sufficiente chiamare lo script di installazione come parte di `postCreateCommand` . Questa operazione verrà eseguita come parte del processo di creazione dello spazio di codice:

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```

Ecco fatto!

## <a name="step-5-trying-it-out"></a>Passaggio 5: Provarlo

Ora che i passaggi di configurazione sono stati eserciti, provare questa operazione in uno spazio di codice live usando il [vero e proprio repo](https://github.com/andysterland/eShopOnWeb).

Per prima cosa, si creerà uno spazio di codice usando Visual Studio:

:::image type="content" source="media/eshoponweb-github-codespaces-prompt.png" alt-text="Creazione di uno spazio di codice":::

Dopo aver avviato la creazione dello spazio di codice, è possibile osservare lo stato del processo di installazione in `C:\.vsonline\.vsoshared\vmTerminal.dat` :

:::image type="content" source="media/eshoponweb-watching-progress.png" alt-text="Controllo dello stato di avanzamento dell'installazione":::

Al termine, eseguire l'app tramite per assicurarsi che tutto `Web.csproj` funzioni correttamente:

:::image type="content" source="media/eshoponweb-csproj.png" alt-text="Esecuzione del progetto":::

Dopo la compilazione e l'avvio dell'app, è possibile visualizzare il negozio nel Web browser:

:::image type="content" source="media/eshoponweb-live.png" alt-text="Visualizzazione del sito":::

Il processo di configurazione ha quindi funzionato correttamente ed è ora possibile sviluppare nel progetto eShopOnWeb.
