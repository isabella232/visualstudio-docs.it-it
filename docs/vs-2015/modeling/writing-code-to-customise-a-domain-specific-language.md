---
title: Scrittura di codice per personalizzare un linguaggio specifico di dominio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 03b92c8ea9b764df517b02dc0dc256b5837a6c10
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965470"
---
# <a name="writing-code-to-customise-a-domain-specific-language"></a>Scrittura di codice per personalizzare un linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa sezione illustra come usare codice personalizzato per accedere, modificare o creare un modello in un linguaggio specifico di dominio.  
  
 Esistono diversi contesti in cui è possibile scrivere codice che funziona con un linguaggio DSL:  
  
- **Comandi personalizzati.** È possibile creare un comando che gli utenti possono richiamare facendo clic sul diagramma e che possono modificare il modello. Per altre informazioni, vedere [Procedura: Aggiungere un comando al Menu di scelta rapida](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
- **Convalida.** È possibile scrivere codice che verifica che il modello è in uno stato corretto. Per altre informazioni, vedere [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
- **Override del comportamento predefinito.** È possibile modificare molti aspetti del codice generato dalla Dsldefinition. Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).  
  
- **Trasformazione del testo.** È possibile scrivere modelli di testo che contengono codice che accede a un modello e genera un file di testo, ad esempio per generare codice programma. Per altre informazioni, vedere [generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
- **Altre estensioni di Visual Studio.** È possibile scrivere le estensioni VSIX separate che leggeranno e modificare modelli. Per altre informazioni, vedere [Procedura: Aprire un modello da file nel codice del programma](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
  Le istanze delle classi definite in Dsldefinition vengono mantenute in una struttura di dati denominata il *Store In memoria* (IMS) o *Store*. Classi definite in un linguaggio DSL sempre accettano una Store come argomento al costruttore. Ad esempio, se il linguaggio DSL definisce una classe denominata esempio:  
  
  `Example element = new Example (theStore);`  
  
  mantenere gli oggetti nel Store (anziché semplicemente come normali oggetti) offre diversi vantaggi.  
  
- **Le transazioni**. È possibile raggruppare una serie di modifiche correlate in una transazione:  
  
   `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
   `{`  
  
   `// make several changes to Store elements here`  
  
   `t.Commit();`  
  
   `}`  
  
   Se si verifica un'eccezione durante le modifiche, in modo che non viene eseguito il commit () finale, reimposterà la Store allo stato precedente. Ciò consente di assicurarsi che gli errori non lascino il modello in uno stato incoerente. Per altre informazioni, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
- **Le relazioni binarie**. Se si definisce una relazione tra due classi, le istanze a entrambe le estremità hanno una proprietà che consente di passare a altra estremità. Le due estremità sono sempre sincronizzate. Ad esempio, se si definisce una relazione parenthood con ruoli denominati elementi padre e figlio, è possibile scrivere:  
  
   `John.Children.Add(Mary)`  
  
   Ora entrambe le espressioni seguenti sono vere:  
  
   `John.Children.Contains(Mary)`  
  
   `Mary.Parents.Contains(John)`  
  
   È anche possibile ottenere lo stesso effetto scrivendo:  
  
   `Mary.Parents.Add(John)`  
  
   Per altre informazioni, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
- **Regole ed eventi**. È possibile definire regole che vengono generati ogni volta che vengono apportate modifiche specificate. Le regole vengono utilizzate, ad esempio, per mantenere aggiornati con gli elementi del modello che presentano le forme nel diagramma. Per altre informazioni, vedere [procedura: rispondere a e la propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).  
  
- **Serializzazione**. La Store offre un metodo standard per serializzare oggetti in che esso contenuti in un file. È possibile personalizzare le regole per la serializzazione e deserializzazione. Per altre informazioni, vedere [archiviazione di File di personalizzazione e la serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)
