---
title: Panoramica di Domain-Specific Language Tools | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c0c8730d2a73b5e6dd2c48138c1633e24234db29
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273260"
---
# <a name="overview-of-domain-specific-language-tools"></a>Informazioni generali sugli strumenti di linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domain-Specific Language Tools (strumenti DSL), che sono ospitate nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], "Let" si progetta un linguaggio specifico di dominio e quindi generare tutte le operazioni che gli utenti devono disporre per creare modelli basati sulla lingua.  
  
 Gli strumenti seguenti sono inclusi negli strumenti DSL:  
  
-   Creazione guidata progetto che usa i modelli di soluzioni differenti che consentono di iniziare a sviluppare il linguaggio specifico di dominio.  
  
-   Finestra di progettazione con interfaccia grafica per la creazione e modifica la definizione di linguaggio specifico di dominio.  
  
-   Un motore di convalida che consente di assicurarsi che la definizione del linguaggio specifico di dominio sia ben formata e consente di visualizzare errori e avvisi se si verificano problemi.  
  
-   Un generatore di codice che richiede una definizione di linguaggio specifico di dominio come input e produce il codice sorgente come output.  
  
## <a name="the-dsl-tools-solution"></a>La soluzione di strumenti DSL  
 La procedura guidata finestra di progettazione Domain-Specific fornisce i modelli di soluzioni seguenti:  
  
-   Flusso di attività  
  
-   Diagrammi classi  
  
-   Linguaggio minimo  
  
-   Modelli di componenti  
  
-   WPF minimo  
  
-   Minimo Windows. Forms  
  
-   Libreria DSL  
  
 Per altre informazioni, vedere [scelta di un modello di soluzione Domain-Specific Language](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 La procedura guidata crea un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] soluzione con i progetti seguenti:  
  
-   Linguaggio specifico di dominio  
  
     Progetto Dsl definisce il linguaggio specifico di dominio e dei relativi strumenti di modifica e di elaborazione.  
  
-   **DslPackage**  
  
     Al progetto DslPackage determina come integrano gli strumenti di linguaggio [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="the-dsl-tools-graphical-interface"></a>L'interfaccia grafica strumenti DSL  
 È possibile usare l'interfaccia grafica strumenti DSL per aggiungere elementi e relazioni per il linguaggio specifico di dominio. Dopo aver aggiunto gli elementi, è possibile definire il proprio aspetto eseguendone il mapping alle forme, personalizzazione dei colori e aggiungendo gli elementi Decorator. È anche possibile aggiungere elementi alla casella degli strumenti.  
  
## <a name="validation-in-dsl-tools"></a>Convalida in strumenti DSL  
 Linguaggio specifico di dominio fornisce un livello di convalida per assicurarsi che il modello di dominio soddisfi i requisiti di base per la generazione di codice. In genere, quando si crea il proprio linguaggio specifico di dominio, è necessario aggiungere il proprio convalida per esprimere le regole per la logica di business. Per altre informazioni sulla convalida personalizzata, vedere [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
 È consigliabile convalidare il linguaggio specifico di dominio spesso quando si progettano. Se il linguaggio specifico di dominio presenta errori di convalida, è possibile generare codice sorgente. Viene eseguito il processo di generazione di codice sorgente dai modelli facendo **Trasforma tutti i modelli** sulla barra degli strumenti di Esplora soluzioni. Ogni volta che si modifica la definizione del linguaggio, assicurarsi anche di **Trasforma tutti i modelli**. Per altre informazioni, vedere [procedura: creare una soluzione di linguaggio specifico di dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="customization-of-dsl-tools"></a>Personalizzazione degli strumenti DSL  
 È possibile fornire codice aggiuntivo per perfezionare il comportamento del modello e per definire i vincoli per la lingua. Se necessario, è possibile apportare modifiche significative modificando i modelli di testo.  
  
## <a name="distributing-your-dsl-solution"></a>Distribuzione della soluzione DSL  
 Strumenti DSL genera un pacchetto ospitato in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Il pacchetto consente di visualizzare una casella degli strumenti DSL explorer e altri elementi dell'interfaccia utente che consentono agli utenti di creare modelli usando il linguaggio specifico di dominio.  
  
 Quando si compila e si esegue la soluzione strumenti DSL [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], una seconda istanza di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] viene è illustrato l'aspetto del linguaggio specifico di dominio per l'utente del linguaggio. Dopo aver verificato che tutto funzioni correttamente, è possibile distribuire il `.vsix` file che si trovano nella cartella di compilazione del progetto DslPackage. Questo file può essere utilizzato per installare il linguaggio DSL come un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensione in altri computer.  Per altre informazioni, vedere [distribuzione di soluzioni Domain-Specific Language](../modeling/deploying-domain-specific-language-solutions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [L'istanza sperimentale](../extensibility/the-experimental-instance.md)   
 [Glossario sugli strumenti Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



