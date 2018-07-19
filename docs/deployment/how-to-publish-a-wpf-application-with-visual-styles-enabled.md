---
title: "Procedura: pubblicare un'applicazione WPF con gli stili visuali abilitati | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2620a008a90b988aa80df8d3c8563163ff92d997
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078378"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Procedura: pubblicare un'applicazione WPF con gli stili visuali abilitati
Stili di abilitare l'aspetto dei controlli comuni da variare in base al tema scelto dall'utente. Per impostazione predefinita, gli stili di visualizzazione non abilitati per le applicazioni Windows Presentation Foundation (WPF), pertanto è necessario attivarli manualmente. Abilitazione degli stili per un'applicazione WPF e quindi pubblicare la soluzione, tuttavia, provoca un errore. Questo argomento descrive come risolvere questo errore e il processo per la pubblicazione di un'applicazione WPF con gli stili visuali abilitati. Per altre informazioni sugli stili di visualizzazione, vedere [panoramica degli stili di visualizzazione](/windows/desktop/Controls/visual-styles-overview). Per altre informazioni sul messaggio di errore, vedere [risolvere i problemi di errori specifici nelle distribuzioni ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).  
  
 Per risolvere l'errore e pubblicare la soluzione, è necessario eseguire le attività seguenti:  
  
-   [Pubblicare la soluzione senza gli stili visuali abilitati](#publish-the-solution-without-visual-styles-enabled).  
  
-   [Creare un file manifesto](#create-a-manifest-file).  
  
-   [Incorporare il file manifesto nel file eseguibile della soluzione pubblicata](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution).  
  
-   [Firmare i manifesti dell'applicazione e della distribuzione](#sign-the-application-and-deployment-manifests).  
  
 Quindi, è possibile spostare i file pubblicati il posizione da cui si desidera che gli utenti finali a installare l'applicazione.  
  
##  <a name="publish-the-solution-without-visual-styles-enabled"></a>Pubblicare la soluzione senza gli stili visuali abilitati  
  
1.  Assicurarsi che il progetto non ha abilitati gli stili di visualizzazione. In primo luogo, verificare i file manifesto del progetto per il codice XML seguente. Quindi, se il codice XML è presente, racchiudere il codice XML con un tag di commento.  
  
     Per impostazione predefinita, gli stili di visualizzazione non sono abilitati.  
  
    ```xml  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     Le procedure seguenti illustrano come aprire il file manifesto associato al progetto.  
  
    ###### <a name="to-open-the-manifest-file-in-a-visual-basic-project"></a>Per aprire il file manifesto in un progetto Visual Basic  
  
    1.  Nella barra dei menu, scegliere **Project**, *NomeProgetto* **proprietà**, dove *NomeProgetto* è il nome del progetto WPF.  
  
         Vengono visualizzate le pagine delle proprietà per il progetto WPF.  
  
    2.  Nel **Application** scheda, scegliere **le impostazioni di Windows Vista**.  
  
         Il file app. manifest verrà aperto nel **Editor di codice**.  
  
    ###### <a name="to-open-the-manifest-file-in-a-c-project"></a>Per aprire il file manifesto in un progetto c#  
  
    1.  Nella barra dei menu, scegliere **Project**, *NomeProgetto* **proprietà**, dove *NomeProgetto* è il nome del progetto WPF.  
  
         Vengono visualizzate le pagine delle proprietà per il progetto WPF.  
  
    2.  Nel **applicazione** scheda, prendere nota del nome che viene visualizzato nel campo del manifesto. Si tratta del nome del manifesto associato al progetto.  
  
        > [!NOTE]
        >  Se **Incorpora manifesto con impostazioni predefinite** oppure **Crea applicazione senza manifesto** vengono visualizzati nel campo del manifesto, non sono abilitati gli stili di visualizzazione. Se il nome di un file manifesto viene visualizzato nel campo del manifesto, procedere al passaggio successivo in questa procedura.  
  
    3.  Nelle **Esplora soluzioni**, scegliere **Mostra tutti i file**.  
  
         Questo pulsante Mostra tutti gli elementi di progetto, inclusi quelli che sono stati esclusi e quelli che sono normalmente nascosti. Il file manifesto viene visualizzato come un elemento del progetto.  
  
2.  Creare e pubblicare la soluzione. Per altre informazioni su come pubblicare la soluzione, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## <a name="create-a-manifest-file"></a>Creare un file manifesto  
  
1.  Incollare il codice XML seguente in un file di blocco note.  
  
     Questo codice XML descrive l'assembly che contiene i controlli che supportano gli stili di visualizzazione.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  Nel blocco note, fare clic su **File**, quindi fare clic su **Salva con nome**.  
  
3.  Nel **Salva con nome** nella finestra di dialogo il **Salva come tipo** elenco a discesa, seleziona **tutti i file**.  
  
4.  Nel **nomefile** casella, denominare il file e di Accodamento *manifest* alla fine del nome del file. Ad esempio: *themes.manifest*.  
  
5.  Scegliere il **Sfoglia cartelle** pulsante, selezionare una cartella specifica e quindi fare clic su **salvare**.  
  
    > [!NOTE]
    >  Nelle procedure restanti si presuppone che il nome di questo file sia *themes.manifest* e che il file viene salvato il *C:\temp* directory nel computer.  
  
## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>Incorporare il file manifesto nel file eseguibile della soluzione pubblicata  
  
1.  Aprire il **prompt dei comandi di Visual Studio**.  
  
     Per altre informazioni su come aprire la **Prompt dei comandi di Visual Studio**, vedere [prompt dei comandi](/dotnet/framework/tools/developer-command-prompt-for-vs).  
  
    > [!NOTE]
    >  I passaggi rimanenti partono dai presupposti seguenti sulla soluzione:  
    >   
    >  -   È il nome della soluzione **MyWPFProject**.  
    > -   La soluzione si trova nella seguente directory: `%UserProfile%\Documents\Visual Studio 2010\Projects\`.  
    >   
    >      La soluzione viene pubblicata nella directory seguente: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`.  
    > -   La versione più recente dei file dell'applicazione pubblicata si trova nella directory seguente: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
    >   
    >  Non è necessario usare il nome o i percorsi delle directory descritti in precedenza. Il nome e i percorsi descritti sopra sono utilizzati solo per illustrare i passaggi necessari per pubblicare la propria soluzione.  
  
2.  Al prompt dei comandi, modificare il percorso della directory che contiene la versione più recente dei file dell'applicazione pubblicata. L'esempio seguente illustra questo passaggio.  
  
    ```cmd  
cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
    ```  
  
3.  Al prompt dei comandi, eseguire il comando seguente per includere il file manifesto nel file eseguibile dell'applicazione.  
  
    ```cmd
    mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy  
    ```  
  
## <a name="sign-the-application-and-deployment-manifests"></a>Firmare i manifesti dell'applicazione e della distribuzione  
  
1.  Al prompt dei comandi, eseguire il comando seguente per rimuovere il *deploy* estensione dal file eseguibile nella directory corrente.  
  
    ```cmd  
    ren MyWPFApp.exe.deploy MyWPFApp.exe  
    ```  
  
    > [!NOTE]
    >  Questo esempio si presuppone che un solo file con il *deploy* estensione di file. Assicurarsi che non è rinominare tutti i file in questa directory contenenti i *deploy* estensione di file.  
  
2.  Al prompt dei comandi, eseguire il comando seguente per firmare il manifesto dell'applicazione.  
  
    ```cmd  
    mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  Questo esempio si presuppone che il manifesto viene firmata usando il *PFX* file del progetto. Se non si firmano il manifesto, è possibile omettere il `-cf` parametro utilizzato in questo esempio. Se si firmano del manifesto con un certificato che richiede una password, specificare il `-password` opzione (`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`).  
  
3.  Al prompt dei comandi, eseguire il comando seguente per aggiungere il *deploy* estensione per il nome del file che è stato rinominato in un passaggio precedente di questa procedura.  
  
    ```  
    ren MyWPFApp.exe MyWPFApp.exe.deploy  
    ```  
  
    > [!NOTE]
    >  Questo esempio si presuppone che un solo file aveva una *deploy* estensione di file. Assicurarsi che non è rinominare tutti i file in questa directory che in precedenza era il *deploy* estensione del nome file.  
  
4.  Al prompt dei comandi, eseguire il comando seguente per firmare il manifesto della distribuzione.  
  
    ```  
    mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  Questo esempio si presuppone che il manifesto viene firmata usando il *PFX* file del progetto. Se non si firmano il manifesto, è possibile omettere il `-cf` parametro utilizzato in questo esempio. Se si firmano del manifesto con un certificato che richiede una password, specificare il `-password` opzione, come nel seguente esempio:`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`.  
  
 Dopo aver eseguito questi passaggi, è possibile spostare i file pubblicati il posizione da cui si desidera che gli utenti finali a installare l'applicazione. Se si intende aggiornare spesso la soluzione, è possibile spostare questi comandi in uno script ed eseguire lo script ogni volta che si pubblica una nuova versione.  
  
## <a name="see-also"></a>Vedere anche  
 [Risolvere errori specifici nelle distribuzioni ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)   
 [Panoramica degli stili di visualizzazione](/windows/desktop/Controls/visual-styles-overview)   
 [Abilitare gli stili visivi](https://msdn.microsoft.com/library/bb773175.aspx)   
 [Prompt dei comandi](/dotnet/framework/tools/developer-command-prompt-for-vs)