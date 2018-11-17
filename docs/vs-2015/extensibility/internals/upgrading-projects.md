---
title: Aggiornamento di progetti | Microsoft Docs
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
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a3f045d947f968655923df16de8c02aafc12a34b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783761"
---
# <a name="upgrading-projects"></a>Aggiornamento dei progetti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Modifiche al modello di progetto da una versione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] alla successiva potrebbe essere necessario aggiornare i progetti e soluzioni in modo che eseguano la versione più recente. Il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] fornisce interfacce che possono essere utilizzate per implementare il supporto di aggiornamento nei propri progetti.  
  
## <a name="upgrade-strategies"></a>Strategie di aggiornamento  
 Per supportare un aggiornamento, l'implementazione di sistema di progetto è necessario definire e implementare una strategia di aggiornamento. Per determinare la strategia, è possibile scegliere per il supporto side-by-side (SxS) backup, backup di copia o entrambi.  
  
-   Backup SxS significa che un progetto copia solo i file che richiedono l'aggiornamento sul posto, aggiungendo un suffisso di nome file appropriato, ad esempio, "old".  
  
-   Backup di copia indica che un progetto copia tutti gli elementi di progetto in un percorso di backup fornito dall'utente. Quindi vengono aggiornati i file presenti nel percorso progetto originale.  
  
## <a name="how-upgrade-works"></a>Come funziona l'aggiornamento  
 Quando una soluzione creata in una versione precedente di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] viene aperto in una versione più recente, i controlli di IDE la soluzione di file per determinare se deve essere aggiornato. Se l'aggiornamento è obbligatorio, il **aggiornamento guidato** viene avviato automaticamente per guidare l'utente attraverso il processo di aggiornamento.  
  
 Quando una soluzione richiede l'aggiornamento, viene eseguita una query ogni factory di progetto per la propria strategia di aggiornamento. La strategia determina se la factory del progetto supporta il backup di copia o SxS. Le informazioni vengono inviate per il **aggiornamento guidato**, che raccoglie le informazioni necessarie per il backup e presenta le opzioni applicabili all'utente.  
  
### <a name="multi-project-solutions"></a>Soluzioni multiprogetto  
 Se una soluzione contiene più progetti e le strategie di aggiornamento sono diversi, ad esempio quando un progetto C++ che supporta solo backup SxS e un progetto Web che supportano solo backup di copia, le factory di progetto devono negoziare la strategia di aggiornamento.  
  
 La soluzione esegue una query ogni factory di progetto per <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Chiama quindi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> per verificare se i file di progetto globale è necessario l'aggiornamento e per determinare le strategie di aggiornamento supportate. Il **aggiornamento guidato** viene quindi richiamato.  
  
 Dopo che l'utente ha completato la procedura guidata, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> viene chiamato su ogni factory di progetto per eseguire l'aggiornamento effettivo. Per facilitare il backup, i metodi IVsProjectUpgradeViaFactory forniscono il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> servizio per registrare i dettagli del processo di aggiornamento. Questo servizio non può essere memorizzato nella cache.  
  
 Dopo aver aggiornato tutti i file globali pertinenti, ogni factory di progetto è possibile scegliere di creare un'istanza di un progetto. L'implementazione di progetto deve supportare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> viene quindi chiamato il metodo per eseguire l'aggiornamento di tutti gli elementi di progetto pertinenti.  
  
> [!NOTE]
>  Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> (metodo) non è incluso il servizio SVsUpgradeLogger. Questo servizio può essere ottenuto chiamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## <a name="best-practices"></a>Suggerimenti  
 Usare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> servizio per verificare se è possibile modificare un file prima di modificarlo e possibile salvare il file prima di salvarlo. Ciò consentirà il backup e aggiornamento implementazioni consentono di gestire i file di progetto in controllo del codice sorgente, i file con autorizzazioni insufficienti e così via.  
  
 Usare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> durante tutte le fasi del backup del servizio e di aggiornamento per fornire informazioni sull'esito positivo o negativo del processo di aggiornamento.  
  
 Per altre informazioni sul backup e l'aggiornamento di progetti, vedere i commenti per IVsProjectUpgrade in vsshell2.idl.  
  
## <a name="see-also"></a>Vedere anche  
 [Progetti](../../extensibility/internals/projects.md)   
 [Aggiornamento di progetti personalizzati](../../misc/upgrading-custom-projects.md)   
 [Aggiornamento degli elementi di progetto](../../misc/upgrading-project-items.md)

