---
title: Creazione di processori di direttiva di modelli di testo T4 personalizzati
description: Informazioni sul processo di trasformazione del modello di testo e su come creare un processore di direttiva del modello di testo T4 personalizzato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 9441a0525a4e01b99f6b43ef696b97f7d1a9b6d3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040398"
---
# <a name="create-custom-t4-text-template-directive-processors"></a>Creare processori di direttiva di modelli di testo T4 personalizzati

Il *processo di trasformazione del modello di* testo accetta un file di *modello* di testo come input e produce un file di testo come output. Il *motore di trasformazione del modello* di testo controlla il processo e interagisce con un host di trasformazione del modello di testo e con uno o più processori di direttiva del modello di testo per completare il processo.  Per altre informazioni, vedere [Processo di trasformazione del modello di testo.](../modeling/the-text-template-transformation-process.md)

Per creare un processore di direttiva personalizzato, si crea una classe che eredita da <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

La differenza tra questi due elementi è che implementa l'interfaccia minima necessaria per ottenere i parametri dall'utente e generare il codice che produce il <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> file di output del modello. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementa lo schema progettuale requires/provides. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> gestisce due parametri speciali, `requires` e `provides` .  Ad esempio, un processore di direttiva personalizzato potrebbe accettare un nome di file dall'utente, aprire e leggere il file e quindi archiviare il testo del file in una variabile denominata `fileText` . Una sottoclasse della classe può prendere un nome file dall'utente come valore del parametro e il nome della variabile in cui archiviare il testo come valore <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> `requires` del `provides` parametro. Questo processore apre e legge il file e quindi archivia il testo del file nella variabile specificata.

Prima di chiamare un processore di direttiva personalizzato da un modello di Visual Studio, è necessario registrarlo.

Per altre informazioni su come aggiungere la chiave del Registro di sistema, vedere [Distribuzione di un processore di direttiva personalizzato.](../modeling/deploying-a-custom-directive-processor.md)

## <a name="custom-directives"></a>Direttive personalizzate

Una direttiva personalizzata è simile alla seguente:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

È possibile usare un processore di direttiva personalizzato quando si vuole accedere a dati o risorse esterni da un modello di testo.

Modelli di testo diversi possono condividere le funzionalità fornite da un singolo processore di direttiva, quindi i processori di direttiva consentono di fattoriare il codice per il riutilizzo. La direttiva predefinita è simile, perché è possibile usarla per eseguire il factor out del codice `include` e condividerlo tra modelli di testo diversi. La differenza è che qualsiasi funzionalità fornita `include` dalla direttiva è fissa e non accetta parametri. Se si desidera fornire funzionalità comuni a un modello di testo e consentire al modello di passare parametri, è necessario creare un processore di direttiva personalizzato.

Alcuni esempi di processori di direttiva personalizzati possono essere:

- Processore di direttiva per restituire dati da un database che accetta un nome utente e una password come parametri.

- Processore di direttiva per aprire e leggere un file che accetta il nome del file come parametro.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Parti principali di un processore di direttiva personalizzato

Per sviluppare un processore di direttiva, è necessario creare una classe che eredita da <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

I metodi più `DirectiveProcessor` importanti che è necessario implementare sono i seguenti.

- `bool IsDirectiveSupported(string directiveName)` - Restituisce `true` se il processore di direttiva può gestire la direttiva denominata.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` - Il motore di modelli chiama questo metodo per ogni occorrenza di una direttiva nel modello. Il processore deve salvare i risultati.

Dopo tutte le chiamate a ProcessDirective() il motore di creazione modelli chiamerà questi metodi:

- `string[] GetReferencesForProcessingRun()` - Restituisce i nomi degli assembly necessari per il codice del modello.

- `string[] GetImportsForProcessingRun()` - Restituisce gli spazi dei nomi che possono essere usati nel codice del modello.

- `string GetClassCodeForProcessingRun()` - Restituisce il codice di metodi, proprietà e altre dichiarazioni che il codice del modello può usare. Il modo più semplice per eseguire questa operazione è compilare una stringa contenente il codice C# o Visual Basic codice. Per fare in modo che il processore di direttiva possa essere chiamato da un modello che usa qualsiasi linguaggio CLR, è possibile costruire le istruzioni come albero CodeDom e quindi restituire il risultato della serializzazione dell'albero nel linguaggio utilizzato dal modello.

- Per altre informazioni, vedere [Procedura dettagliata: Creazione di un processore di direttiva personalizzato.](../modeling/walkthrough-creating-a-custom-directive-processor.md)

## <a name="see-also"></a>Vedi anche

- [Distribuire un processore di direttiva personalizzato](../modeling/deploying-a-custom-directive-processor.md) illustra come registrare un processore di direttiva personalizzato.
- [Procedura dettagliata: Creare un](../modeling/walkthrough-creating-a-custom-directive-processor.md) processore di direttiva personalizzato descrive come creare un processore di direttiva personalizzato, come registrare e testare il processore di direttiva e come formattare il file di output come HTML.
