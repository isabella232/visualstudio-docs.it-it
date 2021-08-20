---
title: Distribuzione di componenti COM con ClickOnce | Microsoft Docs
description: Informazioni sui passaggi necessari per distribuire applicazioni .NET in ClickOnce che contengono componenti COM legacy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 68f62aab190686dbed88628b18e0b1ad0f89a723
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073877"
---
# <a name="deploy-com-components-with-clickonce"></a>Distribuire componenti COM con ClickOnce
La distribuzione di componenti COM legacy è stata tradizionalmente un'attività difficile. I componenti devono essere registrati a livello globale e quindi possono causare effetti collaterali indesiderati tra le applicazioni sovrapposte. Questa situazione in genere non rappresenta un problema nelle applicazioni .NET Framework perché i componenti sono completamente isolati da un'applicazione o sono compatibili side-by-side. Visual Studio consente di distribuire componenti COM isolati nel sistema operativo Windows XP o versione successiva.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] offre un meccanismo semplice e sicuro per la distribuzione delle applicazioni .NET. Tuttavia, se le applicazioni usano componenti COM legacy, sarà necessario eseguire passaggi aggiuntivi per distribuirli. In questo argomento viene descritto come distribuire componenti COM isolati e fare riferimento a componenti nativi, ad esempio da Visual Basic 6.0 o Visual C++.

 Per altre informazioni sulla distribuzione di componenti COM isolati, vedere Semplificare la distribuzione [di app con ClickOnce e Registration-Free COM.](https://web.archive.org/web/20050326005413/msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx)

## <a name="registration-free-com"></a>Domini COM senza registrazione
 COM senza registrazione è una nuova tecnologia per la distribuzione e l'attivazione di componenti COM isolati. Funziona inserendo tutte le informazioni relative alla libreria dei tipi e alla registrazione del componente che vengono in genere installate nel Registro di sistema in un file XML denominato manifesto, archiviato nella stessa cartella dell'applicazione.

 L'isolamento di un componente COM richiede che sia registrato nel computer dello sviluppatore, ma non deve essere registrato nel computer dell'utente finale. Per isolare un componente COM, è necessario solo impostare la proprietà **Isolated** del relativo riferimento su **True.** Per impostazione predefinita, questa proprietà è impostata **su False,** a indicare che deve essere considerata come un riferimento COM registrato. Se questa proprietà è **True,** viene generato un manifesto per questo componente in fase di compilazione. Determina inoltre la copia dei file corrispondenti nella cartella dell'applicazione durante l'installazione.

 Quando il generatore di manifesti rileva un riferimento COM isolato, enumera tutte le voci nella libreria dei tipi del componente, abbinando ogni voce ai dati di registrazione corrispondenti e generando definizioni di manifesto per tutte le classi COM nel file della libreria dei `CoClass` tipi.

## <a name="deploy-registration-free-com-components-using-clickonce"></a>Distribuire componenti COM senza registrazione usando ClickOnce
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la tecnologia di distribuzione è particolarmente adatta per la distribuzione di componenti COM isolati, perché sia che COM senza registrazione richiedono che un componente abbia un manifesto per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] essere distribuito.

 In genere, l'autore del componente deve fornire un manifesto. In caso contrario, tuttavia, Visual Studio è in grado di generare automaticamente un manifesto per un componente COM. La generazione del manifesto viene eseguita durante il processo di pubblicazione. Per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] altre informazioni, vedere Publishing ClickOnce [Applications](../deployment/publishing-clickonce-applications.md). Questa funzionalità consente anche di sfruttare i componenti legacy creati in ambienti di sviluppo precedenti, ad esempio Visual Basic 6.0.

 Esistono due modi per distribuire [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i componenti COM:

- Usare il programma di avvio automatico per distribuire i componenti COM. funziona in tutte le piattaforme supportate.

- Usare la distribuzione dell'isolamento dei componenti nativi (nota anche come COM senza registrazione). Tuttavia, funziona solo in un sistema operativo Windows XP o versione successiva.

### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Esempio di isolamento e distribuzione di un componente COM semplice
 Per illustrare la distribuzione di componenti COM senza registrazione, questo esempio creerà un'applicazione basata su Windows in Visual Basic che fa riferimento a un componente COM nativo isolato creato usando Visual Basic 6.0 e la distribuirà usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 Prima di tutto è necessario creare il componente COM nativo:

##### <a name="to-create-a-native-com-component"></a>Per creare un componente COM nativo

1. Usando Visual Basic 6.0, scegliere **Nuovo** dal menu File **,** **quindi Project**.

2. Nella finestra **di dialogo Project** selezionare il nodo **Visual Basic** e selezionare un progetto **DLL ActiveX** progetto. Nella casella **Nome** digitare `VB6Hello`.

    > [!NOTE]
    > Con COM senza registrazione ActiveX sono supportati solo i tipi di progetto dll e ActiveX control. ActiveX I tipi di progetto EXE e ActiveX document non sono supportati.

3. In **Esplora soluzioni** fare doppio clic su **Class1.vb** per aprire l'editor di testo.

4. In Class1.vb aggiungere il codice seguente dopo il codice generato per il `New` metodo :

    ```vb
    Public Sub SayHello()
       MsgBox "Message from the VB6Hello COM component"
    End Sub
    ```

5. Compilare il componente. Dal menu **Compila** scegliere **Compila soluzione**.

> [!NOTE]
> COM senza registrazione supporta solo DLL e tipi di progetto di controlli COM. Non è possibile usare le ES con COM senza registrazione.

 A questo punto è possibile creare Windows'applicazione basata su più applicazioni e aggiungervi un riferimento al componente COM.

##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Per creare un'Windows basata su codice usando un componente COM

1. Usando Visual Basic, scegliere **Nuovo dal** menu File **,** **quindi Project**.

2. Nella finestra **di dialogo Project** selezionare il nodo **Visual Basic** e selezionare Windows **applicazione**. Nella casella **Nome** digitare `RegFreeComDemo`.

3. In **Esplora soluzioni** fare clic sul **pulsante Mostra tutti i** file per visualizzare i riferimenti al progetto.

4. Fare clic con il pulsante destro **del mouse** sul nodo Riferimenti e **scegliere Aggiungi** riferimento dal menu di scelta rapida.

5. Nella finestra **di dialogo** Aggiungi riferimento fare clic **sulla scheda** Sfoglia, passare VB6Hello.dll e quindi selezionarlo.

    Nell'elenco dei riferimenti viene visualizzato un riferimento **VB6Hello.**

6. Posizionare il **puntatore del** mouse sulla casella **degli strumenti,** selezionare un controllo Pulsante e trascinarlo nel form **Form1.**

7. Nella finestra **Proprietà** impostare la proprietà **Text** del pulsante su **Hello**.

8. Fare doppio clic sul pulsante per aggiungere il codice del gestore e nel file di codice aggiungere il codice in modo che il gestore letta come segue:

   ```vb
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim VbObj As New VB6Hello.Class1
       VbObj.SayHello()
   End Sub
   ```

9. Eseguire l'applicazione. Scegli **Avvia debug** dal menu **Debug**.

   Successivamente è necessario isolare il controllo. Ogni componente COM utilizzato dall'applicazione viene rappresentato nel progetto come riferimento COM. Questi riferimenti sono visibili sotto il **nodo Riferimenti** nella **finestra Esplora soluzioni** riferimenti. Si noti che è possibile aggiungere  riferimenti direttamente usando il comando Aggiungi riferimento nel menu **Project** o indirettamente trascinando un controllo ActiveX nel form.

   La procedura seguente illustra come isolare il componente COM e pubblicare l'applicazione aggiornata contenente il controllo isolato:

##### <a name="to-isolate-a-com-component"></a>Per isolare un componente COM

1. In **Esplora soluzioni**, nel **nodo Riferimenti** selezionare il riferimento **VB6Hello.**

2. Nella finestra **Proprietà** modificare il valore della proprietà **Isolated** da **False** a **True.**

3. Dal menu **Compila** scegliere **Compila soluzione**.

   A questo punto, quando si preme F5, l'applicazione funziona come previsto, ma è ora in esecuzione in COM senza registrazione. Per dimostrarlo, provare ad annullare la registrazione del componente VB6Hello.dll ed eseguire RegFreeComDemo1.exe all'esterno dell'IDE Visual Studio. Questa volta, quando si fa clic sul pulsante, il pulsante funziona ancora. Se si rinomina temporaneamente il manifesto dell'applicazione, l'operazione avrà nuovamente esito negativo.

> [!NOTE]
> È possibile simulare l'assenza di un componente COM annullando temporaneamente la registrazione. Aprire un prompt dei comandi, passare alla cartella di sistema `cd /d %windir%\system32` digitando , quindi annullare la registrazione del componente digitando `regsvr32 /u VB6Hello.dll` . È possibile registrarlo di nuovo digitando `regsvr32 VB6Hello.dll` .

 Il passaggio finale consiste nel pubblicare l'applicazione usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] :

##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Per pubblicare un aggiornamento di un'applicazione con un componente COM isolato

1. Scegliere **Pubblica** **RegFreeComDemo** dal menu Compila .

    Verrà visualizzata la Pubblicazione guidata.

2. Nella Pubblicazione guidata specificare un percorso sul disco del computer locale a cui è possibile accedere ed esaminare i file pubblicati.

3. Fare clic su **Fine** per pubblicare l'applicazione.

   Se si esaminano i file pubblicati, si noterà che è incluso il file sysmon.ocx. Il controllo è completamente isolato per questa applicazione, vale a dire che se il computer dell'utente finale ha un'altra applicazione che usa una versione diversa del controllo, non può interferire con questa applicazione.

## <a name="reference-native-assemblies"></a>Fare riferimento ad assembly nativi
 Visual Studio supporta riferimenti ad assembly Visual Basic 6.0 o C++; Tali riferimenti sono detti riferimenti nativi. È possibile stabilire se un riferimento è nativo verificando che la relativa proprietà **Tipo di file** sia impostata su **Nativo** **o ActiveX**.

 Per aggiungere un riferimento nativo, usare **il comando Aggiungi** riferimento e quindi passare al manifesto. Alcuni componenti posizionano il manifesto all'interno della DLL. In questo caso, è sufficiente scegliere la DLL stessa e Visual Studio la aggiungerà come riferimento nativo se rileva che il componente contiene un manifesto incorporato. Visual Studio includerà automaticamente anche tutti i file dipendenti o gli assembly elencati nel manifesto se sono nella stessa cartella del componente a cui si fa riferimento.

 L'isolamento dei controlli COM semplifica la distribuzione di componenti COM che non dispongono già di manifesti. Tuttavia, se un componente viene fornito con un manifesto, è possibile fare riferimento direttamente al manifesto. In realtà, è sempre consigliabile usare il manifesto fornito dall'autore del componente laddove possibile anziché usare la **proprietà Isolated.**

## <a name="limitations-of-registration-free-com-component-deployment"></a>Limitazioni della distribuzione di componenti COM senza registrazione
 COM senza registrazione offre vantaggi chiari rispetto alle tecniche di distribuzione tradizionali. Esistono tuttavia alcune limitazioni e avvertenze che devono essere sottolineate. La limitazione maggiore è che funziona solo in Windows XP o versione successiva. L'implementazione di COM senza registrazione ha richiesto modifiche al modo in cui i componenti vengono caricati nel sistema operativo di base. Sfortunatamente, non esiste un livello di supporto di livello inferiore per COM senza registrazione.

 Non tutti i componenti sono idonei per COM senza registrazione. Un componente non è adatto se si verifica una delle condizioni seguenti:

- Il componente è un server out-of-process. I server EXE non sono supportati. sono supportate solo LE DLL.

- Il componente fa parte del sistema operativo o è un componente di sistema, ad esempio XML, Internet Explorer o Microsoft Data Access Components (MDAC). È necessario seguire i criteri di ridistribuzione dell'autore del componente. rivolgersi al fornitore.

- Il componente fa parte di un'applicazione, ad esempio Microsoft Office. Ad esempio, non è consigliabile tentare di isolare Microsoft Excel a oggetti. Fa parte del Office e può essere usato solo in un computer in cui è installato il Office completo.

- Il componente deve essere utilizzato come componente aggiuntivo o snap-in, ad esempio un componente aggiuntivo di Office o un controllo in un Web browser. Tali componenti richiedono in genere un tipo di schema di registrazione definito dall'ambiente di hosting che non sia nell'ambito del manifesto stesso.

- Il componente gestisce un dispositivo fisico o virtuale per il sistema, ad esempio un driver di dispositivo per uno spooler di stampa.

- Il componente è ridistribuibile per l'accesso ai dati. Le applicazioni dati richiedono in genere l'installazione di un ridistribuibile di Accesso ai dati separato prima di poter essere eseguite. È consigliabile non tentare di isolare componenti quali Microsoft ADO Data Control, Microsoft OLE DB o Microsoft Data Access Components (MDAC). In alternativa, se l'applicazione usa MDAC o SQL Server Express, è necessario impostarli come prerequisiti; visualizzare [procedura: installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).

  In alcuni casi, lo sviluppatore del componente potrebbe riprogettare il componente per COM senza registrazione. Se non è possibile, è comunque possibile compilare e pubblicare applicazioni che dipendono da esse tramite lo schema di registrazione standard usando il programma di avvio automatico. Per altre informazioni, vedere Creazione [di pacchetti del programma di avvio automatico.](../deployment/creating-bootstrapper-packages.md)

  Un componente COM può essere isolato solo una volta per ogni applicazione. Ad esempio, non è possibile isolare lo stesso componente COM da due **progetti** libreria di classi diversi che fanno parte della stessa applicazione. In questo modo verrà generato un avviso di compilazione e l'applicazione non verrà caricata in fase di esecuzione. Per evitare questo problema, Microsoft consiglia di incapsulare i componenti COM in una singola libreria di classi.

  Esistono diversi scenari in cui la registrazione COM è necessaria nel computer dello sviluppatore, anche se la distribuzione dell'applicazione non richiede la registrazione. La proprietà richiede che il componente COM sia registrato nel computer dello sviluppatore per generare automaticamente `Isolated` il manifesto durante la compilazione. Non sono disponibili funzionalità di acquisizione della registrazione che richiamano la registrazione automatica durante la compilazione. Inoltre, tutte le classi non definite in modo esplicito nella libreria dei tipi non verranno riflesse nel manifesto. Quando si usa un componente COM con un manifesto preesistnte, ad esempio un riferimento nativo, potrebbe non essere necessario registrare il componente in fase di sviluppo. Tuttavia, la registrazione è necessaria se il componente è un controllo  ActiveX e si vuole includerlo nella casella degli strumenti e nella finestra di progettazione Windows Form.

## <a name="see-also"></a>Vedi anche
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)