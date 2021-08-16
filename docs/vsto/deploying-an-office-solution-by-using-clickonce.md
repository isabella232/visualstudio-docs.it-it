---
title: Distribuire una Office di distribuzione usando ClickOnce
description: Informazioni su come distribuire la soluzione Office in meno passaggi se si usa ClickOnce. Eventuali aggiornamenti alla soluzione pubblicati vengono rilevati e installati automaticamente.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 84c3740a1fd51863c782942a12d9863d3bf448c85379f89b82268a01847f0b44
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121297048"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Distribuire una Office di distribuzione usando ClickOnce
  L'uso di ClickOnce consente di distribuire una soluzione Office in un minor numero di passaggi. Eventuali aggiornamenti alla soluzione pubblicati vengono rilevati e installati automaticamente. Tuttavia, ClickOnce richiede che la soluzione venga installata separatamente per ciascun utente di un computer. Pertanto, è consigliabile usare Windows Installer (*.msi*) se più utenti eseguiranno la soluzione nello stesso computer.

## <a name="in-this-topic"></a>Contenuto dell'argomento

- [Pubblicare la soluzione](#Publish)

- [Scegliere come si desidera concedere l'attendibilità alla soluzione](#Trust)

- [Aiutare gli utenti a installare la soluzione](#Helping)

- [Inserire il documento di una soluzione nel computer dell'utente finale (solo personalizzazioni a livello di documento)](#Put)

- [Inserire il documento di una soluzione in un server in cui è eseguito SharePoint (solo personalizzazioni a livello di documento)](#SharePoint)

- [Creare un programma di installazione personalizzato](#Custom)

- [Pubblicare un aggiornamento](#Update)

- [Modificare il percorso di installazione di una soluzione](#Location)

- [Eseguire il rollback di una soluzione a una versione precedente](#Roll)

  Per altre informazioni su come distribuire una soluzione Office creando un file del programma di installazione di Windows, vedere Distribuire una soluzione Office usando Windows [Installer.](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)

## <a name="publish-the-solution"></a><a name="Publish"></a> Pubblicare la soluzione
 È possibile pubblicare la soluzione usando la **Pubblicazione guidata o** Project **progettazione**. In questa procedura si userà progettazione Project **perché** fornisce il set completo di opzioni di pubblicazione. Vedere [Pubblicazione guidata &#40;Office sviluppo in Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>Per pubblicare la soluzione

1. In **Esplora soluzioni** scegliere il nodo denominato per il progetto.

2. Sulla barra dei menu scegliere **Project**, Proprietà **NomeProgetto**. 

3. In Progettazione **Project scegliere** la **scheda Pubblica,** illustrata nella figura seguente.

    ![Scheda Pubblica in Progettazione progetti](../vsto/media/vsto-publishtab.png "Scheda Pubblica in Progettazione progetti")

4. Nella casella Percorso cartella di pubblicazione **(server FTP** o percorso file) immettere il percorso della cartella in cui si vuole che **progettazione Project copia** i file della soluzione.

    È possibile fornire uno dei seguenti tipi di percorso.

   - Un percorso locale (ad esempio, *C:\FolderName\FolderName*).

   - Percorso UNC (Uniform Naming Convention) di una cartella nella rete, ad esempio *\\ \NomeServer\Nome FolderName*.

   - Percorso relativo, ad esempio *PublishFolder, \\* ovvero la cartella in cui il progetto viene pubblicato per impostazione predefinita.

5. Nella casella **INSTALLATION Folder URL (URL** cartella di installazione) immettere il percorso completo del percorso in cui gli utenti finali troveranno la soluzione.

    Se non si conosce ancora la località, non immettere alcun valore in questo campo. Per impostazione predefinita, quando si usa ClickOnce, gli aggiornamenti vengono cercati nella cartella da cui gli utenti installano la soluzione.

6. Scegliere il pulsante **Prerequisiti** .

7. Nella finestra **di dialogo Prerequisiti** verificare che la casella di controllo Crea programma di installazione per installare i **componenti** dei prerequisiti sia selezionata.

8. **Nell'elenco Scegliere i prerequisiti** da installare selezionare le caselle di controllo per Windows Installer **4.5** e il pacchetto .NET Framework appropriato.

    Ad esempio, se la soluzione è destinata a , selezionare le caselle di controllo per [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] **Windows Installer 4.5** e **Microsoft .NET Framework 4.5 Full.**

9. Se la soluzione è destinata .NET Framework 4.5, selezionare anche la casella di controllo **Visual Studio 2010 Tools for Office Runtime** .

    > [!NOTE]
    > Per impostazione predefinita, questa casella di controllo non viene visualizzata. Per visualizzarla, è necessario creare un pacchetto di programma di avvio automatico. Vedere Creare un pacchetto del programma di avvio automatico [per Office 2013 VSTO componente aggiuntivo con Visual Studio 2012.](create-vsto-add-ins-for-office-by-using-visual-studio.md)

10. In **Specificare il percorso di installazione per i** prerequisiti scegliere una delle opzioni visualizzate e quindi scegliere il pulsante **OK.**

     Nella tabella seguente viene descritta ciascuna opzione.

    |Opzione|Descrizione|
    |------------|-----------------|
    |**Scarica prerequisiti dal sito Web del fornitore del componente**|All'utente viene chiesto di scaricare e installare questi prerequisiti dal fornitore.|
    |**Scarica prerequisiti dallo stesso percorso dell'applicazione**|Il software prerequisito viene installato insieme alla soluzione. Se si seleziona questa opzione, tutti i pacchetti di prerequisiti vengono copiati automaticamente da Visual Studio nel percorso di pubblicazione. Per il corretto funzionamento di questa opzione, i pacchetti di prerequisiti devono essere presenti nel computer di sviluppo.|
    |**Scarica prerequisiti dal seguente percorso**|Tutti i pacchetti di prerequisiti vengono copiati da Visual Studio nella posizione specificata e vengono installati insieme alla soluzione.|

     Vedere [La finestra di dialogo Prerequisiti](../ide/reference/prerequisites-dialog-box.md).

11. Scegliere il **pulsante Aggiornamenti,** specificare la frequenza con cui si vuole che il componente aggiuntivo VSTO o la personalizzazione di ogni utente finale controlli la disponibilità di aggiornamenti e quindi scegliere **il pulsante OK.**

    > [!NOTE]
    > Se si esegue la distribuzione usando un CD o un'unità rimovibile, scegliere il pulsante di opzione Non verificare mai **la** disponibilità di aggiornamenti.

     Per informazioni su come pubblicare un aggiornamento, vedere [Pubblicare un aggiornamento.](#Update)

12. Scegliere il **pulsante** Opzioni, esaminare le opzioni nella **finestra di** dialogo Opzioni e quindi scegliere il **pulsante OK.**

13. Scegliere il **pulsante Publish Now (Pubblica** ora).

     Le cartelle e i file seguenti vengono aggiunti automaticamente da Visual Studio nella cartella di pubblicazione specificata precedentemente in questa procedura.

    - Cartella **File dell'applicazione.**

    - Programma di installazione.

    - Manifesto di distribuzione che punta al manifesto di distribuzione della versione più recente.

      La **cartella File** applicazione contiene una sottocartella per ogni versione pubblicata. Ogni sottocartella relativa a una versione specifica contiene i file indicati di seguito.

    - Un manifesto dell'applicazione.

    - Un manifesto di distribuzione.

    - Assembly di personalizzazione.

      Nell'illustrazione seguente viene mostrata la struttura della cartella di pubblicazione di un componente aggiuntivo VSTO di Outlook.

      ![Struttura di cartelle di pubblicazione](../vsto/media/publishfolderstructure.png "Struttura della cartella di pubblicazione")

    > [!NOTE]
    > ClickOnce aggiunge l'estensione *deploy* agli assembly in modo che un'installazione protetta di Internet Information Services (IIS) non blocchi i file a causa di un'estensione non sicura. Quando l'utente installa la soluzione, ClickOnce rimuove *l'estensione deploy.*

14. Copiare i file della soluzione nel percorso di installazione specificato precedentemente in questa procedura.

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a> Decidere come concedere l'attendibilità alla soluzione
 Prima che una soluzione possa essere eseguita nei computer degli utenti, è necessario concedere l'attendibilità oppure gli utenti devono rispondere a una richiesta di attendibilità quando installano la soluzione. Per concedere l'attendibilità alla soluzione, firmare i manifesti usando un certificato che identifichi un editore conosciuto e attendibile. Vedere [Considerare attendibile la soluzione firmando i manifesti dell'applicazione e della distribuzione.](../vsto/granting-trust-to-office-solutions.md#Signing)

 Se si distribuisce una personalizzazione a livello di documento e si vuole inserire il documento in una cartella nel computer dell'utente o renderlo disponibile in un sito di SharePoint, assicurarsi che Office ritieni attendibile il percorso del documento. Vedere [Concedere l'attendibilità ai documenti](../vsto/granting-trust-to-documents.md).

## <a name="help-users-install-the-solution"></a><a name="Helping"></a> Aiutare gli utenti a installare la soluzione
 Gli utenti possono installare la soluzione eseguendo il programma di installazione, aprendo il manifesto della distribuzione o durante la personalizzazione a livello di documento, aprendo direttamente il documento. Come procedura consigliata, gli utenti devono installare la soluzione usando il programma di installazione. Gli altri due approcci non garantiscono l'installazione del software prerequisito. Se gli utenti desiderano aprire il documento dal percorso di installazione, devono aggiungerlo all'elenco dei percorsi attendibili nel Centro protezione dell'applicazione di Office.

### <a name="opening-the-document-of-a-document-level-customization"></a>Apertura del documento di una personalizzazione a livello di documento
 Gli utenti possono aprire il documento di una personalizzazione a livello di documento direttamente dal percorso di installazione oppure copiando il documento nei propri computer locali e aprendo quindi la copia.

 Come procedura consigliata, gli utenti devono aprire una copia del documento nei computer locali per evitare che più utenti tentino di aprire la stessa copia contemporaneamente. Per applicare questo approccio, è possibile configurare il programma di installazione in modo da copiare il documento nei computer degli utenti. Vedere [Inserire il documento di una soluzione nel computer dell'utente finale (solo personalizzazioni a livello di documento).](#Put)

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Installare la soluzione aprendo il manifesto della distribuzione da un sito Web IIS
 Gli utenti possono installare una soluzione Office aprendo il manifesto di distribuzione dal Web. Tuttavia, un'installazione protetta di Internet Information Services (IIS) blocca i file con estensione *vsto.* Il tipo MIME deve essere definito in IIS prima di poter distribuire una soluzione Office tramite IIS.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Per aggiungere il tipo MIME .vsto a IIS 6.0

1. Nel server che esegue IIS 6.0 scegliere Avvia tutti i programmi Strumenti di  >    >    >   **amministrazione Internet Information Services (IIS)**.

2. Scegliere il nome del computer, **la cartella Siti Web** o il sito Web che si sta configurando.

3. Sulla barra dei menu scegliere **Proprietà**  >  **azione.**

4. Nella scheda **Intestazioni HTTP** scegliere il pulsante **Tipi MIME.**

5. Nella finestra **Tipi MIME** scegliere il **pulsante** Nuovo.

6. Nella finestra **Tipo MIME** immettere **.vsto** come estensione, immettere **application/x-ms-vsto** come tipo MIME e quindi applicare le nuove impostazioni.

    > [!NOTE]
    > Per rendere effettive le modifiche è necessario riavviare il servizio Pubblicazione sul Web o attendere il riciclo del processo di lavoro. È quindi necessario scaricare la cache del disco del browser e quindi provare ad aprire di nuovo il file *vsto.*

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Per aggiungere il tipo MIME .vsto a IIS 7.0

1. Nel server che esegue IIS 7.0 scegliere **Avvia**  >  **tutti i programmi**  >  **Accessori**.

2. Aprire il menu di scelta rapida **per Prompt dei comandi** e quindi scegliere Esegui come  **amministratore.**

3. Nella casella **Apri** immettere il percorso seguente e quindi scegliere **OK.**

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Immettere il seguente comando, quindi applicare le nuove impostazioni.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > Per rendere effettive le modifiche è necessario riavviare il servizio Pubblicazione sul Web o attendere il riciclo del processo di lavoro. È quindi necessario scaricare la cache del disco del browser e quindi provare ad aprire di nuovo il file *vsto.*

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a> Inserire il documento di una soluzione nel computer dell'utente finale (solo personalizzazioni a livello di documento)
 È possibile copiare il documento della soluzione nel computer dell'utente finale creando un'azione post-distribuzione. In questo modo, l'utente non deve copiare manualmente il documento dal percorso di installazione al computer dopo aver installato la soluzione. Sarà necessario creare una classe che definisce l'azione post-distribuzione, compilare e pubblicare la soluzione, modificare il manifesto dell'applicazione e firmare nuovamente l'applicazione e il manifesto della distribuzione.

 Le procedure seguenti presuppongono che il nome del progetto sia **ExcelWorkbook** e che la soluzione sia pubblicata in una cartella creata **denominata C:\publish** nel computer.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Creare una classe che definisca l'azione post-distribuzione

1. Sulla barra dei menu scegliere **File**  >  **Aggiungi**  >  **nuovo Project**.

2. Nel riquadro **Modelli installati Project** finestra di  dialogo Aggiungi nuovo Windows **cartella.**

3. Nel riquadro **Modelli** scegliere il **modello Libreria di** classi.

4. Nel campo **Nome** immettere **FileCopyPDA** e quindi scegliere **OK.**

5. In **Esplora soluzioni** scegliere il **progetto FileCopyPDA.**

6. Sulla barra dei menu scegliere **Project**  >  **Aggiungi riferimento**.

7. Nella scheda **.NET** aggiungere riferimenti a `Microsoft.VisualStudio.Tools.Applications.Runtime` e `Microsoft.VisualStudio.Tools.Applications.ServerDocument` .

8. Rinominare la classe in `FileCopyPDA`, quindi sostituire il contenuto del file con il codice. Il codice esegue queste operazioni:

   - Copia del documento sul desktop dell'utente.

   - Modifica la _AssemblyLocation da un percorso relativo a un percorso completo per il manifesto della distribuzione.

   - Eliminazione del file se l'utente disinstalla la soluzione.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs" id="Snippet7":::

### <a name="build-and-publish-the-solution"></a>Compilare e pubblicare la soluzione

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto FileCopyPDA** e quindi scegliere **Compila**.

2. Aprire il menu di scelta rapida per **il progetto ExcelWorkbook** e quindi scegliere **Compila**.

3. Aprire il menu di scelta rapida per **il progetto ExcelWorkbook** e quindi scegliere **Aggiungi riferimento**.

4. Nella finestra **di dialogo** Aggiungi riferimento scegliere la **scheda Progetti** , scegliere **FileCopyPDA** e quindi fare clic sul **pulsante OK.**

5. In **Esplora soluzioni** scegliere il **progetto ExcelWorkbook.**

6. Sulla barra dei menu scegliere **Project**  >  **Nuova cartella**.

7. Immettere **Dati** e quindi premere **INVIO.**

8. In **Esplora soluzioni** scegliere la **cartella** Dati.

9. Sulla barra dei menu scegliere **Project**  >  **Aggiungi elemento esistente**.

10. Nella finestra **di dialogo Aggiungi elemento** esistente passare alla directory di output per il progetto **ExcelWorkbook,** scegliere il file **ExcelWorkbook.xlsx** e quindi scegliere il **pulsante** Aggiungi.

11. In **Esplora soluzioni** scegliere il file **ExcelWorkbook.xlsx** file.

12. Nella finestra **Proprietà** impostare la proprietà Azione **di** compilazione su **Contenuto** e la proprietà Copia nella directory **di output** su Copia se **più recente.**

     Dopo aver completato questi passaggi, il progetto sarà simile alla figura seguente.

     ![Struttura progetto dell'azione post-distribuzione.](../vsto/media/vsto-postdeployment.png "Struttura progetto dell'azione post-distribuzione.")

13. Pubblicare **il progetto ExcelWorkbook.**

### <a name="modify-the-application-manifest"></a>Modificare il manifesto dell'applicazione

1. Aprire la directory della soluzione, **c:\publish**, **usando** Esplora file .

2. Aprire la **cartella File** dell'applicazione e quindi la cartella corrispondente alla versione pubblicata più recente della soluzione.

3. Aprire il **fileExcelWorkbook.dll.manifest** in un editor di testo, ad esempio Blocco note.

4. Dopo l'elemento `</vstav3:update>` aggiungere il codice seguente. Per l'attributo class `<vstav3:entryPoint>` dell'elemento usare la sintassi seguente: *NamespaceName.ClassName*. Nell'esempio riportato di seguito il nome dello spazio dei nomi è uguale a quello della classe. Pertanto, il nome del punto di ingresso risultante è `FileCopyPDA.FileCopyPDA`.

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

1. Nella cartella **%USERPROFILE%\Documents\Visual Studio 2013\Projects\ExcelWorkbook\ExcelWorkbook** copiare il file di certificato **ExcelWorkbook_TemporaryKey.pfx** e incollarlo nella cartella *PublishFolder* **\Application Files\ExcelWorkbook** \_ _MostRecentPublishedVersion._

2. Aprire il prompt dei comandi Visual Studio e quindi passare alla cartella **c:\publish\Application Files\ExcelWorkbook** \_ _MostRecentPublishedVersion_ ( ad **esempio, c:\publish\Application Files\ExcelWorkbook_1_0_0_4**).

3. Firmare il manifesto dell'applicazione modificato usando il comando seguente:

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     Verrà visualizzato il messaggio "ExcelWorkbook.dll.manifest firmato correttamente".

4. Passare alla cartella **c:\publish** e quindi aggiornare e firmare il manifesto della distribuzione eseguendo il comando seguente:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > Nell'esempio precedente sostituire MostRecentVersionNumber con il numero di versione dell'ultima versione pubblicata della soluzione , ad esempio **1_0_0_4**.

     Verrà visualizzato il messaggio "ExcelWorkbook.vsto firmato correttamente".

5. Copiare il file *ExcelWorkbook.vsto* nella directory **c:\publish\Application Files\ExcelWorkbook** \_ _MostRecentVersionNumber._

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a>Inserire il documento di una soluzione in un server che esegue SharePoint (solo personalizzazioni a livello di documento)
 È possibile pubblicare la personalizzazione a livello di documento agli utenti finali tramite SharePoint. Quando gli utenti visitano il sito di SharePoint e aprono il documento, la soluzione viene automaticamente installata dalla cartella di rete condivisa nei computer locali degli utenti. Una volta che la soluzione è installata localmente, la personalizzazione continuerà a essere valida anche se il documento viene copiato in un'altra posizione, ad esempio sul desktop.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Per inserire il documento in un server in cui è eseguito SharePoint

1. Aggiungere il documento della soluzione a una raccolta documenti su un sito di SharePoint.

2. Effettuare i passaggi per uno degli approcci indicati di seguito:

    - Usare lo strumento di configurazione di Office per aggiungere il server in cui è eseguito SharePoint al Centro protezione in Word o Excel in tutti i computer degli utenti.

         Vedere [Criteri di sicurezza e impostazioni in Office 2010.](/previous-versions/office/office-2010/cc178946(v=office.14))

    - Assicurarsi che ogni utente esegua i passaggi indicati di seguito.

        1. Nel computer locale aprire Word o Excel, scegliere la **scheda File** e quindi scegliere il **pulsante** Opzioni.

        2. Nella finestra **di dialogo Centro** protezione scegliere il pulsante **Percorsi** attendibili .

        3. Selezionare la casella di controllo Consenti percorsi attendibili in rete (scelta non **consigliata)** e quindi scegliere il **pulsante Aggiungi nuovo** percorso.

        4. Nella casella **Percorso** immettere l'URL della raccolta documenti SharePoint che contiene il documento caricato, ad esempio *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName* .

             Non aggiungere il nome della pagina Web predefinita, ad esempio *default.aspx* o *AllItems.aspx.*

        5. Selezionare la casella di controllo Anche le **sottocartelle** di questo percorso sono attendibili e quindi scegliere **OK.**

             Nel momento in cui gli utenti aprono il documento dal sito di SharePoint, il documento viene aperto e la personalizzazione viene installata. Gli utenti possono copiare il documento sul proprio desktop. L'esecuzione della personalizzazione continuerà perché le proprietà nel documento puntano al percorso di rete del documento.

## <a name="create-a-custom-installer"></a><a name="Custom"></a> Creare un programma di installazione personalizzato
 È possibile creare un programma di installazione personalizzato per la soluzione Office, anziché usare il programma di installazione creato automaticamente quando si pubblica la soluzione. È ad esempio possibile usare uno script di accesso per avviare l'installazione oppure un file batch per installare la soluzione senza interazione dell'utente. Questi scenari offrono i risultati migliori se i prerequisiti sono già installati nei computer degli utenti finali.

 Come parte del processo di installazione personalizzato, chiamare lo strumento di installazione per le soluzioni Office (*VSTOInstaller.exe*), che viene installato nel percorso seguente per impostazione predefinita:

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Se lo strumento non si trova in  tale percorso, è possibile usare la chiaveHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPatho **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4\InstallerPath** del Registro di sistema per trovare il percorso di tale strumento.

 È possibile usare i parametri seguenti con *VSTOinstaller.exe*.

| Parametro | Definizione |
|------------------| - |
| /Install o /I | Installa la soluzione. È necessario seguire questa opzione con il percorso di un manifesto di distribuzione. È possibile specificare un percorso sul computer locale o di una condivisione file UNC (Universal Naming Convention). È possibile specificare un percorso locale (*C:\FolderName\PublishFolder*), un percorso relativo (*Publish \\*) o un percorso completo (*\\ \ServerName\FolderName* o http://<em>ServerName/FolderName</em>). |
| /Uninstall o /U | Disinstalla la soluzione. È necessario seguire questa opzione con il percorso di un manifesto di distribuzione. È possibile specificare che un percorso che può essere nel computer locale o in una condivisione file UNC. È possibile specificare un percorso locale (*c:\FolderName\PublishFolder*), un percorso relativo (*Publish \\*) o un percorso completo (*\\ \ServerName\FolderName* o http://<em>ServerName/FolderName</em>). |
| /Silent o /S | Installa o disinstalla senza richiedere input da parte dell'utente o visualizzare un messaggio. Se è necessaria una richiesta di attendibilità, la personalizzazione non viene installata o aggiornata. |
| /Help o /? | Visualizza le informazioni della Guida. |

 Quando si esegue *VSTOinstaller.exe*, potrebbero essere visualizzati i codici di errore seguenti.

|Codice di errore|Definizione|
|----------------|----------------|
|0|La soluzione è stata installata o disinstallata correttamente oppure è stata visualizzata la Guida di VSTOInstaller.|
|-100|Una o più opzioni della riga di comando non sono valide o sono impostate più volte. Per altre informazioni, immettere "vstoinstaller /?" o vedere [Creare un programma di installazione personalizzato per una ClickOnce Office personalizzata.](/previous-versions/bb772078(v=vs.110))|
|-101|Una o più opzioni della riga di comando non sono valide. Per altre informazioni, immettere "vstoinstaller /?".|
|-200|L'URI del manifesto della distribuzione non è valido. Per altre informazioni, immettere "vstoinstaller /?".|
|-201|Non è stato possibile installare la soluzione perché il manifesto della distribuzione non è valido. Vedere [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md).|
|-202|Non è stato possibile installare la soluzione perché Visual Studio Tools per Office sezione del manifesto dell'applicazione non è valida. Vedere [Manifesti dell'applicazione per Office soluzioni .](../vsto/application-manifests-for-office-solutions.md)|
|-203|Non è stato possibile installare la soluzione perché si è verificato un errore di download. Controllare l'URI o il percorso del file di rete del manifesto di distribuzione, quindi provare di nuovo.|
|-300|Non è stato possibile installare la soluzione perché si è verificata un'eccezione di sicurezza. Vedere [Soluzioni Office sicurezza](../vsto/securing-office-solutions.md).|
|-400|Non è stato possibile installare la soluzione.|
|-401|Non è stato possibile disinstallare la soluzione.|
|-500|L'operazione è stata annullata perché non è stato possibile installare o disinstallare la soluzione o scaricare il manifesto di distribuzione.|

## <a name="publish-an-update"></a><a name="Update"></a> Pubblicare un aggiornamento
 Per aggiornare una soluzione, pubblicarla di nuovo usando **Project Designer** o **la Pubblicazione** guidata e quindi copiare la soluzione aggiornata nel percorso di installazione. Quando si copiano i file nel percorso di installazione, assicurarsi di sovrascrivere i file precedenti.

 La volta successiva che la soluzione verifica la presenza di un aggiornamento, trova e carica automaticamente la nuova versione.

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a> Modificare il percorso di installazione di una soluzione
 È possibile aggiungere o modificare il percorso di installazione dopo la pubblicazione di una soluzione. È possibile che si desideri modificare il percorso di installazione per uno o più dei motivi seguenti:

- Il percorso di installazione non era noto quando il programma di installazione è stato compilato.

- I file della soluzione sono stati copiati in un percorso diverso.

- Il server che ospita i file di installazione ha un nome o un percorso nuovo.

  Per modificare il percorso di installazione di una soluzione, è necessario aggiornare il programma di installazione e successivamente gli utenti devono eseguirlo. Per le personalizzazioni a livello di documento, gli utenti devono aggiornare anche una proprietà nel proprio documento in modo che punti al nuovo percorso.

> [!NOTE]
> Se non si vuole chiedere agli utenti di aggiornare le proprietà del documento, è possibile chiedere agli utenti di ottenere il documento aggiornato dal percorso di installazione.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Per modificare il percorso di installazione nel programma di installazione

1. Aprire una **finestra del prompt** dei comandi e quindi passare alla cartella di installazione.

2. Eseguire il programma di installazione e includere il parametro `/url`, che assumerà come stringa il nuovo percorso di installazione.

    Nell'esempio seguente viene illustrato come modificare il percorso di installazione in un percorso sul sito Web di Fabrikam, ma è possibile sostituire tale URL con il percorso desiderato:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Se viene visualizzato un messaggio per segnalare che la firma dell'eseguibile sarà invalidata, il certificato usato per firmare la soluzione non è più valido e l'editore è sconosciuto. Di conseguenza, gli utenti dovranno confermare l'attendibilità dell'origine della soluzione prima di poterla installare.

   > [!NOTE]
   > Per visualizzare il valore corrente dell'URL, eseguire `setup.exe /url`.

   Per le personalizzazioni a livello di documento, gli utenti devono aprire il documento e quindi aggiornarne _AssemblyLocation proprietà . Di seguito viene descritta la procedura che gli utenti devono seguire per eseguire questa attività.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>Per aggiornare la proprietà _AssemblyLocation in un documento

1. Nella scheda **File** scegliere **Informazioni**, come illustrato nella figura seguente.

     ![Scheda Informazioni in Excel](../vsto/media/vsto-infotab.png "Scheda Informazioni in Excel")

2. **Nell'elenco** Proprietà scegliere **Proprietà avanzate**, come illustrato nella figura seguente.

     ![Proprietà avanzate in Excel.](../vsto/media/vsto-advanceddocumentproperties.png "Proprietà avanzate in Excel.")

3. Nella scheda **Personalizzato** **dell'elenco Proprietà** scegliere _AssemblyLocation, come illustrato nella figura seguente.

     ![Proprietà AssemblyLocation.](../vsto/media/vsto-assemblylocationproperty.png "Proprietà AssemblyLocation.")

     La **casella Valore** contiene l'identificatore del manifesto della distribuzione.

4. Prima dell'identificatore, immettere il percorso completo del documento, seguito da una barra, nel formato Identificatore percorso |  ( *ad esempio, File://ServerName/FolderName/FileName|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.

     Per altre informazioni su come formattare questo identificatore, vedere Panoramica [delle proprietà dei documenti personalizzati.](../vsto/custom-document-properties-overview.md)

5. Scegliere il **pulsante OK** e quindi salvare e chiudere il documento.

6. Eseguire il programma di installazione senza il parametro /url per installare la soluzione nel percorso specificato.

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a> Eseguire il rollback di una soluzione a una versione precedente
 Eseguire il rollback di una soluzione significa riportare gli utenti a una versione precedente di tale soluzione.

#### <a name="to-roll-back-a-solution"></a>Per eseguire il rollback di una soluzione

1. Aprire il percorso di installazione della soluzione.

2. Nella cartella di pubblicazione di primo livello eliminare il manifesto della distribuzione (file *con estensione vsto).*

3. Individuare la sottocartella della versione che si desidera ripristinare.

4. Copiare il manifesto di distribuzione da tale sottocartella alla cartella di pubblicazione di primo livello.

     Ad esempio, per eseguire il rollback di una soluzione denominata **OutlookAddIn1** dalla versione 1.0.0.1 alla versione 1.0.0.0, copiare il file **OutlookAddIn1.vsto** dalla **cartella OutlookAddIn1_1_0_0_0.** Incollare il file nella cartella di pubblicazione di primo livello, sovrascrivendo il manifesto di distribuzione specifico **della versione** per OutlookAddIn1_1_0_0_1 che era già presente.

     Nell'illustrazione seguente viene mostrata la struttura della cartella di pubblicazione di questo esempio.

     ![Struttura di cartelle di pubblicazione](../vsto/media/publishfolderstructure.png "Struttura della cartella di pubblicazione")

     Alla successiva apertura del documento personalizzato o dell'applicazione da parte dell'utente, verrà rilevata la modifica al manifesto di distribuzione. La versione precedente della soluzione Office viene eseguita dalla cache ClickOnce.

> [!NOTE]
> I dati locali vengono salvati soltanto per una versione precedente di una soluzione. Se si esegue il rollback di due versioni, i dati locali non vengono mantenuti. Per altre informazioni sui dati locali, vedere [Accedere a dati locali e](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)remoti in ClickOnce applicazioni .

## <a name="see-also"></a>Vedi anche

- [Distribuire una Office distribuzione](../vsto/deploying-an-office-solution.md)
- [Pubblicare Office soluzioni](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Procedura: Pubblicare una soluzione Office usando ClickOnce](/previous-versions/bb386095(v=vs.110))
- [Procedura: Installare una soluzione ClickOnce Office personalizzata](/previous-versions/bb608592(v=vs.110))
- [Procedura: Pubblicare una soluzione di Office a livello di documento in un server SharePoint usando ClickOnce](/previous-versions/bb608595(v=vs.110))
- [Creare un programma di installazione personalizzato per una ClickOnce office](/previous-versions/bb772078(v=vs.110))