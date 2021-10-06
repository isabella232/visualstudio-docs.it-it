---
title: JavaScript e TypeScript in Visual Studio 2022
description: Informazioni su Visual Studio 2022 offre un supporto integrato per lo sviluppo JavaScript, sia tramite JavaScript direttamente che con il linguaggio di programmazione TypeScript.
titleSuffix: ''
ms.date: 09/27/2021
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2022'
ms.openlocfilehash: 9b4ff4d4f0e345cd9cb69c98355d929f6209da09
ms.sourcegitcommit: d63ba1eff845d41ca095efb14b499ea96c4b6eba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/06/2021
ms.locfileid: "129561074"
---
# <a name="javascript-and-typescript-in-visual-studio-2022"></a>JavaScript e TypeScript in Visual Studio 2022

## <a name="overview"></a>Panoramica

Visual Studio 2022 offre un supporto integrato per lo sviluppo JavaScript, sia tramite JavaScript diretto che con il linguaggio di programmazione [TypeScript](http://www.typescriptlang.org/), sviluppato per offrire un'esperienza di sviluppo JavaScript più produttiva e piacevole, soprattutto quando si sviluppano progetti su larga scala. È possibile scrivere codice JavaScript o TypeScript in Visual Studio per molti tipi di applicazioni e servizi. 

## <a name="javascript-language-service"></a>JavaScript Language Service 

L'esperienza JavaScript in Visual Studio 2022 è basata sullo stesso motore che fornisce il supporto TypeScript. Questo motore offre supporto, arricchimento e integrazione delle funzionalità immediatamente disponibili. 

L'opzione per ripristinare il servizio di linguaggio JavaScript legacy non è più disponibile. Gli utenti hanno il nuovo servizio di linguaggio JavaScript predefinito. Il nuovo servizio di linguaggio si basa esclusivamente sul servizio di linguaggio TypeScript, supportato dall'analisi statica. Questo servizio consente di offrire strumenti migliori, in modo che il codice JavaScript possa trarre vantaggio da IntelliSense più ricco in base alle definizioni dei tipi. Il nuovo servizio è leggero e utilizza meno memoria rispetto al servizio legacy, offrendo agli utenti prestazioni migliori a seconda delle dimensioni del codice. Sono state anche migliorate le prestazioni del servizio di linguaggio per gestire progetti di grandi dimensioni. 

## <a name="typescript-support"></a>Supporto di TypeScript 

Per impostazione predefinita, Visual Studio 2022 fornisce il supporto del linguaggio per i file JavaScript e TypeScript per alimentare IntelliSense senza alcuna configurazione di progetto specifica.  

Per la compilazione di TypeScript, Visual Studio la flessibilità necessaria per scegliere la versione di TypeScript da usare per ogni progetto. 

Negli MSBuild di compilazione, il pacchetto [NuGet TypeScript](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) è il metodo consigliato per aggiungere il supporto della compilazione TypeScript al progetto. Visual Studio sarà possibile aggiungere questo pacchetto la prima volta che si aggiunge un file TypeScript al progetto. Questo pacchetto è disponibile anche in qualsiasi momento tramite gestione NuGet pacchetti. Quando si NuGet pacchetto, verrà usata la versione del servizio di linguaggio corrispondente per il supporto linguistico nel progetto. Nota: la versione minima supportata di questo pacchetto è 3.6. 

I progetti configurati per npm possono specificare la propria versione del servizio di linguaggio TypeScript aggiungendo il pacchetto [npm TypeScript](https://www.npmjs.com/package/typescript). È possibile specificare la versione usando npm manager nei progetti supportati. Nota: la versione minima supportata di questo pacchetto è 2.1.

Il TypeScript SDK è stato deprecato in Visual Studio 2022. I progetti esistenti che si basano sull'SDK devono essere aggiornati a usando il NuGet pacchetto. Per i progetti che non possono essere aggiornati immediatamente, l'SDK è ancora disponibile in [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-442) e come componente facoltativo nel Visual Studio di installazione. 

> [!TIP] 
> Per i progetti sviluppati Visual Studio 2022, è necessario usare il NuGet TypeScript o il pacchetto npm TypeScript per una maggiore portabilità tra piattaforme e ambienti diversi. Per altre informazioni, vedere [Compilare codice TypeScript usando NuGet](../javascript/compile-typescript-code-nuget.md)   e [Compilare codice TypeScript con tsc](../javascript/compile-typescript-code-npm.md). 

## <a name="project-templates"></a>Modelli di progetto 

A partire da Visual Studio 2022, è disponibile un nuovo tipo di progetto JavaScript/TypeScript (con estensione esproj) che consente di creare progetti Angular, React e Vue autonomi in Visual Studio. Questi progetti front-end vengono creati usando gli strumenti dell'interfaccia della riga di comando del framework installati nel computer locale, quindi la versione del modello dipende dall'utente.  

All'interno di questi nuovi progetti è possibile eseguire unit test JavaScript e TypeScript, aggiungere e connettere facilmente progetti api ASP.NET Core e scaricare i moduli npm usando npm manager. Per iniziare, vedere alcune guide introduttive ed esercitazioni. Per altre informazioni, è possibile leggerle in questo [post di blog.](https://devblogs.microsoft.com/visualstudio/the-new-javascript-typescript-experience-in-vs-2022-preview-3/)