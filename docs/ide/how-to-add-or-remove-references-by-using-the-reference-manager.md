---
title: Aggiungere riferimenti in Gestione riferimenti
description: Informazioni su come usare la finestra di dialogo Gestione riferimenti per aggiungere e gestire i riferimenti ai componenti sviluppati.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: how-to
helpviewer_keywords:
- C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 552ec8364bb58b72199bacecca99283303eb174c
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924916"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Procedura: Aggiungere o rimuovere riferimenti tramite Gestione riferimenti

È possibile usare la finestra di dialogo Gestione riferimenti per aggiungere e gestire riferimenti a componenti sviluppati da sviluppatori, da Microsoft o da altre società. Se si sviluppa un’app Universal Windows, il progetto fa riferimento automaticamente a tutte le DLL SDK Windows corrette. Se si sviluppa un'applicazione .NET, il progetto fa automaticamente riferimentomscorlib.dll *.* Alcune API .NET vengono esposte nei componenti che è necessario aggiungere manualmente. I riferimenti ai componenti COM o ai componenti personalizzati devono essere aggiunti manualmente.

## <a name="reference-manager-dialog-box"></a>Finestra di dialogo Gestione riferimenti

Sul lato sinistro della finestra di dialogo Gestione riferimenti sono disponibili categorie diverse a seconda del tipo di progetto:

- **Assembly** con i sottogruppi **Framework** ed **Estensioni**

- **COM** elenca tutti i componenti COM disponibili per il riferimento

- **Progetti**

- **Progetti condivisi**

- **Windows** con i sottogruppi **Core** ed **Estensioni**. È possibile esplorare i riferimenti in Windows SDK o negli SDK di estensione tramite il **visualizzatore oggetti**.

- **Sfoglia** con il sottogruppo **Recenti**
 
    > [!NOTE]
    > Se si sviluppano **progetti** C++, è possibile che l'opzione Sfoglia non venga visualizzata nella finestra di dialogo Gestione riferimenti .

## <a name="add-a-reference"></a>Aggiungere un riferimento

1. In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul nodo **Riferimento** o **Dipendenze** e scegliere **Aggiungi riferimento**. È anche possibile fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **riferimento**.

   Verrà visualizzata la finestra della **Gestione riferimenti** che elenca i riferimenti disponibili in base al gruppo.

2. Specificare i riferimenti da aggiungere e scegliere **OK**.

## <a name="assemblies-tab"></a>Scheda Assembly

La scheda **Assembly** elenca tutti gli assembly .NET disponibili per riferimento. Nella scheda **Assembly** non vengono elencati gli assembly della Global Assembly Cache (GAC) in quanto questi assembly fanno parte dell'ambiente di runtime. Se si distribuisce o si copia un'applicazione che contiene un riferimento a un assembly registrato nella Global Assembly Cache, l'assembly non verrà distribuito o copiato con l'applicazione, indipendentemente dall'impostazione Copia **locale.** Per altre informazioni, vedere [Gestire i riferimenti in un progetto](../ide/managing-references-in-a-project.md).

Quando si aggiunge manualmente un riferimento a qualsiasi spazio dei nomi EnvDTE (<xref:EnvDTE>, <xref:EnvDTE80>, <xref:EnvDTE90>, <xref:EnvDTE90a> o <xref:EnvDTE100>), impostare la proprietà **Incorpora tipi di interoperabilità** del riferimento su **False** nella finestra **Proprietà**. L'impostazione di questa **proprietà su True** può causare problemi di compilazione a causa di determinate proprietà EnvDTE che non possono essere incorporate.

Tutti i progetti desktop contengono un riferimento implicito a **mscorlib**. I progetti Visual Basic contengono un riferimento implicito a <xref:Microsoft.VisualBasic>. Tutti i progetti contengono un riferimento implicito a **System.Core**, anche se è stato rimosso dall'elenco di riferimenti.

Se un tipo di progetto non supporta gli assembly, la scheda non verrà visualizzata nella finestra di dialogo Gestione riferimenti.

La scheda **Assembly** è costituita da due sottoschede:

1. **Framework** elenca tutti gli assembly che costituiscono il framework di destinazione.

   Per i progetti che non usano .NET Core o la piattaforma UWP (Universal Windows Platform) come destinazione, la scheda **Framework** enumera gli assembly del framework di destinazione. L'utente dovrà aggiungere i riferimenti necessari all'applicazione.

   Per impostazione predefinita, i progetti di Windows universale contengono riferimenti a tutti gli assembly nel framework di destinazione. Nei progetti gestiti, un nodo di sola lettura nella cartella **Riferimenti** **in** Esplora soluzioni indica il riferimento all'intero framework. Di conseguenza, la scheda **Framework** non enumera gli assembly del framework e visualizza invece il messaggio seguente: "Tutti gli assembly framework sono già a cui viene fatto riferimento. Utilizzare Visualizzatore oggetti per esplorare i riferimenti nel framework."

2. **Le** estensioni elencano tutti gli assembly sviluppati da fornitori esterni di componenti e controlli per estendere il framework di destinazione. A seconda dello scopo dell'applicazione utente, potrebbero essere necessari questi assembly.

   **Le** estensioni vengono popolate enumerando gli assembly registrati nei percorsi seguenti:

   Computer a 32 bit:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   Computer a 64 bit:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   E versioni precedenti di [identificatore framework di destinazione]

   Se, ad esempio, un progetto è destinato a .NET Framework 4 in un computer a 32 bit, **Estensioni** enumera gli assembly che sono registrati in *\Microsoft\.NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.0\AssemblyFoldersEx* e *\Microsoft\.NETFramework\v2.0\AssemblyFoldersEx*.

Alcuni componenti nell'elenco potrebbero non essere visualizzati, a seconda della versione del framework del progetto. Ciò può verificarsi nelle seguenti condizioni:

- Un componente che usa una versione recente del framework non è compatibile con un progetto destinato a una versione precedente.

   Per informazioni sulla modifica della versione del framework di destinazione per un progetto, vedere [Panoramica sull'impostazione dei framework di destinazione](visual-studio-multi-targeting-overview.md).

- Un componente che usa .NET Framework 4 non è compatibile con un progetto destinato a .NET Framework 4.5.

Evitare di aggiungere riferimenti a file agli output di altri progetti della stessa soluzione, poiché potrebbero verificarsi errori di compilazione. Usare invece la scheda **Progetti** della finestra di dialogo **Aggiungi riferimento** per creare riferimenti da progetto a progetto. Tale procedura facilita lo sviluppo in team, consentendo una migliore gestione delle librerie di classi create nei progetti. Per altre informazioni, vedere [Risolvere i problemi relativi ai riferimenti interrotti](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> In Visual Studio 2015 o versioni successive, viene creato un riferimento al file anziché un riferimento al progetto se la versione del framework di destinazione di un progetto è .NET Framework 4.5 o successiva e quella dell'altro progetto è .NET Framework 2, 3, 3.5 o 4.0.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Per visualizzare un assembly nella finestra di dialogo Aggiungi riferimento

- Spostare o copiare l'assembly in una o più delle seguenti posizioni:

  - La directory del progetto corrente. È possibile trovare questi assembly tramite la scheda **Sfoglia** .

  - Altre directory di progetto nella stessa soluzione. È possibile trovare questi assembly tramite la scheda **Progetti**.

  \- - oppure -

- Impostare una chiave del Registro di sistema che specifica il percorso degli assembly da visualizzare:

  Per un sistema operativo a 32 bit, aggiungere una delle seguenti chiavi del Registro di sistema.

  - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  Per un sistema operativo a 64 bit, aggiungere una delle seguenti chiavi del Registro di sistema in un hive del Registro di sistema a 32 bit.

  - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  *\<VersionMinimum\>* è la versione del framework più bassa applicabile. Se è v3.0, le cartelle specificate in AssemblyFoldersEx si applicano ai progetti che hanno come destinazione .NET Framework *\<VersionMinimum\>* 3.0 e versioni successive. 

  *\<AssemblyLocation\>* è la directory degli assembly che si  desidera visualizzare nella finestra di dialogo Aggiungi riferimento, ad esempio *C:\Assembly*.

  Se la chiave del Registro di sistema viene creata nel nodo `HKEY_LOCAL_MACHINE`, tutti gli utenti possono visualizzare gli assembly nel percorso specificato nella finestra di dialogo **Aggiungi riferimento**. Se la chiave del Registro di sistema viene creata nel nodo `HKEY_CURRENT_USER`, ha effetto solo sull'impostazione dell'utente corrente.

  Aprire di nuovo la finestra di dialogo **Aggiungi riferimento**. Gli assembly dovrebbero essere visualizzati nella **scheda .NET.** In caso contrario, assicurarsi che gli assembly si trovino nella directory *AssemblyLocation* specificata, riavviare Visual Studio e riprovare.

## <a name="projects-tab"></a>Scheda Progetti

La scheda **Progetti** elenca tutti i progetti compatibili all'interno della soluzione corrente, nella sottoscheda **Soluzione**.

Un progetto può fare riferimento a un altro progetto destinato a una versione del framework diversa. È ad esempio possibile creare un progetto destinato a .NET Framework 4 ma che fa riferimento a un assembly creato per .NET Framework 2. Al contrario, il progetto .NET Framework 2 non può fare riferimento a un progetto .NET Framework 4. Per altre informazioni, vedere [Panoramica sull'impostazione dei framework di destinazione](../ide/visual-studio-multi-targeting-overview.md).

> [!NOTE]
> Un progetto destinato a .NET Framework 4 non è compatibile con un progetto destinato a .NET Framework 4 Client Profile.

## <a name="shared-projects-tab"></a>Scheda Progetti condivisi

Aggiungere un riferimento a un progetto condiviso nella scheda **Progetti condivisi** della finestra di dialogo Gestione riferimenti. I [progetti condivisi](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) consentono di scrivere codice comune a cui fa riferimento una serie di progetti di applicazioni diversi.

## <a name="universal-windows-tab"></a>Scheda Windows universale

La scheda **Windows universale** contiene tutti gli SDK specifici per le piattaforme in cui vengono eseguiti i sistemi operativi Windows.
Questa scheda include due sottogruppi: **Core** ed **Extensions.**

### <a name="core-subgroup"></a>Sottogruppo di base

I progetti di app di Windows universale hanno un riferimento all'SDK di Windows universale per impostazione predefinita. Di conseguenza, nel sottogruppo **Base** in **Gestione riferimenti** non viene enumerato nessun assembly dell'SDK di Windows universale.

### <a name="extensions-subgroup"></a>Sottogruppo Estensioni

**Estensioni** elenca gli SDK utente che estendono la piattaforma Windows di destinazione.

Un SDK è una raccolta di file che in Visual Studio vengono trattati come un singolo componente. Nella scheda **Estensioni** gli SDK applicabili al progetto da cui è stata richiamata la finestra di dialogo Gestione riferimenti sono elencati come singole voci. Una volta aggiunto a un progetto, tutto il contenuto dell'SDK viene utilizzato da Visual Studio in modo tale che l'utente non deve eseguire nuove azioni per sfruttare il contenuto dell'SDK in IntelliSense, nella casella degli strumenti, nelle finestre di progettazione, nel Visualizzatore oggetti, nella compilazione, nella distribuzione, nel debug e nella creazione del pacchetto.

Per informazioni su come visualizzare l'SDK nella **scheda Estensioni,** vedere [Creazione di un Software Development Kit.](../extensibility/creating-a-software-development-kit.md)

> [!NOTE]
> Se un progetto fa riferimento a un SDK che dipende da un altro SDK, Visual Studio userà il secondo SDK solo se si aggiunge manualmente un riferimento a quest'ultimo. Quando un utente sceglie un SDK nella scheda **Estensioni**, la finestra di dialogo Gestione riferimenti consente di identificare le dipendenze dell'SDK indicandole tutte nel riquadro dei dettagli.

Se un tipo di progetto non supporta le estensioni, la scheda non viene visualizzata nella finestra di dialogo Gestione riferimenti.

## <a name="com-tab"></a>Scheda COM

Nella **scheda COM** sono elencati tutti i componenti COM disponibili per il riferimento. Se si desidera aggiungere un riferimento a una DLL COM registrata che contiene un manifesto interno, annullare prima di tutto la registrazione della DLL. In caso contrario, Visual Studio aggiunge il riferimento all'assembly come controllo ActiveX e non come DLL nativa.

Se un tipo di progetto non supporta il modello COM, la scheda non viene visualizzata nella finestra di dialogo Gestione riferimenti.

## <a name="browse"></a>Esplora

È possibile usare il pulsante **Sfoglia** per passare a un componente nel file system.

Un progetto può fare riferimento a un componente destinato a una versione del framework diversa. È ad esempio possibile creare un'applicazione destinata a .NET Framework 4.7 che fa riferimento a un assembly destinato a .NET Framework 4. Per altre informazioni, vedere [Panoramica sull'impostazione dei framework di destinazione](../ide/visual-studio-multi-targeting-overview.md).

Evitare di aggiungere riferimenti a file negli output di un altro progetto all'interno della stessa soluzione, poiché questo potrebbe causare errori di compilazione. Usare invece la scheda **Soluzione** della finestra di dialogo Gestione riferimenti per creare riferimenti da progetto a progetto. Si facilita così lo sviluppo in team, consentendo una migliore gestione delle librerie di classi create nei progetti. Per altre informazioni, vedere [Risolvere i problemi relativi ai riferimenti interrotti](../ide/troubleshooting-broken-references.md).

Non è possibile individuare un SDK e aggiungerlo al progetto. È possibile solo individuare un file, ad esempio un assembly o un file con estensione *winmd*, e aggiungerlo al progetto.

Quando si esegue un riferimento a un file WinMD, il layout previsto è che i file con estensione *\<FileName> winmd,* *\<FileName>.dll* e *\<FileName> pri* siano tutti posizionati uno accanto all'altro. Se si fa riferimento a un WinMD nei seguenti scenari, un set incompleto di file verrà copiato nella directory di output del progetto e, di conseguenza, si verificheranno errori di runtime e di compilazione.

- **Componente nativo**: un progetto nativo crea un WinMD per ogni set di spazi dei nomi disgiunto e una sola DLL costituita dall'implementazione. I file WinMD avranno nomi diversi. Durante la creazione del riferimento a questo file di componente nativo, MSBuild non sarà in grado di riconoscere che WinMD con nome diverso sono in realtà un unico componente. Di conseguenza, verranno copiati solo i file *\<FileName>.dll* e *\<FileName> winmd* con lo stesso nome e si verificheranno errori di runtime. Per risolvere questo problema, creare un SDK di estensione. Per altre informazioni, vedere [Procedura: Creare un Software Development Kit](../extensibility/creating-a-software-development-kit.md).

- **Utilizzo di controlli**: un controllo XAML consiste come minimo nei file con estensione *\<FileName>winmd*, *\<FileName>dll*, *\<FileName>pri*, *\<XamlName>xaml* e *\<ImageName>jpg*. Quando il progetto viene compilato, i file di risorse associati al riferimento al file non verranno copiati nella directory di output del progetto e verranno copiati solo i file con estensione *\<FileName> winmd*, *\<FileName>.dll* e *\<FileName> pri.* Viene registrato un errore di compilazione per informare l'utente che le risorse *\<XamlName> .xaml* *\<ImageName> e.jpg* mancanti. Per ottenere i risultati desiderati, l'utente dovrà copiare manualmente questi file di risorse nella directory di output del progetto per compilazione e debug/runtime. Per risolvere questo problema, creare un SDK di estensione seguendo i passaggi in [Procedura: Creare un Software Development Kit](../extensibility/creating-a-software-development-kit.md) o modificare il file di progetto per aggiungere la proprietà seguente:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Se si aggiunge la proprietà, la compilazione potrebbe essere eseguita più lentamente.

## <a name="recent"></a>Recenti

**Gli assembly**, **COM,** **Windows** e **Sfoglia** supportano ognuno una scheda **Recenti,** che enumera l'elenco dei componenti aggiunti di recente ai progetti.

## <a name="search"></a>Ricerca

La barra di ricerca della finestra di dialogo Gestione riferimenti viene abilitata nella scheda attiva. Ad esempio, se un utente digita "sistema" nella barra di ricerca mentre è attiva la scheda **Soluzione**, verranno restituiti risultati solo se la soluzione è costituita da un nome di progetto contenente il termine "sistema".

## <a name="see-also"></a>Vedere anche

- [Gestire i riferimenti in un progetto](../ide/managing-references-in-a-project.md)
