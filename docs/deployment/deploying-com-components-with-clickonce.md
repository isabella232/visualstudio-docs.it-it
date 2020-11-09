---
title: Distribuzione di componenti COM con ClickOnce | Microsoft Docs
description: Informazioni sui passaggi necessari per distribuire le applicazioni .NET in ClickOnce che contengono componenti COM legacy.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fc6ef0e4d682f0f712eefc4c139895331c31688
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382923"
---
# <a name="deploy-com-components-with-clickonce"></a>Distribuire componenti COM con ClickOnce
La distribuzione di componenti COM legacy è stata tradizionalmente un'attività difficile. I componenti devono essere registrati a livello globale e quindi possono causare effetti collaterali indesiderati tra le applicazioni sovrapposte. In genere, questa situazione non è un problema nelle applicazioni .NET Framework perché i componenti sono completamente isolati in un'applicazione o sono compatibili side-by-side. Visual Studio consente di distribuire componenti COM isolati sul sistema operativo Windows XP o versione successiva.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fornisce un meccanismo semplice e sicuro per la distribuzione di applicazioni .NET. Tuttavia, se le applicazioni utilizzano componenti COM legacy, sarà necessario eseguire passaggi aggiuntivi per la relativa distribuzione. In questo argomento viene descritto come distribuire componenti COM isolati e riferimenti a componenti nativi (ad esempio, da Visual Basic 6,0 o Visual C++).

 Per ulteriori informazioni sulla distribuzione di componenti COM isolati, vedere [semplificare la distribuzione di app con ClickOnce e Registration-Free com](https://web.archive.org/web/20050326005413/msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).

## <a name="registration-free-com"></a>Domini COM senza registrazione
 COM senza registrazione è una nuova tecnologia per la distribuzione e l'attivazione di componenti COM isolati. Funziona inserendo tutte le informazioni di registrazione e la libreria dei tipi del componente, in genere installate nel registro di sistema, in un file XML denominato manifesto, archiviato nella stessa cartella dell'applicazione.

 Per isolare un componente COM è necessario che venga registrato nel computer dello sviluppatore, ma non è necessario che sia registrato nel computer dell'utente finale. Per isolare un componente COM, è sufficiente impostare la proprietà **isolata** del riferimento su **true**. Per impostazione predefinita, questa proprietà è impostata su **false** , a indicare che deve essere considerata come un riferimento com registrato. Se questa proprietà è **true** , viene generato un manifesto per il componente in fase di compilazione. Causa inoltre la copia dei file corrispondenti nella cartella dell'applicazione durante l'installazione.

 Quando il generatore di manifesti rileva un riferimento COM isolato, enumera tutte le `CoClass` voci nella libreria dei tipi del componente, associando ogni voce con i dati di registrazione corrispondenti e generando definizioni di manifesto per tutte le classi com nel file della libreria dei tipi.

## <a name="deploy-registration-free-com-components-using-clickonce"></a>Distribuire componenti COM senza registrazione usando ClickOnce
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la tecnologia di distribuzione è particolarmente adatta per la distribuzione di componenti COM isolati, perché per la distribuzione è necessario [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] che un componente disponga di un manifesto.

 In genere, l'autore del componente deve fornire un manifesto. In caso contrario, Visual Studio è in grado di generare automaticamente un manifesto per un componente COM. La generazione del manifesto viene eseguita durante il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] processo di pubblicazione. per ulteriori informazioni, vedere [pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md). Questa funzionalità consente inoltre di sfruttare i componenti legacy creati negli ambienti di sviluppo precedenti, ad esempio Visual Basic 6,0.

 Esistono due modi per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuire i componenti com:

- Usare il programma di avvio automatico per distribuire i componenti COM. Questa operazione funziona su tutte le piattaforme supportate.

- Usare l'isolamento del componente nativo (noto anche come distribuzione COM senza registrazione). Tuttavia, questo funzionerà solo su un sistema operativo Windows XP o versione successiva.

### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Esempio di isolamento e distribuzione di un semplice componente COM
 Per dimostrare la distribuzione di componenti COM senza registrazione, questo esempio creerà un'applicazione basata su Windows in Visual Basic che fa riferimento a un componente COM nativo isolato creato con Visual Basic 6,0 e lo distribuisce usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 Per prima cosa sarà necessario creare il componente COM nativo:

##### <a name="to-create-a-native-com-component"></a>Per creare un componente COM nativo

1. Utilizzando Visual Basic 6,0, scegliere **nuovo** dal menu **file** , quindi **progetto**.

2. Nella finestra di dialogo **nuovo progetto** selezionare il nodo **Visual Basic** e selezionare un progetto **dll ActiveX** . Nella casella **Nome** digitare `VB6Hello`.

    > [!NOTE]
    > Solo i tipi di progetto di controllo ActiveX e DLL ActiveX sono supportati con COM senza registrazione. I tipi di progetto di documento ActiveX e ActiveX EXE non sono supportati.

3. In **Esplora soluzioni** fare doppio clic su **Class1. vb** per aprire l'editor di testo.

4. In Class1. vb aggiungere il codice seguente dopo il codice generato per il `New` Metodo:

    ```vb
    Public Sub SayHello()
       MsgBox "Message from the VB6Hello COM component"
    End Sub
    ```

5. Compilare il componente. Dal menu **Compila** scegliere **Compila soluzione**.

> [!NOTE]
> COM senza registrazione supporta solo i tipi di progetto DLL e controlli COM. Non è possibile usare gli exe con COM senza registrazione.

 A questo punto è possibile creare un'applicazione basata su Windows e aggiungervi un riferimento al componente COM.

##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Per creare un'applicazione basata su Windows utilizzando un componente COM

1. Utilizzando Visual Basic, scegliere **nuovo** dal menu **file** , quindi **progetto**.

2. Nella finestra di dialogo **nuovo progetto** selezionare il nodo **Visual Basic** e selezionare **applicazione Windows**. Nella casella **Nome** digitare `RegFreeComDemo`.

3. In **Esplora soluzioni** fare clic sul pulsante **Mostra tutti i file** per visualizzare i riferimenti al progetto.

4. Fare clic con il pulsante destro del mouse sul nodo **riferimenti** e scegliere **Aggiungi riferimento** dal menu di scelta rapida.

5. Nella finestra di dialogo **Aggiungi riferimento** fare clic sulla scheda **Sfoglia** , passare a VB6Hello.dll, quindi selezionarla.

    Un riferimento **VB6Hello** viene visualizzato nell'elenco riferimenti.

6. Puntare alla **casella degli strumenti** , selezionare un controllo **Button** e trascinarlo nel form **Form1** .

7. Nella finestra **Proprietà** impostare la proprietà **Text** del pulsante su **Hello**.

8. Fare doppio clic sul pulsante per aggiungere il codice del gestore e nel file di codice aggiungere il codice in modo che il gestore legga come indicato di seguito:

   ```vb
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim VbObj As New VB6Hello.Class1
       VbObj.SayHello()
   End Sub
   ```

9. Eseguire l'applicazione. Scegli **Avvia debug** dal menu **Debug**.

   Successivamente, è necessario isolare il controllo. Ogni componente COM utilizzato dall'applicazione viene rappresentato nel progetto come riferimento COM. Questi riferimenti sono visibili nel nodo **riferimenti** della finestra **Esplora soluzioni** . Si noti che è possibile aggiungere riferimenti direttamente usando il comando **Aggiungi riferimento** nel menu **progetto** o indirettamente trascinando un controllo ActiveX nel form.

   Nei passaggi seguenti viene illustrato come isolare il componente COM e pubblicare l'applicazione aggiornata contenente il controllo isolato:

##### <a name="to-isolate-a-com-component"></a>Per isolare un componente COM

1. In **Esplora soluzioni** , nel nodo **riferimenti** , selezionare il riferimento **VB6Hello** .

2. Nella finestra **Proprietà** modificare il valore della proprietà **isolated** da **false** a **true**.

3. Dal menu **Compila** scegliere **Compila soluzione**.

   A questo punto, quando si preme F5, l'applicazione funziona come previsto, ma ora è in esecuzione in COM senza registrazione. Per dimostrare questo problema, provare a annullare la registrazione del componente VB6Hello.dll ed eseguire RegFreeComDemo1.exe all'esterno dell'IDE di Visual Studio. Questa volta, quando si fa clic sul pulsante, funziona ancora. Se si rinomina temporaneamente il manifesto dell'applicazione, l'operazione avrà esito negativo.

> [!NOTE]
> È possibile simulare l'assenza di un componente COM eseguendo temporaneamente la registrazione. Aprire un prompt dei comandi, passare alla cartella del sistema digitando `cd /d %windir%\system32` , quindi annullare la registrazione del componente digitando `regsvr32 /u VB6Hello.dll` . È possibile registrarlo di nuovo digitando `regsvr32 VB6Hello.dll` .

 Il passaggio finale consiste nel pubblicare l'applicazione usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] :

##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Per pubblicare un aggiornamento di un'applicazione con un componente COM isolato

1. Scegliere **Pubblica RegFreeComDemo** dal menu **Compila** .

    Verrà visualizzata la Pubblicazione guidata.

2. Nella pubblicazione guidata, specificare un percorso sul disco del computer locale a cui è possibile accedere ed esaminare i file pubblicati.

3. Fare clic su **Fine** per pubblicare l'applicazione.

   Se si esaminano i file pubblicati, si noterà che il file Sysmon. ocx è incluso. Il controllo è completamente isolato a questa applicazione, vale a dire che se il computer dell'utente finale dispone di un'altra applicazione che utilizza una versione diversa del controllo, non può interferire con l'applicazione.

## <a name="reference-native-assemblies"></a>Assembly nativi di riferimento
 Visual Studio supporta riferimenti a assembly nativi Visual Basic 6,0 o C++. tali riferimenti sono detti riferimenti nativi. È possibile stabilire se un riferimento è nativo verificando che la proprietà relativa al **tipo di file** sia impostata su **native** o **ActiveX**.

 Per aggiungere un riferimento nativo, utilizzare il comando **Aggiungi riferimento** , quindi selezionare il manifesto. Alcuni componenti inseriscono il manifesto all'interno della DLL. In questo caso, è possibile scegliere semplicemente la DLL e Visual Studio lo aggiungerà come riferimento nativo se rileva che il componente contiene un manifesto incorporato. Visual Studio includerà anche automaticamente eventuali file o assembly dipendenti elencati nel manifesto se si trovano nella stessa cartella del componente a cui si fa riferimento.

 L'isolamento dei controlli COM semplifica la distribuzione di componenti COM che non dispongono già di manifesti. Tuttavia, se un componente viene fornito con un manifesto, è possibile fare direttamente riferimento al manifesto. In realtà, è consigliabile usare sempre il manifesto fornito dall'autore del componente, laddove possibile, invece di usare la proprietà **isolata** .

## <a name="limitations-of-registration-free-com-component-deployment"></a>Limitazioni della distribuzione di componenti COM senza registrazione
 COM senza registrazione offre vantaggi evidenti rispetto alle tecniche di distribuzione tradizionali. Tuttavia, esistono alcune limitazioni e avvertenze che devono essere anche indicate. Il limite massimo è che funziona solo in Windows XP o versione successiva. L'implementazione di COM senza registrazione richiede modifiche al modo in cui i componenti vengono caricati nel sistema operativo di base. Sfortunatamente, non esiste alcun livello di supporto di livello inferiore per le COM senza registrazione.

 Non tutti i componenti sono un candidato idoneo per le COM senza registrazione. Un componente non è adatto se si verifica una delle condizioni seguenti:

- Il componente è un server out-of-process. I server EXE non sono supportati. sono supportate solo le dll.

- Il componente fa parte del sistema operativo oppure è un componente di sistema, ad esempio XML, Internet Explorer o Microsoft Data Access Components (MDAC). È necessario seguire i criteri di ridistribuzione dell'autore del componente; rivolgersi al fornitore.

- Il componente fa parte di un'applicazione, ad esempio Microsoft Office. Ad esempio, non provare a isolare il modello a oggetti di Microsoft Excel. Questo fa parte di Office e può essere usato solo in un computer in cui è installato il prodotto Office completo.

- Il componente deve essere utilizzato come componente aggiuntivo o come snap-in, ad esempio un componente aggiuntivo di Office o un controllo in un Web browser. Questi componenti richiedono in genere un tipo di schema di registrazione definito dall'ambiente host che esula dall'ambito del manifesto stesso.

- Il componente gestisce un dispositivo fisico o virtuale per il sistema, ad esempio un driver di dispositivo per uno spooler di stampa.

- Il componente è un accesso ai dati ridistribuibile. Per poter eseguire le applicazioni di dati, in genere è necessario che sia installato un ridistribuibile di accesso ai dati separato. Non tentare di isolare componenti quali Microsoft ADO Data Control, Microsoft OLE DB o Microsoft Data Access Components (MDAC). In alternativa, se l'applicazione usa MDAC o SQL Server Express, è necessario impostarli come prerequisiti; visualizzare [procedura: installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).

  In alcuni casi, potrebbe essere possibile per lo sviluppatore del componente riprogettarlo per COM senza registrazione. Se ciò non è possibile, è comunque possibile creare e pubblicare applicazioni che dipendono da esse tramite lo schema di registrazione standard utilizzando il programma di avvio automatico. Per ulteriori informazioni, vedere [creazione di pacchetti del programma di avvio automatico](../deployment/creating-bootstrapper-packages.md).

  Un componente COM può essere isolato una sola volta per ogni applicazione. Ad esempio, non è possibile isolare lo stesso componente COM da due progetti di **libreria di classi** diversi che fanno parte della stessa applicazione. In questo modo verrà generato un avviso di compilazione e l'applicazione non verrà caricata in fase di esecuzione. Per evitare questo problema, Microsoft consiglia di incapsulare i componenti COM in un'unica libreria di classi.

  Esistono diversi scenari in cui è richiesta la registrazione COM nel computer dello sviluppatore, anche se la distribuzione dell'applicazione non richiede la registrazione. `Isolated`Per la proprietà è necessario che il componente COM sia registrato nel computer dello sviluppatore per generare automaticamente il manifesto durante la compilazione. Non sono disponibili funzionalità di acquisizione delle registrazioni che richiamano la registrazione automatica durante la compilazione. Inoltre, le classi non definite in modo esplicito nella libreria dei tipi non verranno riflesse nel manifesto. Quando si utilizza un componente COM con un manifesto preesistente, ad esempio un riferimento nativo, potrebbe non essere necessario registrare il componente in fase di sviluppo. Tuttavia, la registrazione è obbligatoria se il componente è un controllo ActiveX e si desidera includerlo nella **casella degli strumenti** e nella finestra di progettazione Windows Forms.

## <a name="see-also"></a>Vedere anche
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)