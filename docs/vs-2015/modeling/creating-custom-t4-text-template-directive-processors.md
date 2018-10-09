---
title: Creazione di processori di direttiva modello di testo T4 personalizzati | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, custom directive processors
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d97b87289be6f6fb685fe9f1b4e5ee4309bd0431
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517472"
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>Creazione di processori di direttiva di modelli di testo T4 personalizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [creazione di processori direttiva di modelli di Custom T4 testo](https://docs.microsoft.com/visualstudio/modeling/creating-custom-t4-text-template-directive-processors).  
  
Il *processo di trasformazione di modello di testo* accetta una *modello di testo* file come input e produce file di testo come output. Il *motore di trasformazione del modello di testo* il processo e il motore interagisce con un host di trasformazione del modello di testo e un modello di testo di uno o più controlli *processori di direttiva* per completare il processo. Per altre informazioni, vedere [il processo di trasformazione del modello di testo](../modeling/the-text-template-transformation-process.md).  
  
 Per creare un processore di direttiva personalizzato, si crea una classe che eredita da <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
 La differenza tra questi due è che <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementa l'interfaccia minima che è necessario per ottenere i parametri da parte dell'utente e per generare il codice che produce il file di output del modello. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementa il modello di progettazione requires/provides. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> gestisce due parametri speciali `requires` e `provides`.  Ad esempio, un processore di direttiva personalizzato potrebbe accettare un nome di file da parte dell'utente, aprire e leggere il file e quindi archiviare il testo del file in una variabile denominata `fileText`. Sottoclasse del <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> classe potrebbe richiedere un nome di file da parte dell'utente come valore del `requires` parametro e il nome della variabile in cui archiviare il testo come valore del `provides` parametro. Questo processore verrebbe aprire e leggere il file e quindi archiviare il testo del file nella variabile specificata.  
  
 Prima di chiamare un processore di direttiva personalizzato da un modello di testo in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è necessario registrarlo.  
  
 Per altre informazioni su come aggiungere la chiave del Registro di sistema, vedere [distribuzione di un processore di direttiva personalizzato](../modeling/deploying-a-custom-directive-processor.md).  
  
## <a name="custom-directives"></a>Direttive personalizzate  
 Una direttiva personalizzata è simile alla seguente:  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`  
  
 È possibile usare un processore di direttiva personalizzato quando si desidera accedere alle risorse o dati esterni da un modello di testo.  
  
 Modelli di testo diversi possono condividere la funzionalità che fornisce un singolo processore di direttiva, in modo che i processori di direttiva forniscono un modo per scomporre il codice per il riutilizzo. L'elemento predefinito `include` direttiva è simile, in quanto è possibile utilizzarlo per scomporre il codice e condividerlo tra modelli di testo diverso. La differenza è che tutte le funzionalità che il `include` direttiva include è fisso e non accetta parametri. Se si desidera fornire le funzionalità comuni per un modello di testo e consentire il modello passare i parametri, è necessario creare un processore di direttiva personalizzato.  
  
 Alcuni esempi di processori di direttiva personalizzati potrebbe essere:  
  
-   Un processore di direttiva per restituire dati da un database che accetta un nome utente e una password come parametri.  
  
-   Un processore di direttiva ad aprire e leggere un file che accetta il nome del file come parametro.  
  
### <a name="principal-parts-of-a-custom-directive-processor"></a>Parti principali di un processore di direttiva personalizzato  
 Per sviluppare un processore di direttiva, è necessario creare una classe che eredita da <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
 La più importante `DirectiveProcessor` metodi che è necessario implementare sono i seguenti.  
  
-   `bool IsDirectiveSupported(string directiveName)` -Restituito `true` se il processore di direttiva può gestire con la direttiva denominata.  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -Il motore del modello chiama questo metodo per ogni occorrenza di una direttiva del modello. Il processore deve salvare i risultati.  
  
 Dopo tutte le chiamate a ProcessDirective () il motore del modello chiameranno tali metodi:  
  
-   `string[] GetReferencesForProcessingRun()` : Restituisce i nomi degli assembly che richiede il codice del modello.  
  
-   `string[] GetImportsForProcessingRun()` -Restituire gli spazi dei nomi che può essere usato nel codice del modello.  
  
-   `string GetClassCodeForProcessingRun()` -Il codice restituito di metodi, proprietà e altre dichiarazioni che possa usare il codice del modello. Il modo più semplice per eseguire questa operazione consiste nella compilazione di una stringa contenente il codice c# o Visual Basic. Per rendere il processore di direttiva in grado di essere chiamato da un modello che Usa qualsiasi linguaggio Common Language Runtime, è possibile creare le istruzioni come un struttura ad albero CodeDom e restituirne il risultato di serializzare l'albero nella lingua utilizzata dal modello.  
  
-   Per altre informazioni, vedere [procedura dettagliata: creazione di un processore di direttiva personalizzato](../modeling/walkthrough-creating-a-custom-directive-processor.md).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Distribuzione di un processore di direttiva personalizzato](../modeling/deploying-a-custom-directive-processor.md)  
 Viene illustrato come registrare un processore di direttiva personalizzato.  
  
 [Procedura dettagliata: creazione di un processore di direttiva personalizzato](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 Viene descritto come creare un processore di direttiva personalizzato, come registrare e testare il processore di direttiva e come formattare il file di output in formato HTML.


