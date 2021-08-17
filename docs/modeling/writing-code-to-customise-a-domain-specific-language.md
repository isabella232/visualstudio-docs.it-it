---
title: Personalizzare un linguaggio specifico di dominio
description: Informazioni su come usare codice personalizzato per accedere, modificare o creare un modello in un linguaggio specifico di dominio (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: bd80246dfa98c898bd46518ebfc55c49b92504aa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055185"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Scrivere codice per personalizzare un linguaggio specifico di dominio

Questa sezione illustra come usare codice personalizzato per accedere, modificare o creare un modello in un linguaggio specifico di dominio.

Esistono diversi contesti in cui è possibile scrivere codice che funziona con un DSL:

- **Comandi personalizzati.** È possibile creare un comando che gli utenti possono richiamare facendo clic con il pulsante destro del mouse sul diagramma e modificando il modello. Per altre informazioni, vedere [Procedura: Aggiungere un comando al menu di scelta rapida.](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)

- **Convalida.** È possibile scrivere codice che verifica che lo stato del modello sia corretto. Per altre informazioni, vedere [Validation in a Domain-Specific Language](../modeling/validation-in-a-domain-specific-language.md).

- **Override del comportamento predefinito.** È possibile modificare molti aspetti del codice generato da DslDefinition.dsl. Per altre informazioni, vedere [Override ed estensione delle classi generate.](../modeling/overriding-and-extending-the-generated-classes.md)

- **Trasformazione testo.** È possibile scrivere modelli di testo contenenti codice che accede a un modello e genera un file di testo, ad esempio per generare codice programma. Per altre informazioni, vedere [Generating Code from a Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md).

- **Altre Visual Studio seguenti.** È possibile scrivere estensioni VSIX separate che leggono e modificano i modelli. Per altre informazioni, vedere [Procedura: Aprire un modello da un file nel codice programma](../modeling/how-to-open-a-model-from-file-in-program-code.md)

Le istanze delle classi definite in DslDefinition.dsl vengono mantenute in una struttura di dati denominata *archivio in* memoria (IMS) o *Archivio*. Le classi definite in un DSL accettano sempre un oggetto Store come argomento per il costruttore. Ad esempio, se il DSL definisce una classe denominata Example:

`Example element = new Example (theStore);`

Mantenere gli oggetti nello Store (anziché semplicemente come oggetti normali) offre diversi vantaggi.

- **Transazioni**. È possibile raggruppare una serie di modifiche correlate in una transazione:

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Se si verifica un'eccezione durante le modifiche, in modo che il commit() finale non sia eseguito, l'archivio verrà reimpostato sullo stato precedente. Ciò consente di assicurarsi che gli errori non lascino il modello in uno stato incoerente. Per altre informazioni, vedere [Esplorazione e aggiornamento di un modello nel codice programma.](../modeling/navigating-and-updating-a-model-in-program-code.md)

- **Relazioni binarie**. Se si definisce una relazione tra due classi, le istanze a entrambe le estremità hanno una proprietà che consente di passare all'altra entità finale. Le due estremità vengono sempre sincronizzate. Ad esempio, se si definisce una relazione parente con ruoli denominati Parent e Children, è possibile scrivere:

     `John.Children.Add(Mary)`

     Entrambe le espressioni seguenti sono ora vere:

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     È anche possibile ottenere lo stesso effetto scrivendo:

     `Mary.Parents.Add(John)`

     Per altre informazioni, vedere [Esplorazione e aggiornamento di un modello nel codice programma.](../modeling/navigating-and-updating-a-model-in-program-code.md)

- **Regole ed eventi**. È possibile definire regole che vengono applicate ogni volta che vengono apportate modifiche specificate. Le regole vengono usate, ad esempio, per mantenere le forme nel diagramma aggiornate con gli elementi del modello che presentano. Per altre informazioni, vedere [Risposta e propagazione delle modifiche.](../modeling/responding-to-and-propagating-changes.md)

- **Serializzazione** di . Store fornisce un modo standard per serializzare gli oggetti in esso contenuti in un file. È possibile personalizzare le regole per la serializzazione e la deserializzazione. Per altre informazioni, vedere [Personalizzazione di file Archiviazione e serializzazione XML.](../modeling/customizing-file-storage-and-xml-serialization.md)

## <a name="see-also"></a>Vedi anche

- [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)