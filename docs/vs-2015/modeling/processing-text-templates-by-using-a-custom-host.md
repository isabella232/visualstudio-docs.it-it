---
title: Elaborazione di modelli di testo tramite un host personalizzato | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1c8f306315ad236843b6fcd5551d9aed13c26a92
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871788"
---
# <a name="processing-text-templates-by-using-a-custom-host"></a>Elaborazione di modelli di testo tramite un host personalizzato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il processo di *trasformazione del modello di testo* accetta un file modello di *testo* come input e produce un file di testo come output. È possibile chiamare il motore di trasformazione del testo da un'estensione [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o da un'applicazione autonoma in esecuzione in un computer nel quale è installato [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Tuttavia, è necessario fornire un *host del modello di testo*. Questa classe connette il modello all'ambiente, trovando risorse quali gli assembly e i file di inclusione e gestendo l'output e i messaggi di errore.

> [!TIP]
> Se si scrive un pacchetto o un'estensione che verrà eseguita in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], anziché scrivere il proprio host, è consigliabile utilizzare il servizio del modello di testo. Per altre informazioni, vedere [richiamo della trasformazione del testo in un'estensione di Visual](../modeling/invoking-text-transformation-in-a-vs-extension.md)Studio.

> [!NOTE]
> Si sconsiglia di utilizzare le trasformazioni del modello di testo nelle applicazioni server. Si sconsiglia di utilizzare le trasformazioni del modello di testo eccetto in un thread singolo. Questo perché il motore del modello di testo riutilizza un solo AppDomain per tradurre, compilare ed eseguire i modelli. Il codice tradotto non è progettato per essere thread-safe. Il motore viene progettato per elaborare file in serie, come sono in fase di progettazione in un progetto di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].
>
> Per le applicazioni di run-time, provare a usare modelli di testo pre-elaborati: vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Se l'applicazione utilizza un set di modelli corretti in fase di compilazione, sarà più facile utilizzare modelli di testo pre-elaborati. È possibile utilizzare questo approccio anche se l'applicazione sarà in esecuzione in un computer nel quale non è installato [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per altre informazioni, vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="executing-a-text-template-in-your-application"></a>Esecuzione di un modello di testo nell'applicazione
 Per eseguire un modello di testo, chiamare il metodo ProcessTemplate di <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 L'applicazione deve trovare e fornire il modello e deve gestire l'output.

 Nel parametro è necessario fornire una classe che implementi [ITextTemplatingEngineHost.](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) `host` Questa viene richiamata dal motore.

 L'host deve essere in grado di registrare errori, risolvere riferimenti agli assembly e ai file di inclusione, fornire un dominio dell'applicazione nel quale il modello possa essere eseguito e possa chiamare il processore adatto per ciascuna direttiva.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>è definito in **Microsoft. VisualStudio. TextTemplating.\*. 0. dll**e [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) sono definiti in **Microsoft. VisualStudio. TextTemplating. Interfaces.\* 0. dll**.

## <a name="in-this-section"></a>In questa sezione
 [Procedura dettagliata: La creazione di un host](../modeling/walkthrough-creating-a-custom-text-template-host.md) del modello di testo personalizzato Mostra come creare un host del modello di testo personalizzato che rende disponibile la funzionalità del modello di testo all'esterno [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]di.

## <a name="reference"></a>Riferimenti
 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>Sezioni correlate
 [Processo di trasformazione del modello di testo](../modeling/the-text-template-transformation-process.md) Viene descritto il funzionamento della trasformazione testo e quali parti è possibile personalizzare.

 [Creazione di processori di direttiva di modelli di testo T4 personalizzati](../modeling/creating-custom-t4-text-template-directive-processors.md) Viene fornita una panoramica dei processori di direttive del modello di testo.
