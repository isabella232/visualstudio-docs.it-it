---
title: Generazione di codice da un linguaggio specifico di dominio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3fbe7e40a277174eb556a61b50eb88279adebfb2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531333"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Generazione di codice da un linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [generazione di codice da un linguaggio specifico di dominio](https://docs.microsoft.com/visualstudio/modeling/generating-code-from-a-domain-specific-language).  
  
Microsoft [!INCLUDE[dsl](../includes/dsl-md.md)] fornisce un potente strumento per generare codice, documenti, file di configurazione e altri artefatti da dati rappresentati nei modelli. Usando [!INCLUDE[dsl](../includes/dsl-md.md)], è possibile creare un set di classi che rappresentano i dati, è possibile scrivere modelli di testo nelle classi i cui nomi e le proprietà riflettono i dati.  
  
 Ad esempio, Fabrikam ha un file XML di nomi di clienti e indirizzi di posta elettronica. Agli sviluppatori di creare un modello in cui clienti sono una classe, con il nome di proprietà e il messaggio di posta elettronica. Scrittura diversi modelli di testo per elaborare i dati, tra cui questo frammento cui viene prodotta una tabella di tutti i clienti come parte di una pagina HTML:  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 Quando viene elaborato il database dei clienti, il file XML viene letto nell'archivio del modello. Oggetto *processore di direttiva*, creato utilizzando [!INCLUDE[dsl](../includes/dsl-md.md)], rende disponibili per il codice della classe Customer nel modello di testo. Molti modelli di testo possono essere eseguiti a fronte dell'archivio stesso.  
  
 Modelli di testo sono essenziali per [!INCLUDE[dsl](../includes/dsl-md.md)]. Vengono usate per generare il codice sorgente per gli elementi del modello di dominio anche per il pacchetto VSPackage e i controlli che consentono di integrare gli strumenti con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 In questa sezione vengono illustrati alcuni dei modi per creare, modificare ed eseguire il debug di modelli di testo utilizzati in [!INCLUDE[dsl](../includes/dsl-md.md)].  
  
## <a name="in-this-section"></a>In questa sezione  
 [Accesso ai modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md)  
  
 Fornisce informazioni di base che fa riferimento al linguaggio specifico di dominio nei modelli di testo.  
  
 [Procedura dettagliata: debug di un modello di testo che accede a un modello](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)  
  
 Viene descritto come eseguire la risoluzione dei problemi e debug su un modello di testo che fa riferimento a un linguaggio specifico di dominio.  
  
 [Procedura dettagliata: connessione di un host a un processore di direttiva generato](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
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



