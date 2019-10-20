---
title: Creazione di processori di direttiva di modelli di testo T4 personalizzati
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 836e2c24d9f236c7b87dfff60b934221b7645f1b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654073"
---
# <a name="create-custom-t4-text-template-directive-processors"></a>Creare processori di direttiva di modelli di testo T4 personalizzati

Il *processo di trasformazione del modello di testo* accetta un file *modello di testo* come input e produce un file di testo come output. Il *motore di trasformazione del modello di testo* controlla il processo e il motore interagisce con un host di trasformazione del modello di testo e uno o più *processori di direttive* del modello di testo per completare il processo. Per ulteriori informazioni, vedere [il processo di trasformazione del modello di testo](../modeling/the-text-template-transformation-process.md).

Per creare un processore di direttiva personalizzato, si crea una classe che eredita da <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

La differenza tra queste due è che <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementa l'interfaccia minima necessaria per ottenere i parametri dall'utente e per generare il codice che produce il file di output del modello. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementa il modello di progettazione requires/fornisce. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> gestisce due parametri speciali, `requires` e `provides`.  Ad esempio, un processore di direttiva personalizzato potrebbe accettare un nome file dall'utente, aprire e leggere il file e quindi archiviare il testo del file in una variabile denominata `fileText`. Una sottoclasse della classe <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> potrebbe richiedere un nome file dall'utente come valore del parametro `requires` e il nome della variabile in cui archiviare il testo come valore del parametro `provides`. Questo processore aprirà e leggerà il file e quindi memorizzerà il testo del file nella variabile specificata.

Prima di chiamare un processore di direttiva personalizzato da un modello di testo in Visual Studio, è necessario registrarlo.

Per ulteriori informazioni su come aggiungere la chiave del registro di sistema, vedere [distribuzione di un processore di direttiva personalizzato](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Direttive personalizzate

Una direttiva personalizzata ha un aspetto simile al seguente:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

È possibile utilizzare un processore di direttiva personalizzato quando si desidera accedere a dati o risorse esterne da un modello di testo.

Modelli di testo diversi possono condividere la funzionalità fornita da un singolo processore di direttiva, in modo che i processori di direttiva forniscano un modo per fattorizzare il codice per il riutilizzo. La direttiva `include` predefinita è simile, perché può essere usata per scomporre il codice e condividerlo tra modelli di testo diversi. La differenza è che qualsiasi funzionalità fornita dalla direttiva `include` è fissa e non accetta parametri. Se si desidera fornire funzionalità comuni a un modello di testo e consentire al modello di passare parametri, è necessario creare un processore di direttiva personalizzato.

Di seguito sono riportati alcuni esempi di processori di direttive personalizzati:

- Un processore di direttiva per restituire dati da un database che accetta come parametri un nome utente e una password.

- Un processore di direttiva per aprire e leggere un file che accetta il nome del file come parametro.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Parti principali di un processore di direttiva personalizzato

Per sviluppare un processore di direttiva, è necessario creare una classe che erediti da <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

I metodi di `DirectiveProcessor` più importanti che è necessario implementare sono i seguenti.

- `bool IsDirectiveSupported(string directiveName)` restituire `true` se il processore di direttiva può gestire la direttiva denominata.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)`: il motore del modello chiama questo metodo per ogni occorrenza di una direttiva nel modello. Il processore deve salvare i risultati.

Dopo tutte le chiamate a ProcessDirective () il motore del modello chiamerà questi metodi:

- `string[] GetReferencesForProcessingRun()`: restituisce i nomi degli assembly richiesti dal codice del modello.

- `string[] GetImportsForProcessingRun()`: restituisce gli spazi dei nomi che possono essere usati nel codice del modello.

- `string GetClassCodeForProcessingRun()`-restituisce il codice di metodi, proprietà e altre dichiarazioni che il codice del modello può utilizzare. Il modo più semplice per eseguire questa operazione consiste nel compilare una stringa C# contenente il codice o Visual Basic. Per fare in modo che il processore di direttiva sia in grado di essere chiamato da un modello che utilizza un linguaggio CLR, è possibile creare le istruzioni come albero CodeDom e restituire quindi il risultato della serializzazione dell'albero nel linguaggio utilizzato dal modello.

- Per altre informazioni, vedere [procedura dettagliata: creazione di un processore di direttiva personalizzato](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Vedere anche

- [Distribuire un processore di direttiva personalizzato](../modeling/deploying-a-custom-directive-processor.md) spiega come registrare un processore di direttiva personalizzato.
- [Procedura dettagliata: creare un processore di direttiva personalizzato](../modeling/walkthrough-creating-a-custom-directive-processor.md) descrive come creare un processore di direttiva personalizzato, come registrare e testare il processore di direttiva e come formattare il file di output come HTML.