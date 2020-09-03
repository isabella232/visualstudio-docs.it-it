---
title: Scrittura di codice per personalizzare una Domain-Specific Language | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4448e9a1c65ccba4a9ae48d0271f9fd91fc011b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662970"
---
# <a name="writing-code-to-customise-a-domain-specific-language"></a>Scrittura di codice per personalizzare un linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa sezione illustra come usare codice personalizzato per accedere, modificare o creare un modello in un linguaggio specifico di dominio.

 Sono disponibili diversi contesti in cui è possibile scrivere codice che funziona con un linguaggio DSL:

- **Comandi personalizzati.** È possibile creare un comando che gli utenti possono richiamare facendo clic con il pulsante destro del mouse sul diagramma e che può modificare il modello. Per altre informazioni, vedere [procedura: aggiungere un comando al menu di scelta rapida](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

- **Convalida.** È possibile scrivere codice che verifica che lo stato del modello sia corretto. Per ulteriori informazioni, vedere [convalida in un Domain-Specific Language](../modeling/validation-in-a-domain-specific-language.md).

- **Override del comportamento predefinito.** È possibile modificare molti aspetti del codice generato da DslDefinition. DSL. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).

- **Trasformazione del testo.** È possibile scrivere modelli di testo che contengono codice che accede a un modello e genera un file di testo, ad esempio per generare codice programma. Per ulteriori informazioni, vedere [generazione di codice da un Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md).

- **Altre estensioni di Visual Studio.** È possibile scrivere estensioni VSIX separate per la lettura e la modifica di modelli. Per altre informazioni, vedere [procedura: aprire un modello da file nel codice del programma](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  Le istanze delle classi definite in DslDefinition. DSL vengono mantenute in una struttura di dati denominata *archivio in memoria* (IMS) o *Archivio*. Le classi definite in un linguaggio DSL accettano sempre un archivio come argomento per il costruttore. Ad esempio, se il linguaggio DSL definisce una classe denominata esempio:

  `Example element = new Example (theStore);`

  mantenere gli oggetti nell'archivio, anziché come oggetti ordinari, offre diversi vantaggi.

- **Transazioni**. È possibile raggruppare una serie di modifiche correlate in una transazione:

   `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

   `{`

   `// make several changes to Store elements here`

   `t.Commit();`

   `}`

   Se si verifica un'eccezione durante le modifiche, in modo che non venga eseguito il commit finale (), verrà ripristinato lo stato precedente dell'archivio. Ciò consente di verificare che gli errori non lascino il modello in uno stato incoerente. Per ulteriori informazioni, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **Relazioni binarie**. Se si definisce una relazione tra due classi, le istanze di entrambe le estremità hanno una proprietà che passa all'altra estremità. Le due entità finali sono sempre sincronizzate. Se, ad esempio, si definisce una relazione di genitorialità con i ruoli denominati parents e Children, è possibile scrivere:

   `John.Children.Add(Mary)`

   Sono ora soddisfatte entrambe le espressioni seguenti:

   `John.Children.Contains(Mary)`

   `Mary.Parents.Contains(John)`

   È anche possibile ottenere lo stesso risultato scrivendo:

   `Mary.Parents.Add(John)`

   Per ulteriori informazioni, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **Regole ed eventi**. È possibile definire regole da attivare ogni volta che vengono apportate modifiche specificate. Le regole vengono usate, ad esempio, per rendere aggiornate le forme del diagramma con gli elementi del modello presenti. Per ulteriori informazioni, vedere [risposta a e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).

- **Serializzazione**. L'archivio fornisce un modo standard per serializzare gli oggetti in esso contenuti in un file. È possibile personalizzare le regole per la serializzazione e la deserializzazione. Per altre informazioni, vedere [personalizzazione dell'archiviazione file e della serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md).

## <a name="see-also"></a>Vedere anche
 [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)
