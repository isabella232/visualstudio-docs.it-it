---
title: L'elaborazione di modelli di testo tramite un Host personalizzato | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5fa54f6b7ea57b6374e8fef291c64f0e5369ffea
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303459"
---
# <a name="processing-text-templates-by-using-a-custom-host"></a>Elaborazione di modelli di testo tramite un host personalizzato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il *trasformazione del modello di testo* elaborare accetta una *modello di testo* file come input e produce file di testo come output. È possibile chiamare il motore di trasformazione del testo da un'estensione [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o da un'applicazione autonoma in esecuzione in un computer nel quale è installato [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Tuttavia, è necessario specificare una *host di modello testo*. Questa classe connette il modello all'ambiente, trovando risorse quali gli assembly e i file di inclusione e gestendo l'output e i messaggi di errore.  
  
> [!TIP]
>  Se si scrive un pacchetto o un'estensione che verrà eseguita in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], anziché scrivere il proprio host, è consigliabile utilizzare il servizio del modello di testo. Per altre informazioni, vedere [richiamo di trasformazione del testo in un'estensione VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
> [!NOTE]
>  Si sconsiglia di utilizzare le trasformazioni del modello di testo nelle applicazioni server. Si sconsiglia di utilizzare le trasformazioni del modello di testo eccetto in un thread singolo. Questo perché il motore del modello di testo riutilizza un solo AppDomain per tradurre, compilare ed eseguire i modelli. Il codice tradotto non è progettato per essere thread-safe. Il motore viene progettato per elaborare file in serie, come sono in fase di progettazione in un progetto di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
>   
>  Per le applicazioni in fase di esecuzione, è consigliabile usare i modelli di testo pre-elaborati: vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
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
  
 Nel parametro `host`, è necessario fornire una classe che implementa <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Questa viene richiamata dal motore.  
  
 L'host deve essere in grado di registrare errori, risolvere riferimenti agli assembly e ai file di inclusione, fornire un dominio dell'applicazione nel quale il modello possa essere eseguito e possa chiamare il processore adatto per ciascuna direttiva.  
  
 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> è definito in **Microsoft.VisualStudio.TextTemplating.\*. 0.log dll**, e <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> definito nella **TextTemplating.\*. 0.log dll**.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Procedura dettagliata: creazione di un host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 Viene mostrato come creare un host del modello di testo personalizzato che rende la funzionalità del modello di testo disponibile al di fuori di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Processo di trasformazione del modello di testo](../modeling/the-text-template-transformation-process.md)  
 Viene illustrato il funzionamento della trasformazione di testo e quali parti è possibile personalizzare.  
  
 [Creazione di processori di direttiva di modelli di testo T4 personalizzati](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Viene fornita una panoramica dei processori di direttiva del modello di testo.



