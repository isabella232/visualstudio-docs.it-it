---
title: Aggiunta di progetto e modelli di elemento di progetto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81aa673eb42bf28368d01baf6a2dfb0e43a1f3b9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199888"
---
# <a name="adding-project-and-project-item-templates"></a>Aggiunta di modelli di progetto e di elementi di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando si creano tipi di progetto personalizzati, è necessario fornire supporto per l'aggiunta di nuovi progetti ed elementi del progetto con lo standard [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] finestre di dialogo di ambiente di sviluppo (IDE) di sviluppo integrato. Gli argomenti seguenti descrivono le diverse tecniche per l'aggiunta di progetti ed elementi del progetto.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Contesto di progetto](../../extensibility/internals/project-context.md)  
 Viene illustrato che il progetto fornisce la maggior parte delle informazioni di contesto per ciò che accade realmente nell'ambiente.  
  
 [Priorità di progetto](../../extensibility/internals/project-priority.md)  
 Viene illustrato che un elemento del progetto è in genere un membro di un progetto per evitare ambiguità sul cui progetto viene utilizzato per aprire l'elemento.  
  
 [Progetto di file esterni](../../extensibility/internals/miscellaneous-files-project.md)  
 Vengono fornite informazioni sui due tipi di editor che può essere utilizzato per aprire i file in un progetto e il ruolo viene riprodotto per determinare quale editor utilizzare quando un elemento del progetto viene aperto il progetto.  
  
 [Registrazione di modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md)  
 Viene spiegato cosa accade quando un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] creazione del progetto.  
  
 [Aggiunta di elementi nelle finestre di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Viene illustrato il processo per l'aggiunta di elementi per il **Aggiungi nuovo elemento** nella finestra di dialogo.  
  
 [Aggiunta di directory nella finestra di dialogo Nuovo progetto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Viene fornito un esempio di registrazione di una nuova directory che contiene i modelli personalizzati resi disponibili da un pacchetto VSPackage.  
  
 [Aggiunta di directory nella finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Viene fornito un esempio di registrazione di un nuovo set di directory per il **Aggiungi nuovo elemento** nella finestra di dialogo.  
  
 [Comandi definiti dall'IDE per l'estensione dei sistemi di progetto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Elenca i diversi tipi di elementi di comando utilizzati per estendere i sistemi di progetto.  
  
 [CATID per gli oggetti che vengono in genere usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Elenca i CATID per gli oggetti che vengono utilizzati per estendere [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] sistemi di progetto.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Procedura: Aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)  
 Vengono fornite istruzioni dettagliate per l'apertura di un elemento intrinsecamente associato a un editor specifico per un progetto.  
  
 [Procedura: Aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)  
 Vengono fornite istruzioni dettagliate per l'apertura di un editor standard.  
  
 [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)  
 Vengono forniti collegamenti agli argomenti concettuali sottotipo di progetto. Estendono sottotipi di progetto esistente [!INCLUDE[csprcs](../../includes/csprcs-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] progetti.  
  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Vengono forniti collegamenti ad argomenti aggiuntivi che offrono informazioni su come progettare nuovi tipi di progetto.

