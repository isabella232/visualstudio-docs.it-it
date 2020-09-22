---
title: Aggiornamento di progetti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e838cb02aa1a620356f96d9e77f1752797ac409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839396"
---
# <a name="upgrading-projects"></a>Aggiornamento dei progetti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le modifiche apportate al modello di progetto da una versione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] al successivo possono richiedere l'aggiornamento di progetti e soluzioni in modo che possano essere eseguiti nella versione più recente. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Fornisce interfacce che possono essere utilizzate per implementare il supporto dell'aggiornamento nei propri progetti.  
  
## <a name="upgrade-strategies"></a>Strategie di aggiornamento  
 Per supportare un aggiornamento, l'implementazione del sistema di progetto deve definire e implementare una strategia di aggiornamento. Per determinare la strategia, è possibile scegliere di supportare il backup affiancato (SxS), il backup di copia o entrambi.  
  
- Il backup SxS significa che un progetto copia solo i file che richiedono l'aggiornamento sul posto, aggiungendo un suffisso di nome file appropriato, ad esempio ". old".  
  
- Copia backup significa che un progetto copia tutti gli elementi del progetto in un percorso di backup fornito dall'utente. Vengono quindi aggiornati i file rilevanti nel percorso del progetto originale.  
  
## <a name="how-upgrade-works"></a>Funzionamento dell'aggiornamento  
 Quando una soluzione creata in una versione precedente di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] viene aperta in una versione più recente, l'IDE controlla il file della soluzione per determinare se è necessario aggiornarlo. Se è richiesto l'aggiornamento, l' **aggiornamento guidato** viene avviato automaticamente per esaminare l'utente durante il processo di aggiornamento.  
  
 Quando è necessario aggiornare una soluzione, viene eseguita una query su ogni factory del progetto per la strategia di aggiornamento. La strategia determina se la factory del progetto supporta il backup di copia o di SxS. Le informazioni vengono inviate all' **aggiornamento guidato**, che raccoglie le informazioni necessarie per il backup e presenta le opzioni applicabili all'utente.  
  
### <a name="multi-project-solutions"></a>Soluzioni per più progetti  
 Se una soluzione contiene più progetti e le strategie di aggiornamento sono diverse, ad esempio quando un progetto C++ che supporta solo il backup SxS e un progetto Web che supporta solo il backup di copia, il progetto Factory deve negoziare la strategia di aggiornamento.  
  
 La soluzione esegue una query su ogni factory di progetto per <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Chiama quindi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> per verificare se i file di progetto globali necessitano dell'aggiornamento e per determinare le strategie di aggiornamento supportate. Viene quindi richiamato l' **aggiornamento guidato** .  
  
 Dopo che l'utente ha completato la procedura guidata, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> viene chiamato su ogni factory del progetto per eseguire l'aggiornamento effettivo. Per facilitare il backup, i metodi IVsProjectUpgradeViaFactory forniscono il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> servizio per registrare i dettagli del processo di aggiornamento. Questo servizio non può essere memorizzato nella cache.  
  
 Dopo l'aggiornamento di tutti i file globali rilevanti, ogni factory del progetto può scegliere di creare un'istanza di un progetto. L'implementazione del progetto deve supportare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>Viene quindi chiamato il metodo per aggiornare tutti gli elementi di progetto pertinenti.  
  
> [!NOTE]
> Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodo non fornisce il servizio SVsUpgradeLogger. Questo servizio può essere ottenuto chiamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .  
  
## <a name="best-practices"></a>Procedure consigliate  
 Usare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> servizio per verificare se è possibile modificare un file prima di modificarlo e salvarlo prima di salvarlo. Ciò consentirà alle implementazioni di backup e di aggiornamento di gestire i file di progetto nel controllo del codice sorgente, i file con autorizzazioni insufficienti e così via.  
  
 Utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> servizio durante tutte le fasi di backup e aggiornamento per fornire informazioni sull'esito positivo o negativo del processo di aggiornamento.  
  
 Per ulteriori informazioni sul backup e sull'aggiornamento dei progetti, vedere i commenti per IVsProjectUpgrade in vsshell2. idl.  
  
## <a name="see-also"></a>Vedere anche  
 [Progetti](../../extensibility/internals/projects.md)   
 [Aggiornamento di progetti personalizzati](../../misc/upgrading-custom-projects.md)   
 [Aggiornamento degli elementi di progetto](../../misc/upgrading-project-items.md)
