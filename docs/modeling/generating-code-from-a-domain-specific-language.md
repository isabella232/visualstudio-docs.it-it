---
title: Generazione di codice da un linguaggio specifico di dominio
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: e9165d5ff6a38dd0dbf214321132f2da0a60b15d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883159"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Generazione di codice da un linguaggio specifico di dominio
Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] fornisce un potente strumento per generare codice, documenti, file di configurazione e altri artefatti da dati rappresentati nei modelli. Usando [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], è possibile creare un set di classi che rappresentano i dati, è possibile scrivere modelli di testo nelle classi i cui nomi e le proprietà riflettono i dati.

 Ad esempio, Fabrikam ha un file XML di nomi di clienti e indirizzi di posta elettronica. Agli sviluppatori di creare un modello in cui clienti sono una classe, con il nome di proprietà e il messaggio di posta elettronica. Scrittura diversi modelli di testo per elaborare i dati, tra cui questo frammento cui viene prodotta una tabella di tutti i clienti come parte di una pagina HTML:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

 Quando viene elaborato il database dei clienti, il file XML viene letto nell'archivio del modello. Oggetto *processore di direttiva*, creato utilizzando [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], rende disponibili per il codice della classe Customer nel modello di testo. Molti modelli di testo possono essere eseguiti a fronte dell'archivio stesso.

 Modelli di testo sono essenziali per [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Vengono utilizzati per generare il codice sorgente per gli elementi del modello di dominio anche per il pacchetto VSPackage e i controlli che consentono di integrare gli strumenti con Visual Studio.

 In questa sezione vengono illustrati alcuni dei modi per creare, modificare ed eseguire il debug di modelli di testo utilizzati in [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].

## <a name="in-this-section"></a>In questa sezione
 [Accesso ai modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md)

 Fornisce informazioni di base che fa riferimento al linguaggio specifico di dominio nei modelli di testo.

 [Procedura dettagliata: Debug di un modello di testo che accede a un modello](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)

 Viene descritto come eseguire la risoluzione dei problemi e debug su un modello di testo che fa riferimento a un linguaggio specifico di dominio.

 [Procedura dettagliata: Connessione di un Host a un processore di direttiva generato](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)

 Viene descritto come connettere un host personalizzato a un processore di direttiva generato.

 [Comando DslTextTransform](../modeling/the-dsltexttransform-command.md)

 Descrive il file di comando che esegue il file eseguibile TextTransform nella riga di comando per i modelli di testo che fanno riferimento a domain-specific Language.

## <a name="reference"></a>Riferimenti
 [Scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md)

 Fornisce la sintassi delle direttive di modello di testo e blocchi di controllo.

## <a name="related-sections"></a>Sezioni correlate
 [Generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

 Viene illustrato il processo di trasformazione di modello di testo.

 [Generazione di codice in un processo di compilazione](../modeling/code-generation-in-a-build-process.md)

 Se si desidera generare i file da un linguaggio DSL in un server di compilazione, leggere questo argomento.