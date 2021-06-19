---
title: Elaborazione di modelli di testo tramite un host personalizzato
description: Si apprenderà che il processo di trasformazione del modello di testo accetta un file modello di testo come input e produce un file di testo come output.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a301df6edaf8558ade5c8a297f233b58de6d8f4e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390932"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Elaborare modelli di testo tramite un host personalizzato

Il *processo di trasformazione del modello di* testo accetta un file modello *di* testo come input e produce un file di testo come output. È possibile chiamare il motore di trasformazione del testo da un'estensione Visual Studio o da un'applicazione autonoma in esecuzione in un computer in cui Visual Studio è installato. Tuttavia, è necessario fornire un *host di modelli di testo*. Questa classe connette il modello all'ambiente, trovando risorse quali gli assembly e i file di inclusione e gestendo l'output e i messaggi di errore.

> [!TIP]
> Se si scrive un pacchetto o un'estensione che verrà eseguita all'interno di Visual Studio, è consigliabile usare il servizio di creazione modelli di testo, anziché scrivere un host personalizzato. Per altre informazioni, vedere [Chiamata della trasformazione testo in un'estensione di Visual Studio.](../modeling/invoking-text-transformation-in-a-vs-extension.md)

> [!NOTE]
> Si sconsiglia di utilizzare le trasformazioni del modello di testo nelle applicazioni server. Si sconsiglia di utilizzare le trasformazioni del modello di testo eccetto in un thread singolo. Questo perché il motore del modello di testo riutilizza un solo AppDomain per tradurre, compilare ed eseguire i modelli. Il codice tradotto non è progettato per essere thread-safe. Il motore è progettato per elaborare i file in modo seriale, come si trova in un progetto Visual Studio in fase di progettazione.
>
> Per le applicazioni di run-time, prendere in considerazione l'uso di modelli di testo pre-elaborato: vedere Generazione di testo in fase di esecuzione [con modelli di testo T4.](../modeling/run-time-text-generation-with-t4-text-templates.md)

Se l'applicazione utilizza un set di modelli corretti in fase di compilazione, sarà più facile utilizzare modelli di testo pre-elaborati. È anche possibile usare questo approccio se l'applicazione verrà eseguita in un computer in cui Visual Studio non è installato. Per altre informazioni, vedere Generazione di testo in fase [di esecuzione con modelli di testo T4.](../modeling/run-time-text-generation-with-t4-text-templates.md)

## <a name="execute-a-text-template-in-your-application"></a>Eseguire un modello di testo nell'applicazione

Per eseguire un modello di testo, chiamare il metodo ProcessTemplate di <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 L'applicazione deve trovare e fornire il modello e deve gestire l'output.

 Nel parametro `host` è necessario fornire una classe che implementa [ITextTemplatingEngineHost.](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) Questa viene richiamata dal motore.

 L'host deve essere in grado di registrare errori, risolvere riferimenti agli assembly e ai file di inclusione, fornire un dominio dell'applicazione nel quale il modello possa essere eseguito e possa chiamare il processore adatto per ciascuna direttiva.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> è definito in **Microsoft.VisualStudio.TextTemplating. \*.0.dll** e [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) è definito in **Microsoft.VisualStudio.TextTemplating.Interfaces. \*.0.dll**.

## <a name="in-this-section"></a>Contenuto della sezione
 [Procedura dettagliata: Creazione di un host modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md) Illustra come creare un host del modello di testo personalizzato che rende la funzionalità del modello di testo disponibile all'esterno Visual Studio.

## <a name="reference"></a>Riferimento
 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>Sezioni correlate

- [Il processo di trasformazione modello di testo](../modeling/the-text-template-transformation-process.md) descrive il funzionamento della trasformazione del testo e le parti che è possibile personalizzare.
- [La creazione di processori di direttiva del modello](../modeling/creating-custom-t4-text-template-directive-processors.md) di testo T4 personalizzati offre una panoramica dei processori di direttiva del modello di testo.
