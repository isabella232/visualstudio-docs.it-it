---
title: Procedure guidate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7afb8956ab3c5f4fb202adadbeea32d90e159074
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964167"
---
# <a name="wizards"></a>Procedure guidate
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dopo aver creato una procedura guidata, si desidera in genere deve essere aggiunto il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente di sviluppo (IDE) integrato in modo che altri utenti possano usarlo. La procedura guidata di aggiunta appare nel **Aggiungi nuovo progetto** oppure **Aggiungi nuovo elemento** finestre di dialogo. Per visualizzare il **Aggiungi nuovo progetto** oppure **Aggiungi nuovo elemento** finestra di dialogo finestre, fare doppio clic su una soluzione aperta in **Esplora soluzioni**, scegliere **Aggiungi**, e quindi fare clic su **nuovo progetto** oppure **nuovo elemento**.  
  
 Procedure guidate possono essere implementate in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per consentire agli utenti di selezionare una visualizzazione struttura ad albero dei valori disponibili quando i colleghi aprono il **Aggiungi nuovo progetto** nella finestra di dialogo o il **Aggiungi nuovo elemento** nella finestra di dialogo o quando sono fare doppio clic su un elemento in **Esplora soluzioni**.  
  
 Nella procedura guidata, è possibile fornire la possibilità di localizzare il nome di un nuovo progetto o ites ed è possibile determinare l'icona visualizzato dagli utenti quando selezionano la procedura guidata. È anche possibile controllare l'ordine in cui vengono visualizzati nuovi elementi relazione agli altri elementi disponibile; gli elementi non sono necessario essere organizzati in ordine alfabetico.  
  
 È anche possibile fornire una procedura guidata che viene avviato in modo diverso, in base ai parametri personalizzati che vengono passati alla procedura guidata quando viene aperto.  
  
 Gli argomenti in questa sezione descrivono i file che implementano per causare il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Aggiungi nuovo progetto** e **Aggiungi nuovo elemento** finestre di dialogo per visualizzare l'elenco tra le procedure guidate disponibili e i modelli, una procedura guidata e i requisiti che deve soddisfare una procedura guidata per funzionare correttamente nell'IDE.  
  
## <a name="in-this-section"></a>In questa sezione  
 [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Viene fornita una panoramica della quale modello file description di directory e spiega come funzionano nell'IDE per visualizzare le cartelle, file VSZ della procedura guidata e i file di modello che sono associati a un progetto nelle finestre di dialogo.  
  
 [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Illustra la modalità di avvio delle procedure guidate l'IDE ed elenca le tre parti del file con estensione vsz.  
  
 [Interfaccia della procedura guidata (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Viene descritto il `IDTWizard` interfaccia che devono implementare le procedure guidate per lavorare in IDE.  
  
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)  
 Illustra le modalità di implementazione delle procedure guidate e ciò che si verifica quando l'IDE passa i parametri di contesto per l'implementazione.  
  
 [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)  
 Viene illustrato come usare i parametri personalizzati per controllare l'operazione della procedura guidata dopo che viene avviata la procedura guidata.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Vengono forniti collegamenti ad argomenti aggiuntivi che offrono informazioni su come progettare nuovi tipi di progetto.  
  
 [Procedura dettagliata: Creazione di una procedura guidata](http://msdn.microsoft.com/library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Viene illustrato come creare una procedura guidata.  
  
 [Estensione dei progetti](../../extensibility/extending-projects.md)  
 Descrive come usare i progetti e le soluzioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per organizzare file di codice e file di risorse e come implementare il controllo del codice sorgente.
