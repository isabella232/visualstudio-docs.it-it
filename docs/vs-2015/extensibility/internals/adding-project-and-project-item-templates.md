---
title: Aggiunta di modelli di progetti e di elementi di progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b68c9f4bbaed73603c46fc0beab77a308b8933d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203866"
---
# <a name="adding-project-and-project-item-templates"></a>Aggiunta di modelli di progetto e di elementi di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando si creano tipi di progetto personalizzati, è necessario fornire supporto per l'aggiunta di nuovi progetti ed elementi di progetto utilizzando le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] finestre di dialogo standard Integrated Development Environment (IDE). Negli argomenti seguenti vengono illustrate diverse tecniche per l'aggiunta di progetti ed elementi di progetto.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Contesto di progetto](../../extensibility/internals/project-context.md)  
 Viene illustrato come il progetto fornisca la maggior parte delle informazioni di contesto relative a ciò che traspare nell'ambiente.  
  
 [Priorità di progetto](../../extensibility/internals/project-priority.md)  
 Viene illustrato che un elemento del progetto è in genere un membro di un progetto per evitare ambiguità sul progetto utilizzato per aprire l'elemento.  
  
 [Progetto di file esterni](../../extensibility/internals/miscellaneous-files-project.md)  
 Vengono fornite informazioni sui due tipi di editor che possono essere utilizzati per aprire i file in un progetto e il ruolo riprodotto dal progetto per determinare quale editor utilizzare quando viene aperto un elemento del progetto.  
  
 [Registrazione di modelli di progetto e di elementi](../../extensibility/internals/registering-project-and-item-templates.md)  
 Viene illustrato cosa accade quando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] viene creato un progetto.  
  
 [Aggiunta di elementi nelle finestre di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Viene illustrato il processo per l'aggiunta di elementi alla finestra di dialogo **Aggiungi nuovo elemento** .  
  
 [Aggiunta di directory nella finestra di dialogo Nuovo progetto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Viene fornito un esempio di registrazione di una nuova directory che contiene modelli personalizzati resi disponibili da un pacchetto VSPackage.  
  
 [Aggiunta di directory nella finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Viene fornito un esempio di registrazione di un nuovo set di directory per la finestra di dialogo **Aggiungi nuovo elemento** .  
  
 [Comandi definiti dall'IDE per l'estensione dei sistemi di progetto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Elenca i diversi tipi di elementi di comando utilizzati per estendere i sistemi di progetto.  
  
 [CATID per gli oggetti che vengono in genere usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Elenca CATID per gli oggetti utilizzati per estendere i [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] sistemi di progetto, e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Procedura: Aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)  
 Vengono fornite istruzioni dettagliate per l'apertura di un elemento associato in modo intrinseco a un editor specifico per un progetto.  
  
 [Procedura: Aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)  
 Vengono fornite istruzioni dettagliate per l'apertura di un editor standard.  
  
 [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)  
 Vengono forniti collegamenti agli argomenti concettuali del sottotipo di progetto. I sottotipi di progetto estendono i [!INCLUDE[csprcs](../../includes/csprcs-md.md)] progetti e esistenti [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .  
  
 [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)  
 Fornisce collegamenti ad argomenti aggiuntivi che offrono informazioni su come progettare nuovi tipi di progetto.
