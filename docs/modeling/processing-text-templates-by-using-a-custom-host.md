---
title: Elaborazione di modelli di testo tramite un host personalizzato
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e72b279d55cbe11f6232ff1f91c8fee443d9c283
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910935"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Elaborare modelli di testo tramite un host personalizzato

Il *trasformazione del modello di testo* elaborare accetta una *modello di testo* file come input e produce file di testo come output. È possibile chiamare il motore di trasformazione del testo da un'estensione di Visual Studio o da un'applicazione autonoma in esecuzione in un computer in cui è installato Visual Studio. Tuttavia, è necessario specificare una *host di modello testo*. Questa classe connette il modello all'ambiente, trovando risorse quali gli assembly e i file di inclusione e gestendo l'output e i messaggi di errore.

> [!TIP]
> Se si sta scrivendo un pacchetto o un'estensione che viene eseguito all'interno di Visual Studio, è consigliabile utilizzare il servizio di creazione di modelli di testo, invece di scrivere il proprio host. Per altre informazioni, vedere [richiamo di trasformazione del testo in un'estensione VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> Si sconsiglia di utilizzare le trasformazioni del modello di testo nelle applicazioni server. Si sconsiglia di utilizzare le trasformazioni del modello di testo eccetto in un thread singolo. Questo perché il motore del modello di testo riutilizza un solo AppDomain per tradurre, compilare ed eseguire i modelli. Il codice tradotto non è progettato per essere thread-safe. Il motore è progettato per elaborare i file in modo seriale, così come sono in un progetto di Visual Studio in fase di progettazione.
>
> Per le applicazioni in fase di esecuzione, è consigliabile usare i modelli di testo pre-elaborati: vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Se l'applicazione utilizza un set di modelli corretti in fase di compilazione, sarà più facile utilizzare modelli di testo pre-elaborati. È possibile usare questo approccio anche se l'applicazione verrà eseguita in un computer in cui non è installato Visual Studio. Per altre informazioni, vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Eseguire un modello di testo all'interno dell'applicazione

Per eseguire un modello di testo, chiamare il metodo ProcessTemplate di <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 L'applicazione deve trovare e fornire il modello e deve gestire l'output.

 Nel parametro `host`, è necessario fornire una classe che implementa <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Questa viene richiamata dal motore.

 L'host deve essere in grado di registrare errori, risolvere riferimenti agli assembly e ai file di inclusione, fornire un dominio dell'applicazione nel quale il modello possa essere eseguito e possa chiamare il processore adatto per ciascuna direttiva.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> è definito in **Microsoft.VisualStudio.TextTemplating.\*. 0.log dll**, e <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> definito nella **TextTemplating.\*. 0.log dll**.

## <a name="in-this-section"></a>In questa sezione
 [Procedura dettagliata: Creazione di un Host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md) illustra come creare un host del modello di testo personalizzato che rende disponibili di fuori di Visual Studio la funzionalità del modello di testo.

## <a name="reference"></a>Riferimenti
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>

## <a name="related-sections"></a>Sezioni correlate

- [Il processo di trasformazione del modello di testo](../modeling/the-text-template-transformation-process.md) viene descritto il funzionamento di trasformazione del testo, e quali parti è possibile personalizzare.
- [Creazione di processori di direttiva modello di testo T4 personalizzati](../modeling/creating-custom-t4-text-template-directive-processors.md) offre una panoramica del testo processori di direttiva del modello.