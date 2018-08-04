---
title: Aggiunta di progetto e modelli di elemento di progetto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db53ddce3161097347760026aea16a51f8098519
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499634"
---
# <a name="add-project-and-project-item-templates"></a>Aggiungere al progetto e modelli di elemento di progetto
Quando si creano tipi di progetto personalizzati, è necessario fornire supporto per l'aggiunta di nuovi progetti ed elementi del progetto con lo standard [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] finestre di dialogo di ambiente di sviluppo (IDE) di sviluppo integrato. Gli argomenti seguenti descrivono le diverse tecniche per l'aggiunta di progetti ed elementi del progetto.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Contesto del progetto](../../extensibility/internals/project-context.md)  
 Viene illustrato che il progetto fornisce la maggior parte delle informazioni di contesto per ciò che accade realmente nell'ambiente.  
  
 [Priorità del progetto](../../extensibility/internals/project-priority.md)  
 Viene illustrato che un elemento del progetto è in genere un membro di un progetto per evitare ambiguità sul cui progetto viene utilizzato per aprire l'elemento.  
  
 [Progetto di file esterni](../../extensibility/internals/miscellaneous-files-project.md)  
 Vengono fornite informazioni sui due tipi di editor che può essere utilizzato per aprire i file in un progetto e il ruolo viene riprodotto per determinare quale editor utilizzare quando un elemento del progetto viene aperto il progetto.  
  
 [Registrare i modelli di progetto ed elemento](../../extensibility/internals/registering-project-and-item-templates.md)  
 Viene spiegato cosa accade quando un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] creazione del progetto.  
  
 [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Viene illustrato il processo per l'aggiunta di elementi per il **Aggiungi nuovo elemento** nella finestra di dialogo.  
  
 [Aggiungere directory alla finestra di dialogo Nuovo progetto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Viene fornito un esempio di registrazione di una nuova directory che contiene i modelli personalizzati resi disponibili da un pacchetto VSPackage.  
  
 [Aggiungere directory alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Viene fornito un esempio di registrazione di un nuovo set di directory per il **Aggiungi nuovo elemento** nella finestra di dialogo.  
  
 [Comandi definiti dall'IDE per l'estensione di sistemi di progetto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Elenca i diversi tipi di elementi di comando utilizzati per estendere i sistemi di progetto.  
  
 [CATID per gli oggetti che sono in genere usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Elenca i CATID per gli oggetti che vengono utilizzati per estendere [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] sistemi di progetto.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Procedura: aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)  
 Vengono fornite istruzioni dettagliate per l'apertura di un elemento intrinsecamente associato a un editor specifico per un progetto.  
  
 [Procedura: aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)  
 Vengono fornite istruzioni dettagliate per l'apertura di un editor standard.  
  
 [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)  
 Vengono forniti collegamenti agli argomenti concettuali sottotipo di progetto. Estendono sottotipi di progetto esistente [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] progetti.  
  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Vengono forniti collegamenti ad argomenti aggiuntivi che offrono informazioni su come progettare nuovi tipi di progetto.