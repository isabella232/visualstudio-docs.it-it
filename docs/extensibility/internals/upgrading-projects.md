---
title: Aggiornamento di progetti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea5c29819d0035e45f97122fd108ea1f51d60806
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057534"
---
# <a name="upgrading-projects"></a>Aggiornamento dei progetti

Modifiche al modello di progetto da una versione di Visual Studio al successivo possono richiedere che i progetti e soluzioni di essere aggiornato in modo che eseguano la versione più recente. Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fornisce interfacce che possono essere utilizzate per implementare il supporto di aggiornamento nei propri progetti.

## <a name="upgrade-strategies"></a>Strategie di aggiornamento

Per supportare un aggiornamento, l'implementazione di sistema di progetto è necessario definire e implementare una strategia di aggiornamento. Per determinare la strategia, è possibile scegliere per il supporto side-by-side (SxS) backup, backup di copia o entrambi.

-   Backup SxS significa che un progetto copia solo i file che richiedono l'aggiornamento sul posto, aggiungendo un suffisso di nome file appropriato, ad esempio, "old".

-   Backup di copia indica che un progetto copia tutti gli elementi di progetto in un percorso di backup fornito dall'utente. Quindi vengono aggiornati i file presenti nel percorso progetto originale.

## <a name="how-upgrade-works"></a>Come funziona l'aggiornamento

Quando una soluzione creata in una versione precedente di Visual Studio viene aperto in una versione più recente, l'IDE controlla il file di soluzione per determinare se deve essere aggiornato. Se l'aggiornamento è obbligatorio, il **aggiornamento guidato** viene avviato automaticamente per guidare l'utente attraverso il processo di aggiornamento.

Quando una soluzione richiede l'aggiornamento, viene eseguita una query ogni factory di progetto per la propria strategia di aggiornamento. La strategia determina se la factory del progetto supporta il backup di copia o SxS. Le informazioni vengono inviate per il **aggiornamento guidato**, che raccoglie le informazioni necessarie per il backup e presenta le opzioni applicabili all'utente.

### <a name="multi-project-solutions"></a>Soluzioni multiprogetto

Se una soluzione contiene più progetti e le strategie di aggiornamento sono diversi, ad esempio quando un progetto C++ che supporta solo backup SxS e un progetto Web che supportano solo backup di copia, le factory di progetto devono negoziare la strategia di aggiornamento.

La soluzione esegue una query ogni factory di progetto per <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Chiama quindi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> per verificare se i file di progetto globale è necessario l'aggiornamento e per determinare le strategie di aggiornamento supportate. Il **aggiornamento guidato** viene quindi richiamato.

Dopo che l'utente ha completato la procedura guidata, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> viene chiamato su ogni factory di progetto per eseguire l'aggiornamento effettivo. Per facilitare il backup, i metodi IVsProjectUpgradeViaFactory forniscono il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> servizio per registrare i dettagli del processo di aggiornamento. Questo servizio non può essere memorizzato nella cache.

Dopo aver aggiornato tutti i file globali pertinenti, ogni factory di progetto è possibile scegliere di creare un'istanza di un progetto. L'implementazione di progetto deve supportare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> viene quindi chiamato il metodo per eseguire l'aggiornamento di tutti gli elementi di progetto pertinenti.

> [!NOTE]
> Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> (metodo) non è incluso il servizio SVsUpgradeLogger. Questo servizio può essere ottenuto chiamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.

## <a name="best-practices"></a>Suggerimenti

Usare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> servizio per verificare se è possibile modificare un file prima di modificarlo e possibile salvare il file prima di salvarlo. Ciò consentirà il backup e aggiornamento implementazioni consentono di gestire i file di progetto in controllo del codice sorgente, i file con autorizzazioni insufficienti e così via.

Usare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> durante tutte le fasi del backup del servizio e di aggiornamento per fornire informazioni sull'esito positivo o negativo del processo di aggiornamento.

Per altre informazioni sul backup e l'aggiornamento di progetti, vedere i commenti per IVsProjectUpgrade in vsshell2.idl.

## <a name="upgrading-custom-projects"></a> Aggiornamento di progetti personalizzati

Se si modificano le informazioni rese persistenti nel file di progetto tra diverse versioni di Visual Studio del prodotto, è necessario supportare l'aggiornamento del file di progetto dalla versione precedente a quella nuova. Per supportare l'aggiornamento che consente di partecipare le **conversione guidata di Visual Studio**, implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaccia. Questa interfaccia contiene l'unico meccanismo disponibile per l'aggiornamento della copia. L'aggiornamento del progetto viene eseguito all'apertura di una parte della soluzione. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaccia viene implementata dalla factory del progetto, o almeno deve essere ottenuta dalla factory del progetto.

Il meccanismo precedente che usa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaccia è ancora supportata, ma concettualmente aggiorna il sistema del progetto come parte del progetto aperto. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaccia viene pertanto chiamata di Visual Studio ambiente anche se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaccia è chiamata o implementata. Questo approccio consente di usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> per implementare la copia solo le parti dell'aggiornamento del progetto e delegare il resto del lavoro da eseguire sul posto (possibilmente nella nuova posizione) di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaccia.

Per un esempio di implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, vedere [esempi di VSSDK](http://aka.ms/vs2015sdksamples).

Con gli aggiornamenti di progetti si verificano i seguenti scenari:

-   Se il file è di un formato più recente rispetto a quelli supportati dal progetto, deve restituire un errore che segnala il problema. Ciò presuppone che la versione precedente del prodotto include codice per verificare la versione.

-   Se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> flag è specificato nella <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodo, l'aggiornamento verrà implementato come un aggiornamento sul posto prima dell'apertura del progetto.

-   Se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> flag è specificato nella <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodo, l'aggiornamento viene implementato come un aggiornamento della copia.

-   Se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> flag è specificato nella <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chiama, quindi all'utente è stato richiesto dall'ambiente di aggiornare il file di progetto come un aggiornamento sul posto, dopo che il progetto è aperto. Ad esempio, l'ambiente richiede all'utente di eseguire l'aggiornamento all'apertura di una versione precedente della soluzione.

-   Se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> flag non è specificato nella <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chiamare, è necessario richiedere all'utente di aggiornare il file di progetto.

     Di seguito è riportato un esempio di messaggio di richiesta dell'aggiornamento:

     "Il progetto '%1' è stato creato con una versione precedente di Visual Studio. Se si apre il progetto con la versione in uso, potrebbe risultare impossibile aprirlo con le versioni precedenti di Visual Studio. Continuare e aprire il progetto?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Per implementare IVsProjectUpgradeViaFactory

1.  Implementare il metodo del <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> dell'interfaccia, in particolare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodo nell'implementazione della factory di progetto, o rendere le implementazioni richiamabili dall'implementazione della factory progetto.

2.  Se si desidera eseguire un aggiornamento sul posto come parte dell'apertura della soluzione, specificare il flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> come il `VSPUVF_FLAGS` parametri in di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementazione.

3.  Se si desidera eseguire un aggiornamento sul posto come parte dell'apertura della soluzione, specificare il flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> come il `VSPUVF_FLAGS` parametri in di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementazione.

4.  Per entrambi i passaggi 2 e 3, il file effettivo aggiornamento passaggi, usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, può essere implementato come descritto nel "implementazione `IVsProjectUpgade`" sezione di seguito, oppure è possibile delegare l'aggiornamento effettivo dei file per <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

5.  Usare i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> alla fase successiva all'aggiornamento correlati i messaggi per l'utente usando migrazione guidata di Visual Studio.

6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> interfaccia viene utilizzata per implementare qualsiasi tipo di aggiornamento dei file che deve essere eseguito come parte di aggiornamento del progetto. Questa interfaccia non viene chiamata da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, ma viene fornita come un meccanismo per aggiornare i file che fanno parte del sistema del progetto, ma il sistema di progetto principale potrebbe non essere direttamente a conoscenza. Questa situazione può ad esempio verificarsi se i file e le proprietà relativi al compilatore non vengono gestiti dallo stesso team di sviluppo che gestisce il resto del sistema del progetto.

### <a name="ivsprojectupgrade-implementation"></a>Implementazione di IVsProjectUpgrade

Se il sistema di progetto implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> , possa non partecipare solo le **conversione guidata di Visual Studio**. Tuttavia, anche se si implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaccia, è comunque possibile delegare l'aggiornamento di file a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementazione.

#### <a name="to-implement-ivsprojectupgrade"></a>Per implementare IVsProjectUpgrade

1.  Quando un utente tenta di aprire un progetto, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metodo viene chiamato dall'ambiente dopo che il progetto viene aperto e prima di qualsiasi altro utente azione può essere eseguita nel progetto. Se l'utente era già stato richiesto di aggiornare la soluzione, il <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> flag viene passato il `grfUpgradeFlags` parametro. Se l'utente apre un progetto direttamente, tale esempio usando il **Aggiungi progetto esistente** comando, il <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> flag non viene passato e il progetto deve richiedere all'utente di eseguire l'aggiornamento.

2.  In risposta al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chiamata, il progetto deve valutare se il file di progetto è aggiornato. Se il progetto non è necessario aggiornare il tipo di progetto a una nuova versione, quindi può semplicemente restituire la <xref:Microsoft.VisualStudio.VSConstants.S_OK> flag.

3.  Se il progetto deve aggiornare il tipo di progetto a una nuova versione, quindi deve determinare se il file di progetto può essere modificato chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metodo e passando un valore di <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> per il `rgfQueryEdit` parametro. Il progetto deve quindi eseguire le operazioni seguenti:

    -   Se il `VSQueryEditResult` valore restituito nel `pfEditCanceled` parametro è <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, quindi l'aggiornamento può continuare perché il file di progetto può essere scritti.

    -   Se il `VSQueryEditResult` valore restituito nel `pfEditCanceled` parametro è <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> e il `VSQueryEditResult` valore ha la <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> bit impostato, quindi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> deve restituire un errore, perché gli utenti devono risolvere il problema di autorizzazioni autonomamente. Il progetto deve quindi eseguire le operazioni seguenti:

         Segnalare l'errore all'utente chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> e restituire il <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> codice di errore <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

    -   Se il `VSQueryEditResult` valore è <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> e il `VSQueryEditResultFlags` ha valore il <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bit impostato, quindi il file di progetto deve essere estratto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...).

4.  Se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> chiamata sul file di progetto fa sì che il file da estrarre e la versione più recente deve essere recuperato, quindi il progetto viene scaricato e ricaricato. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metodo viene chiamato nuovamente dopo aver creata un'altra istanza del progetto. In questa seconda chiamata, il file di progetto può essere scritto sul disco. È consigliabile che il progetto salvi una copia del file di progetto nel formato precedente con un'estensione OLD, apporti le modifiche necessarie per l'aggiornamento e salvi il file di progetto nel nuovo formato. Anche in questo caso, se qualsiasi parte del processo di aggiornamento non riesce, il metodo deve indicare l'esito negativo restituendo <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. Questo determina lo scaricamento del progetto da Esplora soluzioni.

     È importante comprendere l'intero processo che si verifica nell'ambiente per il caso in cui la chiamata ai <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metodo (specificando un valore di ReportOnly) restituisce il <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> e il <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> flag.

5.  L'utente tenta di aprire il file di progetto.

6.  L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementazione.

7.  Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> restituisce `true`, quindi l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementazione.

8.  L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementazione per aprire il file e inizializzare l'oggetto di progetto, ad esempio Project1.

9. L'ambiente chiama l'implementazione di `IVsProjectUpgrade::UpgradeProject` per determinare se il file di progetto deve essere aggiornato.

10. Si chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passare un valore di <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> per il `rgfQueryEdit` parametro.

11. L'ambiente restituisce <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> per `VSQueryEditResult` e il <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bit viene impostato `VSQueryEditResultFlags`.

12. I <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> viene chiamato dall'implementazione `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

Questa chiamata può causare l'estrazione di una nuova copia del file di progetto e il recupero della versione più recente, nonché rendere necessario ricaricare il file di progetto. A questo punto, può verificarsi una delle due situazioni seguenti:

-   Se si gestisce autonomamente il ricaricamento progetto, quindi l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementazione (VSITEMID_ROOT). Quando si riceve questa chiamata, ricaricare la prima istanza del progetto (Project1) e continuare l'aggiornamento del file di progetto. L'ambiente sa che si gestisce il proprio ricaricamento del progetto se si torna `true` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>).

-   Se non si gestisce autonomamente il ricaricamento progetto, quindi è tornare `false` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). In questo caso, prima <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) viene restituito, l'ambiente crea un'altra nuova istanza del progetto, ad esempio Project2, come indicato di seguito:

    1.  L'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> sul primo oggetto di progetto, Project1, tal modo posizionando l'oggetto nello stato inattivo.

    2.  L'ambiente chiama l'implementazione di `IVsProjectFactory::CreateProject` per creare una seconda istanza del progetto, Project2.

    3.  L'ambiente chiama l'implementazione di `IPersistFileFormat::Load` per aprire il file e inizializzare il secondo oggetto di progetto, Project2.

    4.  L'ambiente chiama `IVsProjectUpgrade::UpgradeProject` una seconda volta per determinare se l'oggetto di progetto deve essere aggiornato. Tuttavia, questa chiamata viene eseguita su una nuova, seconda, istanza del progetto, Project2. Si tratta del progetto aperto nella soluzione.

        > [!NOTE]
        > Nell'istanza che viene inserito il primo progetto, Project1, nello stato inattivo, quindi è necessario restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK> dalla prima chiamata ai <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementazione.

    5.  Si chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passare un valore di <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> per il `rgfQueryEdit` parametro.

    6.  L'ambiente restituisce <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> e l'aggiornamento può continuare perché il file di progetto può essere scritti.

Se non si riesce a eseguire l'aggiornamento, restituire <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> da `IVsProjectUpgrade::UpgradeProject`. Se non è necessario eseguire l'aggiornamento o si sceglie di non eseguirlo, gestire la chiamata `IVsProjectUpgrade::UpgradeProject` come un'operazione che non produce effetti. Se si torna <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, viene aggiunto un nodo segnaposto alla soluzione per il progetto.

## <a name="upgrading-project-items"></a>Aggiornamento degli elementi di progetto

Se si aggiungono o gestire gli elementi all'interno di sistemi di progetto non viene implementato, devi partecipare al processo di aggiornamento del progetto. Crystal Reports è un esempio di un elemento che è possibile aggiungere al sistema del progetto.

In genere, gli implementatori di elemento di progetto vuole sfruttare un progetto già completamente un'istanza e l'aggiornamento perché è necessario conoscere il progetto sono riferimenti e quali altre proprietà del progetto sono presenti per prendere una decisione di aggiornamento.

### <a name="to-get-the-project-upgrade-notification"></a>Per ricevere le notifiche di aggiornamento progetto

1.  Impostare il <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> flag (definito in vsshell80.idl) nell'implementazione dell'elemento di progetto. In questo modo l'elemento di progetto VSPackage per caricamento automatico quando la shell di Visual Studio determina che un sistema di progetto è in corso l'aggiornamento.

2.  Consigliare la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaccia tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> (metodo).

3.  Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaccia viene generata dopo che l'implementazione di sistema di progetto completamento delle operazioni di aggiornamento e viene creato il nuovo progetto aggiornato. A seconda dello scenario, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaccia viene attivata dopo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> metodi.

### <a name="to-upgrade-the-project-item-files"></a>Per aggiornare i file di elemento di progetto

1.  È necessario gestire attentamente il processo di backup di file nell'implementazione dell'elemento di progetto. Questo vale in particolare per il backup side-by-side, in cui il `fUpgradeFlag` parametro del <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodo è impostato su <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, in cui vengono inseriti i file che erano stato eseguito il backup insieme file lato designati come "old". I file di backup meno recenti rispetto all'ora di sistema quando il progetto è stato aggiornato possono essere designati come obsoleti. Inoltre, potrebbe essere sovrascritto a meno che non si accettano i passaggi dettagliati per evitare questo problema.

2.  Al momento l'elemento di progetto riceve una notifica di aggiornamento del progetto, il **conversione guidata di Visual Studio** continuerà a essere visualizzato. Pertanto, è necessario utilizzare i metodi del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interfaccia per fornire messaggi di aggiornamento per la procedura guidata dell'interfaccia utente.

## <a name="see-also"></a>Vedere anche

- [Progetti](../../extensibility/internals/projects.md)