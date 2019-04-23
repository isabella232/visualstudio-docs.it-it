---
title: Distribuire una soluzione Office usando ClickOnce
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 940cf70047437c8aa3182121e8b1585b448018f8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060740"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Distribuire una soluzione Office usando ClickOnce
  L'uso di ClickOnce consente di distribuire una soluzione Office in un minor numero di passaggi. Eventuali aggiornamenti alla soluzione pubblicati vengono rilevati e installati automaticamente. Tuttavia, ClickOnce richiede che la soluzione venga installata separatamente per ciascun utente di un computer. Pertanto, è necessario considerare tramite Windows Installer (*file con estensione msi*) se la soluzione sarà eseguita da più di un utente nello stesso computer.

## <a name="in-this-topic"></a>Contenuto dell'argomento

- [Pubblicare la soluzione](#Publish)

- [Scegliere come si desidera concedere l'attendibilità alla soluzione](#Trust)

- [Consentire agli utenti di installare la soluzione](#Helping)

- [Inserire il documento di una soluzione nel computer dell'utente finale (solo personalizzazioni a livello di documento)](#Put)

- [Inserire il documento di una soluzione in un server di cui è eseguito SharePoint (solo personalizzazioni a livello di documento)](#SharePoint)

- [Creare un programma di installazione personalizzato](#Custom)

- [Pubblicare un aggiornamento](#Update)

- [Modificare il percorso di installazione di una soluzione](#Location)

- [Eseguire il rollback di una soluzione a una versione precedente](#Roll)

  Per altre informazioni su come distribuire una soluzione Office creando un file Windows Installer, vedere [distribuire una soluzione Office tramite Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

## <a name="Publish"></a> Pubblicare la soluzione
 È possibile pubblicare la soluzione usando il **pubblicazione guidata** o nella **creazione progetti**. In questa procedura, userai i **Progettazione progetti** perché fornisce il set completo di opzioni di pubblicazione. Visualizzare [pubblicazione guidata di &#40;sviluppo per Office in Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>Per pubblicare la soluzione

1. Nelle **Esplora soluzioni**, scegliere il nodo denominato per il progetto.

2. Nella barra dei menu, scegliere **Project**, *NomeProgetto* **proprietà**.

3. Nel **creazione progetti**, scegliere il **Publish** scheda, come illustrato di seguito.

    ![Scheda pubblicazione della Progettazione progetti](../vsto/media/vsto-publishtab.png "scheda pubblica della Progettazione progetti")

4. Nel **posizione cartella di pubblicazione (server ftp o percorso file)** immettere il percorso della cartella in cui si desidera il **creazione progetti** per copiare i file della soluzione.

    È possibile fornire uno dei seguenti tipi di percorso.

   - Un percorso locale (ad esempio, *C:\FolderName\FolderName*).

   - Un percorso di Uniform Naming Convention (UNC) in una cartella sulla rete (ad esempio,  *\\\ServerName\FolderName*).

   - Un percorso relativo (ad esempio, *PublishFolder\\*, ovvero la cartella in cui il progetto viene pubblicato per impostazione predefinita).

5. Nel **URL cartella di installazione** immettere il percorso completo della posizione in cui gli utenti finali troveranno la soluzione.

    Se ancora non si conosce il percorso, non immettere nulla in questo campo. Per impostazione predefinita, quando si usa ClickOnce, gli aggiornamenti vengono cercati nella cartella da cui gli utenti installano la soluzione.

6. Scegliere il pulsante **Prerequisiti** .

7. Nel **prerequisiti** finestra di dialogo casella, verificare che il **Crea programma di installazione per installare i componenti prerequisiti** casella di controllo è selezionata.

8. Nel **scegliere i prerequisiti da installare** , selezionare le caselle di controllo **Windows Installer 4.5** e il pacchetto .NET Framework appropriato.

    Ad esempio, se la soluzione è destinata al [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], selezionare le caselle di controllo **Windows Installer 4.5** e **Microsoft .NET Framework 4.5 Full**.

9. Se la soluzione è destinata a .NET Framework 4.5, selezionare anche il **Visual Studio 2010 Tools per Office Runtime** casella di controllo.

    > [!NOTE]
    >  Per impostazione predefinita, questa casella di controllo non viene visualizzato. Per visualizzarla, è necessario creare un pacchetto di programma di avvio automatico. Visualizzare [creare un pacchetto di programma di avvio automatico per Office 2013 VSTO Add-in con Visual Studio 2012](create-vsto-add-ins-for-office-by-using-visual-studio.md).

10. Sotto **specificare il percorso di installazione dei prerequisiti**, scegliere una delle opzioni che vengono visualizzati e quindi scegliere il **OK** pulsante.

     Nella tabella seguente viene descritta ciascuna opzione.

    |Opzione|Descrizione|
    |------------|-----------------|
    |**Scarica prerequisiti dal sito Web del fornitore del componente**|All'utente viene chiesto di scaricare e installare questi prerequisiti dal fornitore.|
    |**Scarica prerequisiti dallo stesso percorso dell'applicazione**|Il software prerequisito viene installato insieme alla soluzione. Se si seleziona questa opzione, tutti i pacchetti di prerequisiti vengono copiati automaticamente da Visual Studio nel percorso di pubblicazione. Per il corretto funzionamento di questa opzione, i pacchetti di prerequisiti devono essere presenti nel computer di sviluppo.|
    |**Scarica prerequisiti dal seguente percorso**|Tutti i pacchetti di prerequisiti vengono copiati da Visual Studio nella posizione specificata e vengono installati insieme alla soluzione.|

     Visualizzare [finestra di dialogo Prerequisiti](../ide/reference/prerequisites-dialog-box.md).

11. Scegliere il **aggiornamenti** pulsante, specificare quanto spesso si desidera ogni utente finale del componente aggiuntivo VSTO o personalizzazione per verificare la presenza di aggiornamenti e quindi scegliere il **OK** pulsante.

    > [!NOTE]
    >  Se si distribuisce tramite un CD o un'unità rimovibile, scegliere il **mai zkontrolovat aktualizace** pulsante di opzione.

     Per informazioni su come pubblicare un aggiornamento, vedere [pubblicare un aggiornamento](#Update).

12. Scegliere il **opzioni** pulsante, esaminare le opzioni nella **opzioni** dialogo casella e quindi scegliere il **OK** pulsante.

13. Scegliere il **pubblica** pulsante.

     Le cartelle e i file seguenti vengono aggiunti automaticamente da Visual Studio nella cartella di pubblicazione specificata precedentemente in questa procedura.

    - Il **i file dell'applicazione** cartella.

    - Programma di installazione.

    - Manifesto di distribuzione che punta al manifesto di distribuzione della versione più recente.

      Il **i file dell'applicazione** cartella contiene una sottocartella per ogni versione pubblicata. Ogni sottocartella relativa a una versione specifica contiene i file indicati di seguito.

    - Un manifesto dell'applicazione.

    - Un manifesto di distribuzione.

    - Assembly di personalizzazione.

      Nell'illustrazione seguente viene mostrata la struttura della cartella di pubblicazione di un componente aggiuntivo VSTO di Outlook.

      ![Struttura di cartelle di pubblicazione](../vsto/media/publishfolderstructure.png "pubblicare struttura di cartelle")

    > [!NOTE]
    >  ClickOnce consente di accodare il *deploy* estensione agli assembly in modo che un'installazione protetta di Internet Information Services (IIS) non bloccherà i file a causa di un'estensione non sicura. Quando l'utente installa la soluzione, rimossa da ClickOnce il *deploy* estensione.

14. Copiare i file della soluzione nel percorso di installazione specificato precedentemente in questa procedura.

## <a name="Trust"></a> Scegliere come si desidera concedere l'attendibilità alla soluzione
 Prima che una soluzione possa essere eseguita nei computer degli utenti, è necessario concedere l'attendibilità oppure gli utenti devono rispondere a una richiesta di attendibilità quando installano la soluzione. Per concedere l'attendibilità alla soluzione, firmare i manifesti usando un certificato che identifichi un editore conosciuto e attendibile. Visualizzare [considerare attendibile la soluzione firmando i manifesti dell'applicazione e distribuzione](../vsto/granting-trust-to-office-solutions.md#Signing).

 Se si distribuisce una personalizzazione a livello di documento e si vuole inserire il documento in una cartella nel computer dell'utente o rendere disponibile il documento in un sito di SharePoint, verificare che Office consideri attendibile il percorso del documento. Visualizzare [concedere l'attendibilità a documenti](../vsto/granting-trust-to-documents.md).

## <a name="Helping"></a> Consentire agli utenti di installare la soluzione
 Gli utenti possono installare la soluzione eseguendo il programma di installazione, aprendo il manifesto di distribuzione o durante la personalizzazione a livello di documento, aprendo direttamente il documento. Come procedura consigliata, gli utenti devono installare la soluzione usando il programma di installazione. Gli altri due approcci non garantiscono che i prerequisiti software siano installati. Se gli utenti desiderano aprire il documento dal percorso di installazione, devono aggiungerlo all'elenco dei percorsi attendibili nel Centro protezione dell'applicazione di Office.

### <a name="opening-the-document-of-a-document-level-customization"></a>Apertura del documento di una personalizzazione a livello di documento
 Gli utenti possono aprire il documento di una personalizzazione a livello di documento direttamente dal percorso di installazione oppure copiando il documento nei propri computer locali e aprendo quindi la copia.

 Come procedura consigliata, gli utenti devono aprire una copia del documento nei computer locali per evitare che più utenti tentino di aprire la stessa copia contemporaneamente. Per applicare questo approccio, è possibile configurare il programma di installazione in modo da copiare il documento nei computer degli utenti. Visualizzare [inserire il documento di una soluzione nel computer dell'utente finale (solo personalizzazioni a livello di documento)](#Put).

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Installare la soluzione aprendo il manifesto di distribuzione da un sito Web IIS
 Gli utenti possono installare una soluzione Office aprendo il manifesto di distribuzione dal Web. Tuttavia, un'installazione protetta di Internet Information Services (IIS) bloccherà i file con il *VSTO* estensione. Il tipo MIME deve essere definito in IIS prima di poter distribuire una soluzione Office tramite IIS.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Per aggiungere il tipo MIME .vsto a IIS 6.0

1. Nel server che esegue IIS 6.0, scegliere **avviare** > **tutti i programmi** > **strumenti di amministrazione**  >   **Gestione Internet Information Services (IIS)**.

2. Scegliere il nome del computer, il **siti Web** cartella o il sito web che si sta configurando.

3. Nella barra dei menu, scegliere **azione** > **proprietà**.

4. Nel **intestazioni HTTP** scheda, scegliere il **tipi MIME** pulsante.

5. Nel **tipi MIME** finestra, scegliere il **New** pulsante.

6. Nel **tipo MIME** finestra, immettere **VSTO** come estensione, immettere **application/x-ms-vsto** come MIME digitare e quindi applicare le nuove impostazioni.

    > [!NOTE]
    >  Per rendere effettive le modifiche è necessario riavviare il servizio Pubblicazione sul Web o attendere il riciclo del processo di lavoro. È necessario punto svuotare la cache del browser del disco e quindi provare ad aprire il *VSTO* file nuovo.

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Per aggiungere il tipo MIME .vsto a IIS 7.0

1. Nel server che esegue IIS 7.0, scegliere **avviare** > **tutti i programmi** > **Accessori**.

2. Aprire il menu di scelta rapida **prompt dei comandi**, quindi scegliere **Esegui come amministratore.**

3. Nel **aperto** casella, immettere il percorso seguente e quindi scegliere il **OK** pulsante.

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Immettere il seguente comando, quindi applicare le nuove impostazioni.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    >  Per rendere effettive le modifiche è necessario riavviare il servizio Pubblicazione sul Web o attendere il riciclo del processo di lavoro. È necessario punto svuotare la cache del browser del disco e quindi provare ad aprire il *VSTO* file nuovo.

## <a name="Put"></a> Inserire il documento di una soluzione nel computer dell'utente finale (solo personalizzazioni a livello di documento)
 È possibile copiare il documento della soluzione nel computer dell'utente finale per essi mediante la creazione di un'azione post-distribuzione. In questo modo, l'utente non dovrà copiare manualmente il documento dal percorso di installazione nei propri computer dopo l'installazione della soluzione. È possibile creare una classe che definisca l'azione post-distribuzione, compilare e pubblicare la soluzione, modificare il manifesto dell'applicazione e firmare nuovamente il manifesto dell'applicazione e la distribuzione.

 Le procedure seguenti presuppongono che sia il nome del progetto **ExcelWorkbook** e si pubblica la soluzione in una cartella creata denominata **C:\publish** nel computer.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Creare una classe che definisca l'azione post-distribuzione

1. Nella barra dei menu, scegliere **File** > **Add** > **nuovo progetto**.

2. Nel **Aggiungi nuovo progetto** nella finestra di dialogo il **modelli installati** riquadro, scegliere il **Windows** cartella.

3. Nel **modelli** riquadro, scegliere il **libreria di classi** modello.

4. Nel **nome** immettere **FileCopyPDA**, quindi scegliere il **OK** pulsante.

5. Nelle **Esplora soluzioni**, scegliere il **FileCopyPDA** progetto.

6. Nella barra dei menu scegliere **Progetto** > **Aggiungi riferimento**.

7. Nel **.NET** scheda, aggiungere i riferimenti agli `Microsoft.VisualStudio.Tools.Applications.Runtime` e `Microsoft.VisualStudio.Tools.Applications.ServerDocument`.

8. Rinominare la classe in `FileCopyPDA`, quindi sostituire il contenuto del file con il codice. Mediante il codice vengono effettuate le seguenti attività:

   - Copia del documento sul desktop dell'utente.

   - Modifica la proprietà AssemblyLocation da un percorso relativo a un percorso completo per il manifesto di distribuzione.

   - Eliminazione del file se l'utente disinstalla la soluzione.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>Compilare e pubblicare la soluzione

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **FileCopyPDA** del progetto e quindi scegliere **compilare**.

2. Aprire il menu di scelta rapida per il **ExcelWorkbook** del progetto e quindi scegliere **compilazione**.

3. Aprire il menu di scelta rapida per il **ExcelWorkbook** del progetto e quindi scegliere **Aggiungi riferimento**.

4. Nel **Aggiungi riferimento** finestra di dialogo scegliere la **progetti** scheda, scegliere **FileCopyPDA**e quindi scegliere il **OK** pulsante.

5. Nelle **Esplora soluzioni**, scegliere il **ExcelWorkbook** progetto.

6. Nella barra dei menu, scegliere **Project** > **nuova cartella**.

7. Invio **Data**, quindi scegliere il **invio** chiave.

8. Nelle **Esplora soluzioni**, scegliere il **dati** cartella.

9. Nella barra dei menu, scegliere **Project** > **Aggiungi elemento esistente**.

10. Nel **Aggiungi elemento esistente** finestra di dialogo, individuare la directory di output per il **ExcelWorkbook** del progetto, scegliere il **ExcelWorkbook. xlsx** file e quindi scegliere il  **Aggiungere** pulsante.

11. Nelle **Esplora soluzioni** scegliere i **ExcelWorkbook. xlsx** file.

12. Nel **proprietà** finestra Modifica il **azione di compilazione** proprietà **contenuto** e il **Copy to Output Directory** proprietà  **Copia se più recente**.

     Dopo aver completato questi passaggi, il progetto sarà simile al seguente.

     ![Struttura del progetto dell'azione post-distribuzione. ](../vsto/media/vsto-postdeployment.png "Struttura progetto dell'azione post-distribuzione.")

13. Pubblicare i **ExcelWorkbook** progetto.

### <a name="modify-the-application-manifest"></a>Modificare il manifesto dell'applicazione

1. Directory della soluzione, aprire **c:\publish**, usando **Esplora File**.

2. Aprire il **i file dell'applicazione** cartella e quindi aprire la cartella che corrisponde a più recente pubblicata versione della soluzione.

3. Aprire il **ExcelWorkbook** file in un editor di testo quale Blocco note.

4. Dopo l'elemento `</vstav3:update>` aggiungere il codice seguente. Per l'attributo di classe dell'elemento `<vstav3:entryPoint>` usare la sintassi seguente: *NamespaceName*. Nell'esempio riportato di seguito il nome dello spazio dei nomi è uguale a quello della classe. Pertanto, il nome del punto di ingresso risultante è `FileCopyPDA.FileCopyPDA`.

    ```xml
    <vstav3:postActions>
      <vstav3:postAction>
        <vstav3:entryPoint
          class="FileCopyPDA.FileCopyPDA">
          <assemblyIdentity
            name="FileCopyPDA"
            version="1.0.0.0"
            language="neutral"
            processorArchitecture="msil" />
        </vstav3:entryPoint>
        <vstav3:postActionData>
        </vstav3:postActionData>
      </vstav3:postAction>
    </vstav3:postActions>
    ```

### <a name="re-sign-the-application-and-deployment-manifests"></a>Firmare nuovamente i manifesti dell'applicazione e di distribuzione

1. Nel **%USERPROFILE%\Documents\Visual Studio 2013\Projects\ExcelWorkbook\ExcelWorkbook** copiare il **Excelworkbook_temporarykey** file di certificato e quindi incollarlo nella  *PublishFolder* **\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ cartella.

2. Aprire il prompt dei comandi di Visual Studio e quindi passare alla directory per il **c:\publish\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ cartella (ad esempio **c:\publish\Application Files\ExcelWorkbook_1_0_0_4**).

3. Firmare il manifesto dell'applicazione modificato usando il comando seguente:

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     Verrà visualizzato il messaggio "ExcelWorkbook.dll.manifest firmato correttamente".

4. Modificare il **c:\publish** cartella e quindi aggiornamento e la distribuzione di accesso del manifesto eseguendo il comando seguente:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    >  Nell'esempio precedente, sostituire MostRecentVersionNumber con il numero di versione della versione più recente pubblicata della soluzione (ad esempio, **1_0_0_4**).

     Verrà visualizzato il messaggio "ExcelWorkbook.vsto firmato correttamente".

5. Copia il *ExcelWorkbook* del file per il **c:\publish\Application Files\ExcelWorkbook**\__MostRecentVersionNumber_ directory.

## <a name="SharePoint"></a> Inserire il documento di una soluzione in un server di cui è eseguito SharePoint (solo personalizzazioni a livello di documento)
 È possibile pubblicare la personalizzazione a livello di documento agli utenti finali tramite SharePoint. Quando gli utenti visitano il sito di SharePoint e aprono il documento, la soluzione viene automaticamente installata dalla cartella di rete condivisa nei computer locali degli utenti. Una volta che la soluzione è installata localmente, la personalizzazione continuerà a essere valida anche se il documento viene copiato in un'altra posizione, ad esempio sul desktop.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Per inserire il documento in un server in cui è eseguito SharePoint

1. Aggiungere il documento della soluzione a una raccolta documenti su un sito di SharePoint.

2. Effettuare i passaggi per uno degli approcci indicati di seguito:

    - Usare lo strumento di configurazione di Office per aggiungere il server in cui è eseguito SharePoint al Centro protezione in Word o Excel in tutti i computer degli utenti.

         Visualizzare [i criteri di sicurezza e impostazioni di Office 2010](http://go.microsoft.com/fwlink/?LinkId=99227).

    - Assicurarsi che ogni utente esegua i passaggi indicati di seguito.

        1. Nel computer locale, aprire Word o Excel, scegliere il **File** scheda e quindi scegliere il **opzioni** pulsante.

        2. Nel **Trust Center** finestra di dialogo scegliere la **percorsi attendibili** pulsante.

        3. Selezionare il **Consenti percorsi attendibili sulla mia rete (scelta non consigliata)** casella di controllo e quindi scegliere il **aggiunta nuovo percorso** pulsante.

        4. Nel **percorso** immettere l'URL della raccolta documenti di SharePoint che contiene il documento che è stato caricato (ad esempio *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*).

             Non aggiungere il nome della pagina Web predefinita, ad esempio *default. aspx* oppure *AllItems. aspx*.

        5. Selezionare il **sottocartelle di questo percorso verranno considerati attendibili** casella di controllo e quindi scegliere il **OK** pulsante.

             Nel momento in cui gli utenti aprono il documento dal sito di SharePoint, il documento viene aperto e la personalizzazione viene installata. Gli utenti possono copiare il documento sul proprio desktop. L'esecuzione della personalizzazione continuerà perché le proprietà nel documento puntano al percorso di rete del documento.

## <a name="Custom"></a> Creare un programma di installazione personalizzato
 È possibile creare un programma di installazione personalizzato per la soluzione Office, anziché usare il programma di installazione che viene creato automaticamente quando si pubblica la soluzione. Ad esempio, è possibile usare un segno nello script per avviare l'installazione oppure è possibile usare un file batch per installare la soluzione senza interazione dell'utente. Questi scenari offrono i risultati migliori se i prerequisiti sono già installati nei computer degli utenti finali.

 Come parte del processo di installazione personalizzata, chiamare lo strumento programma di installazione per le soluzioni Office (*VSTOInstaller.exe*), impostazione predefinita che viene installato nel percorso seguente:

 *shared\VSTO\10.0\VSTOInstaller.exe %CommonProgramFiles%\Microsoft*

 Se lo strumento non è in tale percorso, è possibile usare la **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath** o **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4 \InstallerPath** chiave del Registro di sistema per individuare il percorso dello strumento.

 È possibile usare i parametri seguenti con *VSTOinstaller.exe*.

| Parametro | Definizione |
|------------------| - |
| /Install o /I | Installa la soluzione. È necessario seguire questa opzione con il percorso di un manifesto di distribuzione. È possibile specificare un percorso sul computer locale o di una condivisione file UNC (Universal Naming Convention). È possibile specificare un percorso locale (*C:\FolderName\PublishFolder*), un percorso relativo (*Publish\\*), o un percorso completo (*\\\ServerName\ FolderName* o http://<em>ServerName/FolderName</em>). |
| /Uninstall o /U | Disinstalla la soluzione. È necessario seguire questa opzione con il percorso di un manifesto di distribuzione. È possibile specificare che un percorso che può essere nel computer locale o in una condivisione file UNC. È possibile specificare un percorso locale (*c:\FolderName\PublishFolder*), un percorso relativo (*Publish\\*), o un percorso completo (*\\\ServerName\ FolderName* o http://<em>ServerName/FolderName</em>). |
| /Silent o /S | Installa o disinstalla senza richiedere input da parte dell'utente o visualizzare un messaggio. Se è necessaria una richiesta di attendibilità, la personalizzazione non è installata o aggiornata. |
| /Help o /? | Visualizza le informazioni della Guida. |

 Quando si esegue *VSTOinstaller.exe*, i codici di errore seguente potrebbe essere visualizzato.

|Codice di errore|Definizione|
|----------------|----------------|
|0|La soluzione è stata installata o disinstallata correttamente oppure è stata visualizzata la Guida di VSTOInstaller.|
|-100|Una o più opzioni della riga di comando non sono valide o sono state impostate più volte. Per altre informazioni, immettere "vstoinstaller /?" oppure vedere [creare un programma di installazione personalizzato per una soluzione ClickOnce Office](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e).|
|-101|Una o più opzioni della riga di comando non sono valide. Per altre informazioni, immettere "vstoinstaller /?".|
|-200|L'URI del manifesto di distribuzione non è valido. Per altre informazioni, immettere "vstoinstaller /?".|
|-201|Non è stato possibile installare la soluzione perché il manifesto di distribuzione non è valido. Visualizzare [manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md).|
|-202|Non è stato possibile installare la soluzione perché Visual Studio Tools per la sezione Office del manifesto dell'applicazione non è valido. Visualizzare [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).|
|-203|Non è stato possibile installare la soluzione perché si è verificato un errore di download. Controllare l'URI o il percorso del file di rete del manifesto di distribuzione, quindi provare di nuovo.|
|-300|Non è stato possibile installare la soluzione perché si è verificata un'eccezione di sicurezza. Visualizzare [soluzioni Office Secure](../vsto/securing-office-solutions.md).|
|-400|Non è stato possibile installare la soluzione.|
|-401|Non è stato possibile disinstallare la soluzione.|
|-500|L'operazione è stata annullata perché non è stato possibile installare o disinstallare la soluzione o scaricare il manifesto di distribuzione.|

## <a name="Update"></a> Pubblicare un aggiornamento
 Per aggiornare una soluzione, occorre pubblicarla nuovamente usando il **creazione progetti** oppure **pubblicazione guidata**, e quindi si copia la soluzione aggiornata nel percorso di installazione. Quando si copiano i file nel percorso di installazione, assicurarsi di sovrascrivere i file precedenti.

 La prossima volta che la soluzione controlla per un aggiornamento, verrà trovare e caricare automaticamente la nuova versione.

## <a name="Location"></a> Modificare il percorso di installazione di una soluzione
 È possibile aggiungere o modificare il percorso di installazione dopo la pubblicazione di una soluzione. È possibile che si desideri modificare il percorso di installazione per uno o più dei motivi seguenti:

- Il percorso di installazione non era noto quando il programma di installazione è stato compilato.

- I file della soluzione sono stati copiati in un percorso diverso.

- Il server che ospita i file di installazione ha un nome o un percorso nuovo.

  Per modificare il percorso di installazione di una soluzione, è necessario aggiornare il programma di installazione e successivamente gli utenti devono eseguirlo. Per le personalizzazioni a livello di documento, gli utenti devono aggiornare anche una proprietà nel proprio documento in modo che punti al nuovo percorso.

> [!NOTE]
>  Se non si desidera chiedere agli utenti di aggiornare le proprietà del documento, è possibile chiedere agli utenti di ottenere il documento aggiornato dal percorso di installazione.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Per modificare il percorso di installazione nel programma di installazione

1. Aprire una **prompt dei comandi** finestra e quindi passare alla cartella di installazione.

2. Eseguire il programma di installazione e includere il parametro `/url`, che assumerà come stringa il nuovo percorso di installazione.

    Nell'esempio seguente viene illustrato come modificare il percorso di installazione in un percorso sul sito Web di Fabrikam, ma è possibile sostituire tale URL con il percorso desiderato:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   >  Se viene visualizzato un messaggio per segnalare che la firma dell'eseguibile sarà invalidata, il certificato usato per firmare la soluzione non è più valido e l'editore è sconosciuto. Di conseguenza, gli utenti dovranno confermare l'attendibilità dell'origine della soluzione prima di poterla installare.

   > [!NOTE]
   >  Per visualizzare il valore corrente dell'URL, eseguire `setup.exe /url`.

   Per le personalizzazioni a livello di documento, gli utenti devono aprire il documento e quindi aggiornare la proprietà AssemblyLocation. Di seguito viene descritta la procedura che gli utenti devono seguire per eseguire questa attività.

#### <a name="to-update-the-assemblylocation-property-in-a-document"></a>Per aggiornare la proprietà _AssemblyLocation in un documento

1. Nel **File** scheda, scegliere **Info**, come illustrato di seguito.

     ![Scheda informazioni in Excel](../vsto/media/vsto-infotab.png "scheda informazioni in Excel")

2. Nel **delle proprietà** scegliere **delle proprietà avanzate**, mostrato nell'immagine seguente.

     ![Proprietà avanzate in Excel. ](../vsto/media/vsto-advanceddocumentproperties.png "Proprietà avanzate in Excel.")

3. Nel **Custom** scheda il **proprietà** scegliere AssemblyLocation, come mostrato nella figura seguente.

     ![Proprietà AssemblyLocation. ](../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation la proprietà.")

     Il **valore** casella contiene l'identificatore del manifesto di distribuzione.

4. Prima dell'identificatore immettere il percorso completo del documento seguito da una barra, nel formato *tracciato*|*identificatore* (ad esempio, *File://ServerName/ Nomecartella/FileName | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.

     Per altre informazioni su come questo identificatore di formato, vedere [Cenni preliminari sulle proprietà di documento Custom](../vsto/custom-document-properties-overview.md).

5. Scegliere il **OK** pulsante, quindi salvare e chiudere il documento.

6. Eseguire il programma di installazione senza il parametro /url per installare la soluzione nel percorso specificato.

## <a name="Roll"></a> Eseguire il rollback di una soluzione a una versione precedente
 Eseguire il rollback di una soluzione significa riportare gli utenti a una versione precedente di tale soluzione.

#### <a name="to-roll-back-a-solution"></a>Per eseguire il rollback di una soluzione

1. Aprire il percorso di installazione della soluzione.

2. Cartella di pubblicazione di primo livello, eliminare il manifesto di distribuzione (il *VSTO* file).

3. Individuare la sottocartella della versione che si desidera ripristinare.

4. Copiare il manifesto di distribuzione da tale sottocartella alla cartella di pubblicazione di primo livello.

     Ad esempio, per eseguire il rollback di una soluzione che viene chiamata **OutlookAddIn1** dalla versione 1.0.0.1 alla versione 1.0.0.0, copiare il file **OutlookAddIn1.vsto** dal **OutlookAddIn1_1_0_0_0** cartella. Incollare il file di primo livello di pubblicazione cartella, sovrascrivendo il manifesto di distribuzione specifico della versione per **OutlookAddIn1_1_0_0_1** che era già presente.

     Nell'illustrazione seguente viene mostrata la struttura della cartella di pubblicazione di questo esempio.

     ![Struttura di cartelle di pubblicazione](../vsto/media/publishfolderstructure.png "pubblicare struttura di cartelle")

     Alla successiva apertura del documento personalizzato o dell'applicazione da parte dell'utente, verrà rilevata la modifica al manifesto di distribuzione. La versione precedente della soluzione Office viene eseguita dalla cache ClickOnce.

> [!NOTE]
>  I dati locali vengono salvati soltanto per una versione precedente di una soluzione. Se si esegue il rollback di due versioni, non vengono conservati i dati locali. Per altre informazioni sui dati locali, vedere [accedere ai dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Vedere anche

- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
- [Pubblicare soluzioni Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Procedura: Distribuire una soluzione Office usando ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Procedura: Installare una soluzione ClickOnce Office](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)
- [Procedura: Pubblicare una soluzione Office a livello di documento in un server SharePoint tramite ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)
- [Creare un programma di installazione personalizzato per una soluzione office ClickOnce](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)