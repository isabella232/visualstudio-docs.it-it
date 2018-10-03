---
title: Aggiornamento di progetti personalizzati | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: douge
ms.openlocfilehash: 5c3fd31cfc7cfbf3f7dd687d38483f5bb62703ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528584"
---
# <a name="upgrading-custom-projects"></a>Aggiornamento di progetti personalizzati
Se si modificano le informazioni rese persistenti nel file di progetto tra diverse versioni di Visual Studio del prodotto, è necessario supportare l'aggiornamento del file di progetto dalla versione precedente a quella nuova. Per supportare l'aggiornamento che consente di partecipare le **conversione guidata di Visual Studio**, implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaccia. Questa interfaccia contiene l'unico meccanismo disponibile per l'aggiornamento della copia. L'aggiornamento del progetto viene eseguito all'apertura di una parte della soluzione. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaccia viene implementata dalla factory del progetto, o almeno deve essere ottenuta dalla factory del progetto.  
  
 Il meccanismo precedente che usa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaccia è ancora supportata, ma concettualmente aggiorna il sistema del progetto come parte del progetto aperto. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaccia viene pertanto chiamata dal [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente anche se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaccia è chiamata o implementata. Questo approccio consente di usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> per implementare la copia solo le parti dell'aggiornamento del progetto e delegare il resto del lavoro da eseguire sul posto (possibilmente nella nuova posizione) di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaccia.  
  
 Per un esempio di implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, vedere [esempi di VSSDK](../misc/vssdk-samples.md).  
  
 Con gli aggiornamenti di progetti si verificano i seguenti scenari:  
  
-   Se il file è di un formato più recente rispetto a quelli supportati dal progetto, deve restituire un errore che segnala il problema. Questo comportamento presuppone che la versione precedente del prodotto, ad esempio Visual Studio .NET 2003, includa il codice per verificare la versione.  
  
-   Se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> flag è specificato nella <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodo, l'aggiornamento verrà implementato come un aggiornamento sul posto prima dell'apertura del progetto.  
  
-   Se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> flag è specificato nella <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodo, l'aggiornamento viene implementato come un aggiornamento della copia.  
  
-   Se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flag è specificato nella <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chiama, quindi all'utente è stato richiesto dall'ambiente di aggiornare il file di progetto come un aggiornamento sul posto, dopo che il progetto è aperto. Ad esempio, l'ambiente richiede all'utente di eseguire l'aggiornamento all'apertura di una versione precedente della soluzione.  
  
-   Se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flag non è specificato nella <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chiamare, è necessario richiedere all'utente di aggiornare il file di progetto.  
  
     Di seguito è riportato un esempio di messaggio di richiesta dell'aggiornamento:  
  
     "Il progetto '%1' è stato creato con una versione precedente di Visual Studio. Se si apre il progetto con la versione in uso, potrebbe risultare impossibile aprirlo con le versioni precedenti di Visual Studio. Continuare e aprire il progetto?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Per implementare IVsProjectUpgradeViaFactory  
  
1.  Implementare il metodo del <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> dell'interfaccia, in particolare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodo nell'implementazione della factory di progetto, o rendere le implementazioni richiamabili dall'implementazione della factory progetto.  
  
2.  Se si desidera eseguire un aggiornamento sul posto come parte dell'apertura della soluzione, specificare il flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> come il `VSPUVF_FLAGS` parametri in di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementazione.  
  
3.  Se si desidera eseguire un aggiornamento sul posto come parte dell'apertura della soluzione, specificare il flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> come il `VSPUVF_FLAGS` parametri in di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementazione.  
  
4.  Per entrambi i passaggi 2 e 3, il file effettivo aggiornamento passaggi, usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, può essere implementato come descritto nel "implementazione `IVsProjectUpgade`" sezione di seguito, oppure è possibile delegare l'aggiornamento effettivo dei file per <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5.  Usare i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> alla fase successiva all'aggiornamento correlati i messaggi per l'utente usando migrazione guidata di Visual Studio.  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> interfaccia viene utilizzata per implementare qualsiasi tipo di aggiornamento dei file che deve essere eseguito come parte di aggiornamento del progetto. Questa interfaccia non viene chiamata da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, ma viene fornita come un meccanismo per aggiornare i file che fanno parte del sistema del progetto, ma il sistema di progetto principale potrebbe non essere direttamente a conoscenza. Questa situazione può ad esempio verificarsi se i file e le proprietà relativi al compilatore non vengono gestiti dallo stesso team di sviluppo che gestisce il resto del sistema del progetto.  
  
## <a name="ivsprojectupgrade-implementation"></a>Implementazione di IVsProjectUpgrade  
 Se il sistema di progetto implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> , possa non partecipare solo le **conversione guidata di Visual Studio**. Tuttavia, anche se si implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaccia, è comunque possibile delegare l'aggiornamento di file a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementazione.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Per implementare IVsProjectUpgrade  
  
1.  Quando un utente tenta di aprire un progetto, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metodo viene chiamato dall'ambiente dopo che il progetto viene aperto e prima di qualsiasi altro utente azione può essere eseguita nel progetto. Se l'utente era già stato richiesto di aggiornare la soluzione, il <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flag viene passato il `grfUpgradeFlags` parametro. Se l'utente apre un progetto direttamente, tale esempio usando il **Aggiungi progetto esistente** comando, il <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flag non viene passato e il progetto deve richiedere all'utente di eseguire l'aggiornamento.  
  
2.  In risposta al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chiamata, il progetto deve valutare se il file di progetto è aggiornato. Se il progetto non è necessario aggiornare il tipo di progetto a una nuova versione, quindi può semplicemente restituire la <xref:Microsoft.VisualStudio.VSConstants.S_OK> flag.  
  
3.  Se il progetto deve aggiornare il tipo di progetto a una nuova versione, quindi deve determinare se il file di progetto può essere modificato chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metodo e passando un valore di <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> per il `rgfQueryEdit` parametro. Il progetto deve quindi eseguire le operazioni seguenti:  
  
    -   Se il `VSQueryEditResult` valore restituito nel `pfEditCanceled` parametro è <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, quindi l'aggiornamento può continuare perché il file di progetto può essere scritti.  
  
    -   Se il `VSQueryEditResult` valore restituito nel `pfEditCanceled` parametro è <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e il `VSQueryEditResult` valore ha la <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit impostato, quindi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> deve restituire un errore, perché gli utenti devono risolvere il problema di autorizzazioni autonomamente. Il progetto deve quindi eseguire le operazioni seguenti:  
  
         Segnalare l'errore all'utente chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>. e restituire il <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> codice di errore <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
    -   Se il `VSQueryEditResult` valore è <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e il `VSQueryEditResultFlags` ha valore il <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit impostato, quindi il file di progetto deve essere estratto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...).  
  
4.  Se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> chiamata sul file di progetto fa sì che il file da estrarre e la versione più recente deve essere recuperato, quindi il progetto viene scaricato e ricaricato. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metodo viene chiamato nuovamente dopo aver creata un'altra istanza del progetto. In questa seconda chiamata, il file di progetto può essere scritto sul disco. È consigliabile che il progetto salvi una copia del file di progetto nel formato precedente con un'estensione OLD, apporti le modifiche necessarie per l'aggiornamento e salvi il file di progetto nel nuovo formato. Anche in questo caso, se qualsiasi parte del processo di aggiornamento non riesce, il metodo deve indicare l'esito negativo restituendo <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Questo determina lo scaricamento del progetto da Esplora soluzioni.  
  
     È importante comprendere l'intero processo che si verifica nell'ambiente per il caso in cui la chiamata ai <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metodo (specificando un valore di ReportOnly) restituisce il <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e il <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> flag.  
  
5.  L'utente tenta di aprire il file di progetto.  
  
6.  L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementazione.  
  
7.  Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> restituisce `true`, quindi l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementazione.  
  
8.  L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementazione per aprire il file e inizializzare l'oggetto di progetto, ad esempio Project1.  
  
9. L'ambiente chiama l'implementazione di `IVsProjectUpgrade::UpgradeProject` per determinare se il file di progetto deve essere aggiornato.  
  
10. Si chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passare un valore di <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> per il `rgfQueryEdit` parametro.  
  
11. L'ambiente restituisce <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> per `VSQueryEditResult` e il <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit viene impostato `VSQueryEditResultFlags`.  
  
12. I <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> viene chiamato dall'implementazione `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
 Questa chiamata può causare l'estrazione di una nuova copia del file di progetto e il recupero della versione più recente, nonché rendere necessario ricaricare il file di progetto. A questo punto, può verificarsi una delle due situazioni seguenti:  
  
-   Se si gestisce autonomamente il ricaricamento progetto, quindi l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementazione (VSITEMID_ROOT). Quando si riceve questa chiamata, ricaricare la prima istanza del progetto (Project1) e continuare l'aggiornamento del file di progetto. L'ambiente sa che si gestisce il proprio ricaricamento del progetto se si torna `true` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
-   Se non si gestisce autonomamente il ricaricamento progetto, quindi è tornare `false` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). In questo caso, prima <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>([QEF_ForceEdit_NoPrompting](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True), [QEF_DisallowInMemoryEdits](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True),) viene restituito, l'ambiente crea un'altra nuova istanza del progetto, ad esempio Project2, come di seguito:  
  
    1.  L'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> sul primo oggetto di progetto, Project1, tal modo posizionando l'oggetto nello stato inattivo.  
  
    2.  L'ambiente chiama l'implementazione di `IVsProjectFactory::CreateProject` per creare una seconda istanza del progetto, Project2.  
  
    3.  L'ambiente chiama l'implementazione di `IPersistFileFormat::Load` per aprire il file e inizializzare il secondo oggetto di progetto, Project2.  
  
    4.  L'ambiente chiama `IVsProjectUpgrade::UpgradeProject` una seconda volta per determinare se l'oggetto di progetto deve essere aggiornato. Tuttavia, questa chiamata viene eseguita su una nuova, seconda, istanza del progetto, Project2. Si tratta del progetto aperto nella soluzione.  
  
        > [!NOTE]
        >  Nell'istanza che viene inserito il primo progetto, Project1, nello stato inattivo, quindi è necessario restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK> dalla prima chiamata ai <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementazione. Visualizzare [progetto di base](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) per l'implementazione di `IVsProjectUpgrade::UpgradeProject`.  
  
    5.  Si chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passare un valore di <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> per il `rgfQueryEdit` parametro.  
  
    6.  L'ambiente restituisce <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e l'aggiornamento può continuare perché il file di progetto può essere scritti.  
  
 Se non si riesce a eseguire l'aggiornamento, restituire <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> da `IVsProjectUpgrade::UpgradeProject`. Se non è necessario eseguire l'aggiornamento o si sceglie di non eseguirlo, gestire la chiamata `IVsProjectUpgrade::UpgradeProject` come un'operazione che non produce effetti. Se si torna <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, viene aggiunto un nodo segnaposto alla soluzione per il progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Conversione guidata di Visual Studio](http://msdn.microsoft.com/en-us/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Aggiornamento degli elementi di progetto](../misc/upgrading-project-items.md)   
 [Progetti](../extensibility/internals/projects.md)