---
title: JavaScript e TypeScript in Visual Studio 2019
description: Informazioni su Visual Studio 2019 offre supporto rtf per lo sviluppo JavaScript, sia tramite JavaScript direttamente che con il linguaggio di programmazione TypeScript.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4a826460ade1a771fd8361bb91345dd7bbf19455d8046dfe0fe520e07cdcca6d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370931"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript e TypeScript in Visual Studio 2019

## <a name="overview"></a>Panoramica

Visual Studio 2019 offre supporto avanzato per lo sviluppo in JavaScript, sia usando JavaScript direttamente che tramite il [linguaggio di programmazione TypeScript](http://www.typescriptlang.org/), che è stato sviluppato per offrire un'esperienza di sviluppo JavaScript più produttiva e piacevole, in particolare per lo sviluppo di progetti su larga scala. È possibile scrivere codice JavaScript o TypeScript in Visual Studio per molti tipi di applicazioni e servizi.

## <a name="javascript-language-service"></a>JavaScript Language Service

L'esperienza JavaScript in Visual Studio 2019 si basa sullo stesso motore che fornisce il supporto di TypeScript. Ciò consente supporto delle funzionalità, completezza e integrazione migliori, direttamente nella versione predefinita.

L'opzione per ripristinare il servizio di linguaggio JavaScript legacy non è più disponibile. Il servizio di linguaggio JavaScript è ora disponibile per impostazione predefinita. Il nuovo servizio di linguaggio si basa esclusivamente sul servizio di linguaggio TypeScript, supportato dall'analisi statica. Ciò consente di mettere a disposizione strumenti migliori, in modo che il codice JavaScript possa trarre vantaggio da un'esecuzione di IntelliSense più completa in base alle definizioni dei tipi. Il nuovo servizio è leggero e utilizza meno memoria rispetto al servizio legacy, offrendo agli utenti prestazioni migliori a seconda delle dimensioni del codice. Sono state anche migliorate le prestazioni del servizio di linguaggio per gestire progetti di grandi dimensioni.

## <a name="typescript-support"></a>Supporto di TypeScript

Visual Studio 2019 offre diverse opzioni per l'integrazione della compilazione TypeScript nel progetto:

* TypeScript [NuGet pacchetto](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). Quando si installa il pacchetto NuGet per TypeScript 3.2 o versione successiva nel progetto, la versione corrispondente del servizio di linguaggio TypeScript viene caricata nell'editor.
* Pacchetto [npm TypeScript](https://www.npmjs.com/package/typescript). Quando il pacchetto npm per TypeScript 2.1 o versione successiva è installato nel progetto, la versione corrispondente del servizio di linguaggio TypeScript viene caricata nell'editor.
* TypeScript SDK, disponibile per impostazione predefinita nel programma di installazione di Visual Studio, nonché come download dell'SDK autonomo da [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-395).

> [!TIP]
> Per i progetti sviluppati Visual Studio 2019, si consiglia di usare typeScript NuGet o il pacchetto npm TypeScript per una maggiore portabilità tra piattaforme e ambienti diversi. Per altre informazioni, vedere [Compilare codice TypeScript usando NuGet](../javascript/compile-typescript-code-nuget.md) [e Compilare codice TypeScript con tsc.](../javascript/compile-typescript-code-npm.md)

## <a name="projects"></a>Progetti

Le app UWP JavaScript non sono più supportate in Visual Studio 2019. Non è possibile creare o aprire progetti UWP JavaScript (file con estensione *jsproj*). Per altre informazioni, vedere la documentazione sulla [ creazione delle app Web progressive](/microsoft-edge/progressive-web-apps-chromium) eseguite in modo corretto in Windows.
