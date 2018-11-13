---
title: Distribuzione di componenti COM con ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e81462b2ccb5d29a0090623d72cf78183abd6917
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348747"
---
# <a name="deploy-com-components-with-clickonce"></a>Distribuire i componenti COM con ClickOnce
Distribuzione di componenti COM legacy è tradizionalmente difficile. I componenti devono essere registrati a livello globale e pertanto possono causare effetti collaterali indesiderati applicazioni sovrapposte. Questa situazione non è in genere un problema in applicazioni .NET Framework perché i componenti sono completamente isolati a un'applicazione o sono compatibili con side-by-side. Visual Studio consente di distribuire i componenti COM isolati nel Windows XP o versioni successive del sistema operativo.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fornisce un meccanismo semplice e sicuro per la distribuzione di applicazioni .NET. Tuttavia, se le applicazioni usano i componenti COM legacy, è necessario eseguire passaggi aggiuntivi per la loro distribuzione. Questo argomento descrive come distribuire i componenti COM isolati e fanno riferimento a componenti nativi (ad esempio, da Visual Basic 6.0 o Visual C++).  
  
 Per altre informazioni sulla distribuzione di componenti COM isolati, vedere [Simplify App Deployment with ClickOnce and Registration-Free COM](https://web.archive.org/web/20050326005413/msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).
  
## <a name="registration-free-com"></a>Registration-free COM  
 COM senza registrazione è una nuova tecnologia per la distribuzione e attivazione di componenti COM isolati. Funziona inserendo la libreria dei tipi del componente e informazioni di registrazione che viene in genere installate nel Registro di sistema in un file XML denominato un manifesto, archiviato nella stessa cartella dell'applicazione.  
  
 Isolare un componente COM richiede che si sia registrato nel computer dello sviluppatore, ma non devono essere registrati nel computer dell'utente finale. Per isolare un componente COM, è sufficiente è impostato il riferimento **Isolated** proprietà **True**. Per impostazione predefinita, questa proprietà è impostata su **False**, che indica che deve essere considerato come un riferimento COM registrato. Se questa proprietà è **True**, verrà creato un manifesto da generare per questo componente in fase di compilazione. Determina anche i file corrispondenti da copiare nella cartella dell'applicazione durante l'installazione.  
  
 Quando il generatore del manifesto incontra un riferimento COM isolato, enumera tutte le `CoClass` voci nella libreria dei tipi del componente, la corrispondenza di ogni voce con i relativi dati di registrazione corrispondente e la generazione di definizioni del manifesto per tutto il modello COM classi nel file di libreria dei tipi.  
  
## <a name="deploy-registration-free-com-components-using-clickonce"></a>Distribuire i componenti COM senza registrazione mediante ClickOnce  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tecnologia di distribuzione è adatta per la distribuzione di componenti COM isolati, in quanto entrambi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e COM senza registrazione richiede che un componente disponga di un manifesto.  
  
 In genere, l'autore del componente deve fornire un manifesto. Se non lo è, tuttavia, Visual Studio è in grado di generare automaticamente un manifesto da un componente COM. La generazione del manifesto viene eseguita durante la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] processo di pubblicazione; per altre informazioni, vedere [pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md). Questa funzionalità consente anche di sfruttare i componenti legacy che è stato creato in ambienti di sviluppo precedenti, ad esempio Visual Basic 6.0.  
  
 Esistono due modi che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] consente di distribuire i componenti COM:  
  
-   Usare il programma di avvio per distribuire i componenti COM. Questa opzione funziona su tutte le piattaforme supportate.  
  
-   Usare la distribuzione di isolamento (noto anche come COM senza registrazione) componente nativo. Tuttavia, questa impostazione funziona solo in un Windows XP o versioni successive del sistema operativo.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Esempio di isolamento e la distribuzione di un semplice componente COM  
 Per dimostrare la distribuzione di componenti COM senza registrazione, in questo esempio verrà creare un'applicazione basata su Windows in Visual Basic che fa riferimento a un componente COM nativo isolato creato utilizzando Visual Basic 6.0 e distribuirla tramite [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Prima di tutto è necessario creare il componente COM nativo:  
  
##### <a name="to-create-a-native-com-component"></a>Per creare un componente COM nativo  
  
1.  Utilizzando Visual Basic 6.0, dal **File** menu, fare clic su **New**, quindi **progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo, seleziona la **Visual Basic** nodo e selezionare un **DLL ActiveX** progetto. Nella casella **Nome** digitare `VB6Hello`.  
  
    > [!NOTE]
    >  Sono supportati solo i tipi di progetto DLL ActiveX e il controllo ActiveX con COM senza registrazione. Tipi di progetto EXE ActiveX e il documento ActiveX non sono supportati.  
  
3.  Nelle **Esplora soluzioni**, fare doppio clic su **Class1.vb** per aprire l'editor di testo.  
  
4.  In Class1, aggiungere il codice seguente dopo il codice generato per il `New` metodo:  
  
    ```vb  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Compilare il componente. Dal **compilare** menu, fare clic su **Compila soluzione**.  
  
> [!NOTE]
>  COM senza registrazione supporta solo le DLL e controlla i tipi di progetto di COM. È possibile usare file eseguibili con COM senza registrazione.  
  
 A questo punto è possibile creare un'applicazione basata su Windows e aggiungervi un riferimento al componente COM.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Per creare un'applicazione basata su Windows usando un componente COM  
  
1. Utilizza Visual Basic, dal **File** menu, fare clic su **New**, quindi **progetto**.  
  
2. Nel **nuovo progetto** finestra di dialogo, seleziona la **Visual Basic** nodo e selezionare **applicazione Windows**. Nella casella **Nome** digitare `RegFreeComDemo`.  
  
3. Nelle **Esplora soluzioni**, fare clic sui **Mostra tutti i file** pulsante per visualizzare i riferimenti al progetto.  
  
4. Fare doppio clic il **riferimenti** nodo e selezionare **Aggiungi riferimento** dal menu di scelta rapida.  
  
5. Nel **Aggiungi riferimento** della finestra di dialogo fare clic sui **Sfoglia** scheda, passare a VB6Hello, quindi selezionarlo.  
  
    Oggetto **VB6Hello** riferimento verrà visualizzato nell'elenco dei riferimenti.  
  
6. Scegliere il **casella degli strumenti**, selezionare una **pulsante** controllano e trascinarlo in modo che il **Form1** form.  
  
7. Nel **delle proprietà** impostare nella finestra proprietà del pulsante **testo** proprietà **Hello**.  
  
8. Fare doppio clic sul pulsante per aggiungere il codice del gestore e nel file di codice, aggiungere il codice in modo che il gestore di è simile alla seguente:  
  
   ```vb  
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim VbObj As New VB6Hello.Class1  
       VbObj.SayHello()  
   End Sub  
   ```  
  
9. Eseguire l'applicazione. Dal **Debug** menu, fare clic su **Avvia debug**.  
  
   Successivamente è necessario isolare il controllo. Ogni componente COM che usa l'applicazione è rappresentato nel progetto come riferimento COM. Questi riferimenti sono visibili nel **riferimenti** nodo il **Esplora soluzioni** finestra. (Si noti che è possibile aggiungere riferimenti usando direttamente il **Aggiungi riferimento** comando le **progetto** dal menu o indirettamente, trascinare un controllo ActiveX nel form.)  
  
   La procedura seguente illustra come isolare il componente COM e pubblicare l'applicazione aggiornata che contiene il controllo di tipo isolato:  
  
##### <a name="to-isolate-a-com-component"></a>Per isolare un componente COM  
  
1. Nella **Esplora soluzioni**, nella **riferimenti** nodo, seleziona il **VB6Hello** riferimento.  
  
2. Nel **proprietà** finestra, modificare il valore della **Isolated** proprietà dal **False** a **True**.  
  
3. Dal **compilare** menu, fare clic su **Compila soluzione**.  
  
   A questo punto, quando si preme F5, l'applicazione funzionerà come previsto, ma ora è in esecuzione in COM senza registrazione. Per dimostrare questo, provare l'annullamento della registrazione del componente VB6Hello e in esecuzione RegFreeComDemo1.exe di fuori di IDE di Visual Studio. Questa volta quando viene scelto il pulsante, continuerà a funzionare. Se si rinomina temporaneamente il manifesto dell'applicazione, anche in questo caso non riuscirà.  
  
> [!NOTE]
>  È possibile simulare l'assenza di un componente COM annullarne temporaneamente. Aprire un prompt dei comandi, passare alla cartella di sistema digitando `cd /d %windir%\system32`, quindi annullare la registrazione del componente digitando `regsvr32 /u VB6Hello.dll`. È possibile registrarlo nuovamente digitando `regsvr32 VB6Hello.dll`.  
  
 Il passaggio finale consiste nel pubblicare l'applicazione usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Per pubblicare un aggiornamento dell'applicazione con un componente COM isolato  
  
1. Dal **compilare** menu, fare clic su **pubblicare RegFreeComDemo**.  
  
    Verrà visualizzata la Pubblicazione guidata.  
  
2. Nella pubblicazione guidata, specificare un percorso nel disco del computer locale in cui è possibile accedere ed esaminare i file pubblicati.  
  
3. Fare clic su **fine** per pubblicare l'applicazione.  
  
   Se si esaminano i file pubblicati, si noterà che il file Sysmon. ocx sia incluso. Il controllo è completamente isolata e prevede l'applicazione, vale a dire che, se macchina dell'utente finale ha un'altra applicazione utilizza una versione diversa del controllo, non può interferire con l'applicazione.  
  
## <a name="reference-native-assemblies"></a>Assembly di riferimento nativi  
 Visual Studio supporta riferimenti agli assembly C++; o nativo Visual Basic 6.0 tali riferimenti vengono chiamati i riferimenti nativi. È possibile indicare se un riferimento è nativo verificando che relativi **tipo di File** è impostata su **nativo** oppure **ActiveX**.  
  
 Per aggiungere un riferimento nativo, usare il **Aggiungi riferimento** comando, quindi passare al manifesto. Alcuni componenti di inserire il manifesto all'interno della DLL. In questo caso, è sufficiente scegliere la DLL e Visual Studio vengono aggiunte automaticamente come un riferimento nativo se rileva che il componente include un manifesto incorporato. Visual Studio includerà anche automaticamente eventuali file dipendenti o assembly elencati nel manifesto se fossero nella stessa cartella del componente di riferimento.  
  
 Isolamento del controllo COM rende facile da distribuire i componenti COM che non dispongono già dei manifesti. Tuttavia, se un componente viene fornito con un manifesto, è possibile fare riferimento il manifesto direttamente. Infatti, si dovrebbe usare sempre il manifesto fornito dall'autore del componente, laddove possibile, invece di usare la **Isolated** proprietà.  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Limitazioni della distribuzione dei componenti COM senza registrazione  
 COM senza registrazione offre vantaggi non crittografati tramite le tecniche di distribuzione tradizionali. Tuttavia, esistono alcune limitazioni e avvertenze che devono anche essere sono evidenziate. Il limite massimo è che funziona solo in Windows XP o versione successiva. L'implementazione di COM senza registrazione ha richiesto modifiche al modo in cui i componenti vengono caricati nel sistema operativo core. Non esiste alcun livello di supporto di livello inferiore per COM senza registrazione.  
  
 Non tutti i componenti sono un candidato idoneo per COM senza registrazione. Un componente non è un valore appropriato se viene soddisfatta una delle operazioni seguenti:  
  
- Il componente è un server out-of-process. Server di file EXE non sono supportati; sono supportate solo le DLL.  
  
- Il componente fa parte del sistema operativo, o è un componente del sistema, ad esempio XML, Internet Explorer o Microsoft Data Access Components (MDAC). È necessario seguire il criterio di ridistribuzione dell'autore del componente; rivolgersi al fornitore.  
  
- Il componente è parte di un'applicazione, ad esempio Microsoft Office. Ad esempio, non tentare di isolare il modello oggetto di Microsoft Excel. Ciò fa parte di Office e può essere utilizzato solo in un computer con il prodotto completo Office installato.  
  
- Il componente deve essere utilizzato come un componente aggiuntivo o uno snap-in, ad esempio un componente aggiuntivo di Office o un controllo in un Web browser. Tali componenti richiedono in genere qualche tipo di schema di registrazione definito dall'ambiente di hosting che esula dall'ambito del manifesto.  
  
- Il componente gestisce un dispositivo fisico o virtuale per il sistema, ad esempio, un driver di dispositivo per uno spooler di stampa.  
  
- Il componente è un accesso ai dati ridistribuibile. Applicazioni di dati richiedono in genere un accesso ai dati ridistribuibili da installare prima che possano eseguire. Non provare a isolare i componenti, ad esempio il controllo dati ADO di Microsoft, Microsoft OLE DB o Microsoft Data Access Components (MDAC). In alternativa, se l'applicazione usa MDAC o SQL Server Express, è necessario impostarli come prerequisiti; visualizzare [procedura: installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
  In alcuni casi, potrebbe essere possibile per lo sviluppatore del componente, riprogettare per COM senza registrazione. Se questo non è possibile, è possibile compilare e pubblicare applicazioni che dipendono da essi tramite lo schema di registrazione standard usando il programma di bootstrap. Per altre informazioni, vedere [creazione di pacchetti Bootstrapper](../deployment/creating-bootstrapper-packages.md).  
  
  Un componente COM può essere solo una volta isolato per ogni applicazione. Ad esempio, non puoi isolare stesso componente COM da due diverse **libreria di classi** progetti che fanno parte della stessa applicazione. Questa operazione comporterà un avviso di compilazione e l'applicazione avrà esito negativo caricare in fase di esecuzione. Per evitare questo problema, è consigliabile incapsulare i componenti COM in un'unica libreria di classi.  
  
  Esistono diversi scenari COM è necessario eseguire la registrazione sul computer dello sviluppatore, anche se la distribuzione dell'applicazione non richiede la registrazione. Il `Isolated` proprietà richiede che il componente COM sia registrato nel computer dello sviluppatore per generare automaticamente il manifesto durante la compilazione. Non sono disponibili funzionalità per l'acquisizione di registrazione che richiamano la registrazione automatica durante la compilazione. Inoltre, tutte le classi non esplicitamente definite nella libreria dei tipi non si rifletteranno nel manifesto. Quando si usa un componente COM con un manifesto di pre-esistente, ad esempio un riferimento nativo, il componente non debba essere registrata in fase di sviluppo. Tuttavia, la registrazione è obbligatoria se il componente è un controllo ActiveX e si desidera includerlo nel **casella degli strumenti** e in Progettazione Windows Form.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)