---
title: Elaborazione di modelli di testo tramite un host personalizzato
description: Informazioni che il processo di trasformazione del modello di testo accetta un file modello di testo come input e produce un file di testo come output.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b1a4e4c2177e388db1de0b42fe10d92daa1a3e67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934910"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Elaborare modelli di testo tramite un host personalizzato

Il processo di *trasformazione del modello di testo* accetta un file modello di *testo* come input e produce un file di testo come output. È possibile chiamare il motore di trasformazione del testo da un'estensione di Visual Studio o da un'applicazione autonoma in esecuzione in un computer in cui è installato Visual Studio. Tuttavia, è necessario fornire un *host del modello di testo*. Questa classe connette il modello all'ambiente, trovando risorse quali gli assembly e i file di inclusione e gestendo l'output e i messaggi di errore.

> [!TIP]
> Se si sta scrivendo un pacchetto o un'estensione che verrà eseguita all'interno di Visual Studio, è consigliabile usare il servizio modello di testo, anziché scrivere un host personalizzato. Per altre informazioni, vedere [richiamo della trasformazione del testo in un'estensione di Visual](../modeling/invoking-text-transformation-in-a-vs-extension.md)Studio.

> [!NOTE]
> Si sconsiglia di utilizzare le trasformazioni del modello di testo nelle applicazioni server. Si sconsiglia di utilizzare le trasformazioni del modello di testo eccetto in un thread singolo. Questo perché il motore del modello di testo riutilizza un solo AppDomain per tradurre, compilare ed eseguire i modelli. Il codice tradotto non è progettato per essere thread-safe. Il motore è progettato per elaborare i file in modo seriale, così come sono in un progetto di Visual Studio in fase di progettazione.
>
> Per le applicazioni di run-time, provare a usare modelli di testo pre-elaborati: vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Se l'applicazione utilizza un set di modelli corretti in fase di compilazione, sarà più facile utilizzare modelli di testo pre-elaborati. È anche possibile usare questo approccio se l'applicazione verrà eseguita in un computer in cui non è installato Visual Studio. Per altre informazioni, vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Eseguire un modello di testo nell'applicazione

Per eseguire un modello di testo, chiamare il metodo ProcessTemplate di <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 L'applicazione deve trovare e fornire il modello e deve gestire l'output.

 Nel `host` parametro è necessario fornire una classe che implementi [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Questa viene richiamata dal motore.

 L'host deve essere in grado di registrare errori, risolvere riferimenti agli assembly e ai file di inclusione, fornire un dominio dell'applicazione nel quale il modello possa essere eseguito e possa chiamare il processore adatto per ciascuna direttiva.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> è definito in **Microsoft. VisualStudio. TextTemplating. \*.0.dll** e [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) è definito in **Microsoft. VisualStudio. TextTemplating. Interfaces. \*.0.dll**.

## <a name="in-this-section"></a>Contenuto della sezione
 [Procedura dettagliata: creazione di un host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md) Viene illustrato come creare un host del modello di testo personalizzato che rende disponibile la funzionalità del modello di testo all'esterno di Visual Studio.

## <a name="reference"></a>Riferimento
 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>Sezioni correlate

- [Il processo di trasformazione del modello di testo descrive il funzionamento della trasformazione del](../modeling/the-text-template-transformation-process.md) testo e le parti che è possibile personalizzare.
- [Creazione di processori di direttiva di modelli di testo T4 personalizzati](../modeling/creating-custom-t4-text-template-directive-processors.md) offre una panoramica dei processori di direttiva per i modelli di testo.
