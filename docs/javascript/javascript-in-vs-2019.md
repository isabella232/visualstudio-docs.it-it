---
title: JavaScript e TypeScript in Visual Studio 2019
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: df4630182e89dad08360794057bda856ff4d677b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "79549943"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript e TypeScript in Visual Studio 2019

## <a name="overview"></a>Panoramica

Visual Studio 2019 offre supporto avanzato per lo sviluppo in JavaScript, sia usando JavaScript direttamente che tramite il [linguaggio di programmazione TypeScript](http://www.typescriptlang.org/), che è stato sviluppato per offrire un'esperienza di sviluppo JavaScript più produttiva e piacevole, in particolare per lo sviluppo di progetti su larga scala. È possibile scrivere codice JavaScript o TypeScript in Visual Studio per molti tipi di applicazioni e servizi.

## <a name="javascript-language-service"></a>JavaScript Language Service

L'esperienza JavaScript in Visual Studio 2019 si basa sullo stesso motore che fornisce il supporto di TypeScript. Ciò consente supporto delle funzionalità, completezza e integrazione migliori, direttamente nella versione predefinita.

L'opzione per ripristinare il servizio di linguaggio JavaScript legacy non è più disponibile. Il servizio di linguaggio JavaScript è ora disponibile per impostazione predefinita. Il nuovo servizio di linguaggio si basa esclusivamente sul servizio di linguaggio TypeScript, supportato dall'analisi statica. Ciò consente di mettere a disposizione strumenti migliori, in modo che il codice JavaScript possa trarre vantaggio da un'esecuzione di IntelliSense più completa in base alle definizioni dei tipi. Il nuovo servizio è leggero e utilizza meno memoria rispetto al servizio legacy, offrendo agli utenti prestazioni migliori a seconda delle dimensioni del codice. Sono state anche migliorate le prestazioni del servizio di linguaggio per gestire progetti di grandi dimensioni.

## <a name="typescript-support"></a>Supporto di TypeScript

Visual Studio 2019 offre diverse opzioni per l'integrazione della compilazione TypeScript nel progetto:

* [Pacchetto NuGet di TypeScript](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). Quando si installa il pacchetto NuGet per TypeScript 3.2 o versione successiva nel progetto, la versione corrispondente del servizio di linguaggio TypeScript viene caricata nell'editor.
* [Pacchetto npm di TypeScript](https://www.npmjs.com/package/typescript). Quando il pacchetto npm per TypeScript 2.1 o versione successiva è installato nel progetto, la versione corrispondente del servizio di linguaggio TypeScript viene caricata nell'editor.
* TypeScript SDK, disponibile per impostazione predefinita nel programma di installazione di Visual Studio, nonché come download dell'SDK autonomo da [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017).

Per i progetti sviluppati in Visual Studio 2019, si consiglia di usare i pacchetti npm e NuGet di TypeScript per maggiore portabilità in piattaforme e ambienti e diversi.

Un utilizzo comune per il pacchetto NuGet consiste nel compilare TypeScript usando l'interfaccia della riga di comando di .NET Core.One common usage for the NuGet package is to compile TypeScript using the .NET Core CLI. A meno che non si modifichi manualmente il file di progetto per importare destinazioni di compilazione da un'installazione di TypeScript SDK, il pacchetto NuGet è l'unico modo per abilitare la compilazione TypeScript utilizzando i comandi dell'interfaccia della riga di comando di .NET Core, ad `dotnet build` esempio e `dotnet publish`.

## <a name="remove-default-imports-aspnet-core-projects"></a>Rimuovere le importazioni predefinite (ASP.NET progetti core)

Nei progetti meno recenti che utilizzano il formato non di [tipo SDK,](https://docs.microsoft.com/nuget/resources/check-project-format)potrebbe essere necessario rimuovere alcuni elementi del file di progetto.

Se si utilizza il pacchetto NuGet per il supporto MSBuild `Microsoft.TypeScript.Default.props` per `Microsoft.TypeScript.targets`un progetto, il file di progetto non deve importare o . I file vengono importati dal pacchetto NuGet, pertanto includerli separatamente può causare un comportamento imprevisto.

1. Fare clic con il pulsante destro del mouse sul progetto e scegliere **Scarica progetto**.

1. Fare clic con il pulsante destro del mouse sul progetto e scegliere **Modifica \< *nome*\>file di progetto**.

   Viene aperto il file di progetto.

1. Rimuovere i `Microsoft.TypeScript.Default.props` `Microsoft.TypeScript.targets`riferimenti a e .

   Le importazioni da rimuovere sono simili alle seguenti:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```

## <a name="projects"></a>Progetti

Le app UWP JavaScript non sono più supportate in Visual Studio 2019. Non è possibile creare o aprire progetti UWP JavaScript (file con estensione *jsproj*). Per altre informazioni, vedere la documentazione sulla [ creazione delle app Web progressive](/microsoft-edge/progressive-web-apps/get-started) eseguite in modo corretto in Windows.
