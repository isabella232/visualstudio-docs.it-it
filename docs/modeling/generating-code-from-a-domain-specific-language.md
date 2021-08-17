---
title: Generazione di codice da un linguaggio specifico di dominio
description: Informazioni su Domain-Specific Language Tools offre un modo efficace per generare codice, documenti e altri elementi dai dati rappresentati nei modelli.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: b86507ac3e5aaadc0fc5f5c1b2bb9c1f380d9e5b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047907"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Generazione di codice da un linguaggio specifico di dominio

Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] offre un modo efficace per generare codice, documenti, file di configurazione e altri elementi dai dati rappresentati nei modelli. Usando , è possibile creare un set di classi che rappresentano i dati ed è possibile scrivere modelli di testo in classi i cui nomi e proprietà riflettono [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] i dati.

Ad esempio, Fabrikam ha un file XML con i nomi dei clienti e gli indirizzi di posta elettronica. Gli sviluppatori creano un modello in cui Customer è una classe, con il nome delle proprietà e la posta elettronica. Scrivono diversi modelli di testo per elaborare i dati, incluso questo frammento che produce una tabella di tutti i clienti come parte di una pagina HTML:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

Quando il database del cliente viene elaborato, il file XML viene letto nell'archivio modelli. Un *processore di* direttiva , creato tramite [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , rende la classe Customer disponibile per il codice nel modello di testo. Molti modelli di testo possono essere eseguiti nello stesso archivio.

I modelli di testo sono essenziali per [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] . Vengono usati per generare il codice sorgente per gli elementi del modello di dominio, nonché per il pacchetto VSPackage e i controlli usati per integrare gli strumenti con Visual Studio.

In questa sezione vengono illustrati alcuni dei modi per creare, modificare ed eseguire il debug di modelli di testo usati in [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] .

## <a name="in-this-section"></a>Contenuto della sezione

[Accesso ai modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md)\
Fornisce informazioni di base sul riferimento al linguaggio specifico di dominio nei modelli di testo.

[Procedura dettagliata: Debug di un modello di testo che accede a un modello](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)\
Viene descritto come eseguire la risoluzione dei problemi e il debug in un modello di testo che fa riferimento a un linguaggio specifico di dominio.

[Procedura dettagliata: Connessione di un host a un processore di direttiva generato](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)\
Viene descritto come connettere un host personalizzato a un processore di direttiva generato.

[Comando DslTextTransform](../modeling/the-dsltexttransform-command.md)\
Descrive il file di comando che esegue l'eseguibile TextTransform nella riga di comando per i modelli di testo che fanno riferimento a linguaggi specifici di dominio.

## <a name="reference"></a>Riferimento

[Scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md)\
Fornisce la sintassi delle direttive del modello di testo e dei blocchi di controllo.

## <a name="related-sections"></a>Sezioni correlate

[Generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)\
Illustra il processo di trasformazione del modello di testo.

[Generazione di codice in un processo di compilazione](../modeling/code-generation-in-a-build-process.md)\
Leggere questo argomento se si generano file da un DSL in un server di compilazione.
