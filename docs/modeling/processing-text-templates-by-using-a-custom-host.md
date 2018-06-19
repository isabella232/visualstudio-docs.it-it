---
title: Elaborazione di modelli di testo tramite un host personalizzato
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7a47580ef347c71ecc2218816b07afc06c3866a3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31950059"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Modelli di testo di processo tramite un Host personalizzato

Il *trasformazione del modello di testo* elaborare accetta un *modello di testo* file come input e produce un file di testo come output. È possibile chiamare il motore di trasformazione del testo da un'estensione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o da un'applicazione autonoma in esecuzione in un computer nel quale è installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Tuttavia, è necessario fornire un *host del modello di testo*. Questa classe connette il modello all'ambiente, trovando risorse quali gli assembly e i file di inclusione e gestendo l'output e i messaggi di errore.

> [!TIP]
> Se si scrive un pacchetto o un'estensione che verrà eseguita in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], anziché scrivere il proprio host, è consigliabile utilizzare il servizio del modello di testo. Per ulteriori informazioni, vedere [richiamo di trasformazione del testo in un'estensione VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> Si sconsiglia di utilizzare le trasformazioni del modello di testo nelle applicazioni server. Si sconsiglia di utilizzare le trasformazioni del modello di testo eccetto in un thread singolo. Questo perché il motore del modello di testo riutilizza un solo AppDomain per tradurre, compilare ed eseguire i modelli. Il codice tradotto non è progettato per essere thread-safe. Il motore viene progettato per elaborare file in serie, come sono in fase di progettazione in un progetto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].
>
> Per le applicazioni in fase di esecuzione, è consigliabile utilizzare i modelli di testo pre-elaborato: vedere [la generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Se l'applicazione utilizza un set di modelli corretti in fase di compilazione, sarà più facile utilizzare modelli di testo pre-elaborati. È possibile utilizzare questo approccio anche se l'applicazione sarà in esecuzione in un computer nel quale non è installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per ulteriori informazioni, vedere [la generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Eseguire un modello di testo nell'applicazione

Per eseguire un modello di testo, chiamare il metodo ProcessTemplate di <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 L'applicazione deve trovare e fornire il modello e deve gestire l'output.

 Nel parametro `host`, è necessario fornire una classe che implementa <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Questa viene richiamata dal motore.

 L'host deve essere in grado di registrare errori, risolvere riferimenti agli assembly e ai file di inclusione, fornire un dominio dell'applicazione nel quale il modello possa essere eseguito e possa chiamare il processore adatto per ciascuna direttiva.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> è definito in **Microsoft.VisualStudio.TextTemplating.\*. 0. dll**, e <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> definita **TextTemplating.\*. 0 dll**.

## <a name="in-this-section"></a>In questa sezione
 [Procedura dettagliata: Creazione di un Host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md) viene illustrato come creare un host del modello di testo personalizzato che rende il testo modello funzionalità disponibile di fuori [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="reference"></a>Riferimenti
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>

## <a name="related-sections"></a>Sezioni correlate

- [Il processo di trasformazione del modello di testo](../modeling/the-text-template-transformation-process.md) viene descritto il funzionamento di trasformazione del testo, e quali parti è possibile personalizzare.
- [Creazione di processori di direttiva modello di testo T4 personalizzati](../modeling/creating-custom-t4-text-template-directive-processors.md) viene fornita una panoramica del testo processori di direttive di modello.