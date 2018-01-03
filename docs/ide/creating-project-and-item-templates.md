---
title: Creazione di modelli di progetti e di elementi | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], projects
- item templates, about item templates
- templates [Visual Studio], item
- Visual Studio templates, item
- Visual Studio templates, about templates
- project templates [Visual Studio], about project templates
- Visual Studio templates, project
- templates [Visual Studio], about templates
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 43b45f70e8ac7a6eeadfd3fb216b53540ec9a8b8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="creating-project-and-item-templates"></a>Creazione di modelli di progetti e di elementi
I modelli di progetto e di elemento di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] forniscono stub riutilizzabili che supportano gli utenti con codice e strutture di base che è possibile utilizzare per gli scopi desiderati.  
  
## <a name="visual-studio-templates"></a>Modelli di Visual Studio  
 Durante l'installazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono installati vari modelli di progetto e di elemento predefiniti. I modelli Windows Forms Application e Libreria di classi di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] disponibili nella finestra di dialogo **Nuovo progetto** sono esempi di modelli di progetto. I modelli di elemento installati sono disponibili nella finestra di dialogo **Aggiungi nuovo elemento** e comprendono elementi come file di codice, file XML, pagine HTML e fogli di stile.  
  
 I modelli rappresentano un punto di partenza per cominciare la creazione di progetti o per espandere i progetti correnti. I modelli di progetto forniscono i file necessari per un determinato tipo di progetto, includono i riferimenti ad assembly standard e impostano le proprietà di progetto predefinite e le opzioni del compilatore. La complessità dei modelli di elemento può variare: da un singolo file vuoto con una corretta estensione di file fino a un elemento a più file contenente, ad esempio, file di codice sorgente con codice stub, file di informazioni sulla progettazione e risorse incorporate.  
  
 Oltre ai modelli installati disponibili nelle finestre di dialogo **Nuovo progetto** e **Aggiungi nuovo elemento** è possibile creare modelli personalizzati o scaricare e usare modelli creati dalla community. Per altre informazioni, vedere [Procedura: Creare modelli di progetto](../ide/how-to-create-project-templates.md) e [Procedura: Creare modelli di elementi](../ide/how-to-create-item-templates.md).  
  
## <a name="contents-of-a-template"></a>Contenuto di un modello  
 Tutti i modelli di progetto e i modelli di elemento, sia quelli installati con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sia quelli creati dall'utente, funzionano in base agli stessi principi e hanno contenuti simili. Tutti i modelli contengono gli elementi seguenti:  
  
-   I file da creare quando viene usato il modello, tra cui i file del codice sorgente, le risorse incorporate, i file di progetto e così via.  
  
-   Un file VSTEMPLATE. Questo file contiene i metadati che offrono a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] le informazioni necessarie per visualizzare il modello nelle finestre di dialogo **Nuovo progetto** e **Aggiungi nuovo elemento** e per creare un progetto o un elemento dal modello. Per altre informazioni sui file con estensione vstemplate, vedere [Parametri di modello](../ide/template-parameters.md).  
  
 Quando questi file vengono compressi in un file ZIP e inseriti nella cartella corretta, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] li visualizza automaticamente. I modelli di progetto sono disponibili nella sezione **Modelli personali** della finestra di dialogo **Nuovo progetto** e i modelli di elemento sono disponibili nella finestra di dialogo **Aggiungi nuovo elemento**. Per altre informazioni sulle cartelle dei modelli, vedere [Procedura: Individuare e organizzare modelli](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="starter-kits"></a>Starter kit  
 Gli starter kit sono modelli avanzati che possono essere condivisi con altri membri della community. Uno starter kit include esempi di codice compilabili, documentazione e altre risorse per facilitare l'apprendimento di nuovi strumenti e tecniche di programmazione durante la compilazione di applicazioni utili e reali. I contenuti e le procedure di base per gli starter kit sono identici a quelli dei modelli. Per altre informazioni, vedere [Procedura: Creare starter kit](../ide/how-to-create-starter-kits.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare modelli di progetto](../ide/how-to-create-project-templates.md)   
 [Procedura: Creare modelli di elementi](../ide/how-to-create-item-templates.md)   
 [Parametri di modello](../ide/template-parameters.md)   
 [Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)   
 [Procedura: Creare starter kit](../ide/how-to-create-starter-kits.md)