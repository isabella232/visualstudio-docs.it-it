---
title: Aggiornamento di progetti | Microsoft Docs
description: Informazioni sulle interfacce fornite da Visual Studio SDK per implementare il supporto dell'aggiornamento nei progetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f796668437ac4cb7b529e9d3db66c7aba4325c147da42132cda649199c9063ed
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375637"
---
# <a name="upgrading-projects"></a>Aggiornamento dei progetti

Le modifiche al modello di progetto da una versione di Visual Studio alla successiva potrebbero richiedere l'aggiornamento di progetti e soluzioni in modo che possano essere eseguiti nella versione più recente. fornisce [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfacce che possono essere usate per implementare il supporto dell'aggiornamento nei progetti.

## <a name="upgrade-strategies"></a>Strategie di aggiornamento

Per supportare un aggiornamento, l'implementazione del sistema del progetto deve definire e implementare una strategia di aggiornamento. Per determinare la strategia, è possibile scegliere di supportare il backup side-by-side (SxS), il backup di copia o entrambi.

- Il backup SxS significa che un progetto copia solo i file che necessitano di aggiornamento sul posto, aggiungendo un suffisso del nome file appropriato, ad esempio ".old".

- Copia backup significa che un progetto copia tutti gli elementi del progetto in un percorso di backup fornito dall'utente. I file pertinenti nel percorso del progetto originale vengono quindi aggiornati.

## <a name="how-upgrade-works"></a>Funzionamento dell'aggiornamento

Quando una soluzione creata in una versione precedente di Visual Studio viene aperta in una versione più recente, l'IDE controlla il file della soluzione per determinare se è necessario aggiornarlo. Se è necessario eseguire l'aggiornamento, **l'Aggiornamento guidato** viene avviato automaticamente per illustrare all'utente il processo di aggiornamento.

Quando una soluzione richiede l'aggiornamento, esegue una query su ogni factory del progetto per la strategia di aggiornamento. La strategia determina se la factory del progetto supporta il backup di copia o il backup SxS. Le informazioni vengono inviate **all'Aggiornamento guidato,** che raccoglie le informazioni necessarie per il backup e presenta all'utente le opzioni applicabili.

### <a name="multi-project-solutions"></a>Soluzioni multi-Project

Se una soluzione contiene più progetti e le strategie di aggiornamento sono diverse, ad esempio quando un progetto C++ che supporta solo il backup SxS e un progetto Web che supporta solo il backup di copia, le factory del progetto devono negoziare la strategia di aggiornamento.

La soluzione esegue una query su ogni factory del progetto per <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Chiama quindi per <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> verificare se i file di progetto globali devono essere aggiornati e per determinare le strategie di aggiornamento supportate. Viene **quindi richiamata** l'Aggiornamento guidato.

Dopo che l'utente ha completato la procedura guidata, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> viene chiamato in ogni factory del progetto per eseguire l'aggiornamento effettivo. Per facilitare il backup, i metodi IVsProjectUpgradeViaFactory forniscono il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> servizio per registrare i dettagli del processo di aggiornamento. Questo servizio non può essere memorizzato nella cache.

Dopo aver aggiornato tutti i file globali pertinenti, ogni factory del progetto può scegliere di creare un'istanza di un progetto. L'implementazione del progetto deve supportare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . Viene <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> quindi chiamato il metodo per aggiornare tutti gli elementi di progetto pertinenti.

> [!NOTE]
> Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodo non fornisce il servizio SVsUpgradeLogger. Questo servizio può essere ottenuto chiamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .

## <a name="best-practices"></a>Procedure consigliate

Usare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> servizio per verificare se è possibile modificare un file prima di modificarlo e salvarlo prima di salvarlo. Ciò consente alle implementazioni di backup e aggiornamento di gestire i file di progetto nel controllo del codice sorgente, i file con autorizzazioni insufficienti e così via.

Usare il servizio durante tutte le fasi di backup e aggiornamento per fornire informazioni sull'esito positivo o negativo <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> del processo di aggiornamento.

Per altre informazioni sul backup e l'aggiornamento dei progetti, vedere i commenti per IVsProjectUpgrade in vsshell2.idl.

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a> Aggiornamento di progetti personalizzati

Se si modificano le informazioni rese persistenti nel file di progetto tra diverse versioni di Visual Studio del prodotto, è necessario supportare l'aggiornamento del file di progetto dalla versione precedente a quella nuova. Per supportare l'aggiornamento che consente di partecipare **alla Visual Studio guidata,** implementare l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Questa interfaccia contiene l'unico meccanismo disponibile per l'aggiornamento della copia. L'aggiornamento del progetto viene eseguito all'apertura di una parte della soluzione. L'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> è implementata dalla factory del progetto o almeno deve poter essere ottenuta dalla factory del progetto.

Il meccanismo precedente che usa l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> è ancora supportato, ma concettualmente aggiorna il sistema del progetto come parte del progetto aperto. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>L'interfaccia viene pertanto chiamata dall'ambiente Visual Studio anche se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> l'interfaccia viene chiamata o implementata. Questo approccio consente di usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> per implementare solo le parti della copia e del progetto dell'aggiornamento e delegare il resto del lavoro da eseguire sul posto (possibilmente nella nuova posizione) tramite l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

Per un'implementazione di esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> di , vedere Gli esempi di [VSSDK.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

Con gli aggiornamenti di progetti si verificano i seguenti scenari:

- Se il file è di un formato più recente rispetto a quelli supportati dal progetto, deve restituire un errore che segnala il problema. Si presuppone che la versione precedente del prodotto includa il codice per verificare la versione.

- Se è specificato il flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> nel metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, l'aggiornamento verrà implementato come un aggiornamento sul posto prima dell'apertura del progetto.

- Se è specificato il flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> nel metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, l'aggiornamento viene implementato come un aggiornamento della copia.

- Se è specificato il flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> nella chiamata <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, all'utente è stato richiesto dall'ambiente di aggiornare il file di progetto come un aggiornamento sul posto, dopo l'apertura del progetto. Ad esempio, l'ambiente richiede all'utente di eseguire l'aggiornamento all'apertura di una versione precedente della soluzione.

- Se non è specificato il flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> nella chiamata <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, è necessario richiedere all'utente di aggiornare il file di progetto.

     Di seguito è riportato un esempio di messaggio di richiesta dell'aggiornamento:

     "Il progetto '%1' è stato creato con una versione precedente di Visual Studio. Se si apre il progetto con la versione in uso, potrebbe risultare impossibile aprirlo con le versioni precedenti di Visual Studio. Continuare e aprire il progetto?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Per implementare IVsProjectUpgradeViaFactory

1. Implementare il metodo dell'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, in particolare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> nell'implementazione della factory del progetto, o rendere le implementazioni richiamabili dall'implementazione della factory del progetto.

2. Se si vuole eseguire un aggiornamento sul posto come parte dell'apertura della soluzione, specificare il flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> come parametro `VSPUVF_FLAGS` nell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.

3. Se si vuole eseguire un aggiornamento sul posto come parte dell'apertura della soluzione, specificare il flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> come parametro `VSPUVF_FLAGS` nell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.

4. Per entrambi i passaggi 2 e 3, le operazioni per l'aggiornamento effettivo dei file tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> possono essere implementate come descritto di seguito nella sezione "Implementazione di `IVsProjectUpgade`" oppure è possibile delegare l'aggiornamento effettivo dei file a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

5. Usare i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> per inviare i messaggi relativi all'aggiornamento per l'utente tramite la Migrazione guidata di Visual Studio.

6. L'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> viene usata per implementare qualsiasi tipo di aggiornamento dei file che deve essere eseguito come parte dell'aggiornamento del progetto. Questa interfaccia non viene chiamata da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, ma viene fornita come meccanismo per aggiornare i file che fanno parte del sistema del progetto, ma di cui il sistema del progetto principale potrebbe non essere direttamente a conoscenza. Questa situazione può ad esempio verificarsi se i file e le proprietà relativi al compilatore non vengono gestiti dallo stesso team di sviluppo che gestisce il resto del sistema del progetto.

### <a name="ivsprojectupgrade-implementation"></a>Implementazione di IVsProjectUpgrade

Se il sistema del progetto implementa solo , non può partecipare alla conversione <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> **Visual Studio guidata**. Tuttavia, anche se si implementa l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, è comunque possibile delegare l'aggiornamento dei file all'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

#### <a name="to-implement-ivsprojectupgrade"></a>Per implementare IVsProjectUpgrade

1. Quando un utente tenta di aprire un progetto, il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> è chiamato dall'ambiente dopo che il progetto viene aperto e prima che qualsiasi altra azione dell'utente possa essere eseguita sul progetto. Se all'utente era già stato richiesto di aggiornare la soluzione, viene passato il flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> nel parametro `grfUpgradeFlags`. Se l'utente apre un progetto direttamente, ad esempio usando il comando **Aggiungi Project** esistente, il flag non viene passato e il progetto deve richiedere all'utente di eseguire <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> l'aggiornamento.

2. In risposta alla chiamata <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, il progetto deve valutare se il file di progetto deve essere aggiornato. Se il progetto non deve aggiornare il tipo di progetto a una nuova versione, può semplicemente restituire il flag <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

3. Se il progetto deve aggiornare il tipo di progetto a una nuova versione, deve determinare se il file di progetto può essere modificato chiamando il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passando un valore <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> per il parametro `rgfQueryEdit`. Il progetto deve quindi eseguire le operazioni seguenti:

    - Se il valore `VSQueryEditResult` restituito nel parametro `pfEditCanceled` è <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, l'aggiornamento può continuare perché è possibile eseguire la scrittura del file di progetto.

    - Se il valore `VSQueryEditResult` restituito nel parametro `pfEditCanceled` è <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> e il valore `VSQueryEditResult` ha il bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> impostato, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> deve restituire un errore, perché gli utenti devono risolvere autonomamente il problema di autorizzazioni. Il progetto deve quindi eseguire le operazioni seguenti:

         Segnalare l'errore all'utente chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> e restituire il codice di errore a <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .

    - Se il valore `VSQueryEditResult` è <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> e il valore `VSQueryEditResultFlags` ha il bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> impostato, il file di progetto deve essere estratto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...).

4. Se la chiamata <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> sul file di progetto determina l'estrazione del file e il recupero della versione più recente, il progetto viene scaricato e ricaricato. Il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> viene chiamato nuovamente dopo la creazione di un'altra istanza del progetto. In questa seconda chiamata, il file di progetto può essere scritto sul disco. È consigliabile che il progetto salvi una copia del file di progetto nel formato precedente con un'estensione OLD, apporti le modifiche necessarie per l'aggiornamento e salvi il file di progetto nel nuovo formato. Anche in questo caso, se qualsiasi parte del processo di aggiornamento non riesce, il metodo deve indicare l'errore restituendo <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. Questo determina lo scaricamento del progetto da Esplora soluzioni.

     È importante comprendere l'intero processo che si verifica nell'ambiente qualora la chiamata al metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (che specifica un valore di ReportOnly) restituisca i flag <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> e <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>.

5. L'utente tenta di aprire il file di progetto.

6. L'ambiente chiama l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.

7. Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> restituisce `true`, l'ambiente chiama l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.

8. L'ambiente chiama l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> per aprire il file e inizializzare l'oggetto di progetto, ad esempio Project1.

9. L'ambiente chiama l'implementazione di `IVsProjectUpgrade::UpgradeProject` per determinare se il file di progetto deve essere aggiornato.

10. Si chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e si passa un valore <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> per il parametro `rgfQueryEdit`.

11. L'ambiente restituisce <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> per `VSQueryEditResult` e il bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> è impostato in `VSQueryEditResultFlags`.

12. L'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> chiama `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

Questa chiamata può causare l'estrazione di una nuova copia del file di progetto e il recupero della versione più recente, nonché rendere necessario ricaricare il file di progetto. A questo punto, può verificarsi una delle due situazioni seguenti:

- Se si gestisce autonomamente il ricaricamento del progetto, l'ambiente chiama l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT). Quando si riceve questa chiamata, ricaricare la prima istanza del progetto (Project1) e continuare l'aggiornamento del file di progetto. L'ambiente è consapevole del fatto che si gestisce autonomamente il ricaricamento del progetto se si restituisce `true` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>).

- Se non si gestisce autonomamente il ricaricamento del progetto, si restituisce `false` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). In questo caso, prima che (QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) venga restituito, l'ambiente crea un'altra nuova istanza del progetto, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Project2, come indicato di seguito:

    1. L'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> sul primo oggetto di progetto, Project1, impostando così questo oggetto nello stato inattivo.

    2. L'ambiente chiama l'implementazione di `IVsProjectFactory::CreateProject` per creare una seconda istanza del progetto, Project2.

    3. L'ambiente chiama l'implementazione di `IPersistFileFormat::Load` per aprire il file e inizializzare il secondo oggetto di progetto, Project2.

    4. L'ambiente chiama `IVsProjectUpgrade::UpgradeProject` una seconda volta per determinare se l'oggetto di progetto deve essere aggiornato. Tuttavia, questa chiamata viene eseguita su una nuova, seconda, istanza del progetto, Project2. Si tratta del progetto aperto nella soluzione.

        > [!NOTE]
        > Nel caso il primo progetto, Project1, sia impostato nello stato inattivo, è necessario restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK> dalla prima chiamata nell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>.

    5. Si chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e si passa un valore <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> per il parametro `rgfQueryEdit`.

    6. L'ambiente restituisce <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> e l'aggiornamento può continuare perché è possibile eseguire la scrittura del file di progetto.

Se non è possibile eseguire l'aggiornamento, restituire <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> da `IVsProjectUpgrade::UpgradeProject`. Se non è necessario eseguire l'aggiornamento o si sceglie di non eseguirlo, gestire la chiamata `IVsProjectUpgrade::UpgradeProject` come un'operazione che non produce effetti. Se si restituisce <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, viene aggiunto un nodo segnaposto alla soluzione per il progetto.

## <a name="upgrading-project-items"></a>Aggiornamento degli elementi di progetto

Se si aggiungono o si gestiscono elementi all'interno di sistemi di progetto non implementati, potrebbe essere necessario partecipare al processo di aggiornamento del progetto. Il report Disampli è un esempio di elemento che può essere aggiunto al sistema del progetto.

In genere, gli implementatori di elementi di progetto desiderano sfruttare un progetto già completamente creato e aggiornato perché devono conoscere quali sono i riferimenti al progetto e quali altre proprietà del progetto sono disponibili per prendere una decisione di aggiornamento.

### <a name="to-get-the-project-upgrade-notification"></a>Per ottenere la notifica di aggiornamento del progetto

1. Impostare il <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> flag (definito in vsshell80.idl) nell'implementazione dell'elemento di progetto. In questo modo il pacchetto VSPackage dell'elemento di progetto viene caricato automaticamente quando la shell Visual Studio determina che è in corso l'aggiornamento di un sistema di progetto.

2. Consigliare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> l'interfaccia tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> il metodo .

3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>L'interfaccia viene generato dopo che l'implementazione del sistema del progetto ha completato le operazioni di aggiornamento e dopo la creazione del nuovo progetto aggiornato. A seconda dello scenario, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> l'interfaccia viene generato dopo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> i metodi , o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> .

### <a name="to-upgrade-the-project-item-files"></a>Per aggiornare i file degli elementi di progetto

1. È necessario gestire con attenzione il processo di backup dei file nell'implementazione dell'elemento di progetto. Questo vale in particolare per un backup side-by-side, in cui il parametro del metodo è impostato su , dove i file di cui è stato eseguito il backup vengono posizionati insieme ai file affiancati designati `fUpgradeFlag` <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> come <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> ".old". I file di cui è stato eseguito il backup precedenti all'ora di sistema in cui è stato aggiornato il progetto possono essere designati come non aggiornati. Inoltre, potrebbero essere sovrascritti a meno che non si eservino passaggi specifici per evitare questo problema.

2. Nel momento in cui l'elemento di progetto riceve una notifica dell'aggiornamento del progetto, viene comunque visualizzata Visual Studio **conversione** guidata. Pertanto, è consigliabile usare i metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> dell'interfaccia per fornire messaggi di aggiornamento all'interfaccia utente della procedura guidata.

## <a name="see-also"></a>Vedi anche

- [Progetti](../../extensibility/internals/projects.md)
