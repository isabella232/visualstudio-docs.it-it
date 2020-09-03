---
title: Distribuire una soluzione Office tramite ClickOnce
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
ms.openlocfilehash: f4adbd08d13d26c717beeb454bd323185bb88640
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "79416562"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Distribuire una soluzione Office tramite ClickOnce
  L'uso di ClickOnce consente di distribuire una soluzione Office in un minor numero di passaggi. Eventuali aggiornamenti alla soluzione pubblicati vengono rilevati e installati automaticamente. Tuttavia, ClickOnce richiede che la soluzione venga installata separatamente per ciascun utente di un computer. Pertanto, è consigliabile utilizzare Windows Installer (*MSI*) se più utenti eseguiranno la soluzione nello stesso computer.

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

  Per altre informazioni su come distribuire una soluzione Office creando un file di Windows Installer, vedere [distribuire una soluzione Office usando Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="publish-the-solution"></a><a name="Publish"></a> Pubblicare la soluzione
 È possibile pubblicare la soluzione tramite la **pubblicazione guidata** o **Progettazione progetti**. In questa procedura verrà utilizzato **Progettazione progetti** perché fornisce il set completo di opzioni di pubblicazione. Vedere [pubblicazione guidata &#40;sviluppo per Office in Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>Per pubblicare la soluzione

1. In **Esplora soluzioni**scegliere il nodo denominato per il progetto.

2. Sulla barra dei menu scegliere **Progetto**, *Proprietà* **NomeProgetto**.

3. In creazione **progetti**scegliere la scheda **pubblica** , illustrata nella figura seguente.

    ![Scheda Pubblica in Progettazione progetti](../vsto/media/vsto-publishtab.png "Scheda Pubblica in Progettazione progetti")

4. Nella casella percorso **cartella di pubblicazione (server FTP o percorso file)** immettere il percorso della cartella in cui si desidera che la **finestra di progettazione progetti** copi i file della soluzione.

    È possibile fornire uno dei seguenti tipi di percorso.

   - Un percorso locale, ad esempio *c:\Nomecartella\Nomecartella*.

   - Un percorso UNC (Uniform Naming Convention) di una cartella della rete (ad esempio, * \\ \ServerName\FolderName*).

   - Un percorso relativo (ad esempio, *cartellapubblicazione \\ *, che è la cartella in cui il progetto viene pubblicato per impostazione predefinita).

5. Nella casella **URL cartella di installazione** immettere il percorso completo della posizione in cui gli utenti finali troveranno la soluzione.

    Se non si conosce ancora il percorso, non immettere nulla in questo campo. Per impostazione predefinita, quando si usa ClickOnce, gli aggiornamenti vengono cercati nella cartella da cui gli utenti installano la soluzione.

6. Scegliere il pulsante **Prerequisiti** .

7. Nella finestra di dialogo **prerequisiti** verificare che la casella di controllo **Crea programma di installazione per installare componenti dei prerequisiti** sia selezionata.

8. Nell'elenco **scegliere i prerequisiti da installare** selezionare le caselle di controllo per **Windows Installer 4,5** e il pacchetto di .NET Framework appropriato.

    Ad esempio, se la soluzione è destinata a [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , selezionare le caselle di controllo per **Windows Installer 4,5** e **Microsoft .NET Framework 4,5 Full**.

9. Se la soluzione è destinata al .NET Framework 4,5, selezionare anche la casella di controllo **Visual Studio 2010 Tools per Office Runtime** .

    > [!NOTE]
    > Per impostazione predefinita, questa casella di controllo non viene visualizzata. Per visualizzarla, è necessario creare un pacchetto di programma di avvio automatico. Vedere [creare un pacchetto del programma di avvio automatico per un componente aggiuntivo VSTO di Office 2013 con Visual Studio 2012](create-vsto-add-ins-for-office-by-using-visual-studio.md).

10. In **specificare il percorso di installazione dei prerequisiti**scegliere una delle opzioni visualizzate, quindi scegliere il pulsante **OK** .

     Nella tabella seguente viene descritta ciascuna opzione.

    |Opzione|Descrizione|
    |------------|-----------------|
    |**Scarica prerequisiti dal sito Web del fornitore del componente**|All'utente viene chiesto di scaricare e installare questi prerequisiti dal fornitore.|
    |**Scarica prerequisiti dallo stesso percorso dell'applicazione**|Il software prerequisito viene installato insieme alla soluzione. Se si seleziona questa opzione, tutti i pacchetti di prerequisiti vengono copiati automaticamente da Visual Studio nel percorso di pubblicazione. Per il corretto funzionamento di questa opzione, i pacchetti di prerequisiti devono essere presenti nel computer di sviluppo.|
    |**Scarica prerequisiti dal seguente percorso**|Tutti i pacchetti di prerequisiti vengono copiati da Visual Studio nella posizione specificata e vengono installati insieme alla soluzione.|

     Vedere la finestra di [dialogo Prerequisiti](../ide/reference/prerequisites-dialog-box.md).

11. Scegliere il pulsante **aggiornamenti** , specificare la frequenza con cui si desidera che il componente aggiuntivo VSTO o la personalizzazione di ogni utente finale verifichi la disponibilità di aggiornamenti, quindi scegliere il pulsante **OK** .

    > [!NOTE]
    > Se si esegue la distribuzione usando un CD o un'unità rimovibile, scegliere il pulsante **di opzione non verificare mai gli aggiornamenti** .

     Per informazioni su come pubblicare un aggiornamento, vedere [pubblicare un aggiornamento](#Update).

12. Scegliere il pulsante **Opzioni** , rivedere le opzioni nella finestra di dialogo **Opzioni** , quindi scegliere il pulsante **OK** .

13. Scegliere il pulsante **pubblica ora** .

     Le cartelle e i file seguenti vengono aggiunti automaticamente da Visual Studio nella cartella di pubblicazione specificata precedentemente in questa procedura.

    - Cartella dei **file dell'applicazione** .

    - Programma di installazione.

    - Manifesto di distribuzione che punta al manifesto di distribuzione della versione più recente.

      La cartella **file applicazione** contiene una sottocartella per ogni versione pubblicata. Ogni sottocartella relativa a una versione specifica contiene i file indicati di seguito.

    - Un manifesto dell'applicazione.

    - Un manifesto di distribuzione.

    - Assembly di personalizzazione.

      Nell'illustrazione seguente viene mostrata la struttura della cartella di pubblicazione di un componente aggiuntivo VSTO di Outlook.

      ![Struttura della cartella di pubblicazione](../vsto/media/publishfolderstructure.png "Struttura della cartella di pubblicazione")

    > [!NOTE]
    > ClickOnce aggiunge l'estensione *. deploy* agli assembly in modo che un'installazione protetta di Internet Information Services (IIS) non blocchi i file a causa di un'estensione unsafe. Quando l'utente installa la soluzione, ClickOnce rimuove l'estensione *. deploy* .

14. Copiare i file della soluzione nel percorso di installazione specificato precedentemente in questa procedura.

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a> Decidere come si desidera concedere l'attendibilità alla soluzione
 Prima che una soluzione possa essere eseguita nei computer degli utenti, è necessario concedere l'attendibilità oppure gli utenti devono rispondere a una richiesta di attendibilità quando installano la soluzione. Per concedere l'attendibilità alla soluzione, firmare i manifesti usando un certificato che identifichi un editore conosciuto e attendibile. [Per informazioni sull'attendibilità della soluzione, firmare i manifesti dell'applicazione e della distribuzione](../vsto/granting-trust-to-office-solutions.md#Signing).

 Se si distribuisce una personalizzazione a livello di documento e si vuole inserire il documento in una cartella nel computer dell'utente o rendere disponibile il documento in un sito di SharePoint, assicurarsi che Office consideri attendibile il percorso del documento. Vedere [concedere l'attendibilità ai documenti](../vsto/granting-trust-to-documents.md).

## <a name="help-users-install-the-solution"></a><a name="Helping"></a> Aiutare gli utenti a installare la soluzione
 Gli utenti possono installare la soluzione eseguendo il programma di installazione, aprendo il manifesto della distribuzione o durante la personalizzazione a livello di documento, aprendo direttamente il documento. Come procedura consigliata, gli utenti devono installare la soluzione usando il programma di installazione. Gli altri due approcci non assicurano che i prerequisiti software siano installati. Se gli utenti desiderano aprire il documento dal percorso di installazione, devono aggiungerlo all'elenco dei percorsi attendibili nel Centro protezione dell'applicazione di Office.

### <a name="opening-the-document-of-a-document-level-customization"></a>Apertura del documento di una personalizzazione a livello di documento
 Gli utenti possono aprire il documento di una personalizzazione a livello di documento direttamente dal percorso di installazione oppure copiando il documento nei propri computer locali e aprendo quindi la copia.

 Come procedura consigliata, gli utenti devono aprire una copia del documento nei computer locali per evitare che più utenti tentino di aprire la stessa copia contemporaneamente. Per applicare questo approccio, è possibile configurare il programma di installazione in modo da copiare il documento nei computer degli utenti. Vedere [inserire il documento di una soluzione nel computer dell'utente finale (solo personalizzazioni a livello di documento)](#Put).

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Installare la soluzione aprendo il manifesto di distribuzione da un sito Web IIS
 Gli utenti possono installare una soluzione Office aprendo il manifesto di distribuzione dal Web. Tuttavia, un'installazione protetta di Internet Information Services (IIS) bloccherà i file con estensione *VSTO* . Il tipo MIME deve essere definito in IIS prima di poter distribuire una soluzione Office tramite IIS.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Per aggiungere il tipo MIME .vsto a IIS 6.0

1. Nel server in cui è in esecuzione IIS 6,0, scegliere **Avvia**  >  **tutti i programmi**  >  gestione**strumenti di amministrazione**  >   **Internet Information Services (IIS)**.

2. Scegliere il nome del computer, la cartella **siti Web** o il sito Web che si sta configurando.

3. Sulla barra dei menu scegliere proprietà **azione**  >  **Properties**.

4. Nella scheda **intestazioni HTTP** scegliere il pulsante **tipi MIME** .

5. Nella finestra **tipi MIME** scegliere il pulsante **nuovo** .

6. Nella finestra **tipo MIME** immettere **. VSTO** come estensione, immettere **Application/x-ms-vsto** come tipo MIME, quindi applicare le nuove impostazioni.

    > [!NOTE]
    > Per rendere effettive le modifiche è necessario riavviare il servizio Pubblicazione sul Web o attendere il riciclo del processo di lavoro. È quindi necessario svuotare la cache del disco del browser e provare nuovamente ad aprire il file con *estensione VSTO* .

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Per aggiungere il tipo MIME .vsto a IIS 7.0

1. Sul server che esegue IIS 7,0, scegliere **Avvia**  >  **tutti i programmi**  >  **Accessori**.

2. Aprire il menu di scelta rapida per **prompt dei comandi**, quindi scegliere  **Esegui come amministratore.**

3. Nella casella **Apri** immettere il percorso seguente e quindi scegliere il pulsante **OK** .

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Immettere il seguente comando, quindi applicare le nuove impostazioni.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > Per rendere effettive le modifiche è necessario riavviare il servizio Pubblicazione sul Web o attendere il riciclo del processo di lavoro. È quindi necessario svuotare la cache del disco del browser e provare nuovamente ad aprire il file con *estensione VSTO* .

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a> Inserire il documento di una soluzione nel computer dell'utente finale (solo personalizzazioni a livello di documento)
 È possibile copiare il documento della soluzione nel computer dell'utente finale creando un'azione post-distribuzione. In questo modo, l'utente non deve copiare manualmente il documento dal percorso di installazione nel computer dopo aver installato la soluzione. È necessario creare una classe che definisca l'azione post-distribuzione, compilare e pubblicare la soluzione, modificare il manifesto dell'applicazione e firmare nuovamente l'applicazione e il manifesto di distribuzione.

 Nelle procedure riportate di seguito si presuppone che il nome del progetto sia **ExcelWorkbook** e che la soluzione venga pubblicata in una cartella creata denominata **C:\publish** nel computer.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Creare una classe che definisca l'azione post-distribuzione

1. Sulla barra dei menu scegliere **file**  >  **Aggiungi**  >  **nuovo progetto**.

2. Nel riquadro **modelli installati** della finestra di dialogo **Aggiungi nuovo progetto** scegliere la cartella **Windows** .

3. Nel riquadro **modelli** scegliere il modello **libreria di classi** .

4. Nel campo **nome** immettere **FileCopyPDA**, quindi scegliere il pulsante **OK** .

5. In **Esplora soluzioni**scegliere il progetto **FileCopyPDA** .

6. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi riferimento**.

7. Nella scheda **.NET** aggiungere riferimenti a `Microsoft.VisualStudio.Tools.Applications.Runtime` e `Microsoft.VisualStudio.Tools.Applications.ServerDocument` .

8. Rinominare la classe in `FileCopyPDA`, quindi sostituire il contenuto del file con il codice. Il codice esegue queste operazioni:

   - Copia del documento sul desktop dell'utente.

   - Modifica la proprietà _AssemblyLocation da un percorso relativo in un percorso completo per il manifesto della distribuzione.

   - Eliminazione del file se l'utente disinstalla la soluzione.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>Compilare e pubblicare la soluzione

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **FileCopyPDA** , quindi scegliere **Compila**.

2. Aprire il menu di scelta rapida per il progetto **ExcelWorkbook** , quindi scegliere **Compila**.

3. Aprire il menu di scelta rapida per il progetto **ExcelWorkbook** , quindi scegliere **Aggiungi riferimento**.

4. Nella finestra di dialogo **Aggiungi riferimento** scegliere la scheda **progetti** , scegliere **FileCopyPDA**, quindi scegliere il pulsante **OK** .

5. In **Esplora soluzioni**scegliere il progetto **ExcelWorkbook** .

6. Sulla barra dei menu scegliere **progetto**  >  **nuova cartella**.

7. Immettere i **dati**, quindi premere il tasto **invio** .

8. In **Esplora soluzioni**scegliere la cartella **dati** .

9. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi elemento esistente**.

10. Nella finestra di dialogo **Aggiungi elemento esistente** individuare la directory di output per il progetto **ExcelWorkbook** , scegliere il file **ExcelWorkbook.xlsx** , quindi scegliere il pulsante **Aggiungi** .

11. In **Esplora soluzioni** scegliere il file di **ExcelWorkbook.xlsx** .

12. Nella finestra **Proprietà** impostare la proprietà **azione di compilazione** su **contenuto** e la proprietà **copia in directory di output** su **copia se più recente**.

     Una volta completati questi passaggi, il progetto sarà simile a quello illustrato nella figura seguente.

     ![Struttura progetto dell'azione post-distribuzione.](../vsto/media/vsto-postdeployment.png "Struttura progetto dell'azione post-distribuzione.")

13. Pubblicare il progetto **ExcelWorkbook** .

### <a name="modify-the-application-manifest"></a>Modificare il manifesto dell'applicazione

1. Aprire la directory della soluzione, **c:\publish**, usando **Esplora file**.

2. Aprire la cartella **file applicazione** , quindi aprire la cartella che corrisponde alla versione pubblicata più recente della soluzione.

3. Aprire il file **ExcelWorkbook.dll. manifest** in un editor di testo, ad esempio Blocco note.

4. Dopo l'elemento `</vstav3:update>` aggiungere il codice seguente. Per l'attributo Class dell' `<vstav3:entryPoint>` elemento, usare la sintassi seguente: *NamespaceName. NomeClasse*. Nell'esempio riportato di seguito il nome dello spazio dei nomi è uguale a quello della classe. Pertanto, il nome del punto di ingresso risultante è `FileCopyPDA.FileCopyPDA`.

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

1. Nella cartella **%USERPROFILE%\Documents\Visual Studio 2013 \ Projects\ExcelWorkbook\ExcelWorkbook** copiare il file di certificato **ExcelWorkbook_TemporaryKey. pfx** , quindi incollarlo nella cartella *cartellapubblicazione* **\Dati Files\ExcelWorkbook** \_ _MostRecentPublishedVersion_

2. Aprire il prompt dei comandi di Visual Studio e passare alla cartella **c:\publish\Application Files\ExcelWorkbook** \_ _MostRecentPublishedVersion_ , ad esempio **c:\publish\Application Files \ ExcelWorkbook_1_0_0_4**.

3. Firmare il manifesto dell'applicazione modificato usando il comando seguente:

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     Verrà visualizzato il messaggio "ExcelWorkbook.dll.manifest firmato correttamente".

4. Passare alla cartella **c:\publish** , quindi aggiornare e firmare il manifesto di distribuzione eseguendo il comando seguente:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > Nell'esempio precedente, sostituire MostRecentVersionNumber con il numero di versione della versione pubblicata più di recente della soluzione (ad esempio, **1_0_0_4**).

     Verrà visualizzato il messaggio "ExcelWorkbook.vsto firmato correttamente".

5. Copiare il file *ExcelWorkbook. VSTO* nella directory **c:\publish\Application Files\ExcelWorkbook** \_ _MostRecentVersionNumber_

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a> Inserire il documento di una soluzione in un server in cui è in esecuzione SharePoint (solo personalizzazioni a livello di documento)
 È possibile pubblicare la personalizzazione a livello di documento agli utenti finali tramite SharePoint. Quando gli utenti visitano il sito di SharePoint e aprono il documento, la soluzione viene automaticamente installata dalla cartella di rete condivisa nei computer locali degli utenti. Una volta che la soluzione è installata localmente, la personalizzazione continuerà a essere valida anche se il documento viene copiato in un'altra posizione, ad esempio sul desktop.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Per inserire il documento in un server in cui è eseguito SharePoint

1. Aggiungere il documento della soluzione a una raccolta documenti su un sito di SharePoint.

2. Effettuare i passaggi per uno degli approcci indicati di seguito:

    - Usare lo strumento di configurazione di Office per aggiungere il server in cui è eseguito SharePoint al Centro protezione in Word o Excel in tutti i computer degli utenti.

         Vedere [criteri e impostazioni di sicurezza in Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)).

    - Assicurarsi che ogni utente esegua i passaggi indicati di seguito.

        1. Nel computer locale aprire Word o Excel, scegliere la scheda **file** , quindi scegliere il pulsante **Opzioni** .

        2. Nella finestra di dialogo **Centro protezione** scegliere il pulsante **percorsi attendibili** .

        3. Selezionare la casella di controllo **Consenti percorsi attendibili sulla rete (scelta non consigliata)** , quindi scegliere il pulsante **Aggiungi nuova posizione** .

        4. Nella casella **percorso** immettere l'URL della raccolta documenti di SharePoint contenente il documento caricato (ad esempio, *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName* ).

             Non aggiungere il nome della pagina Web predefinita, ad esempio *default. aspx* o *AllItems. aspx*.

        5. Selezionare la casella **di controllo anche le sottocartelle di questo percorso sono attendibili** , quindi scegliere il pulsante **OK** .

             Nel momento in cui gli utenti aprono il documento dal sito di SharePoint, il documento viene aperto e la personalizzazione viene installata. Gli utenti possono copiare il documento sul proprio desktop. L'esecuzione della personalizzazione continuerà perché le proprietà nel documento puntano al percorso di rete del documento.

## <a name="create-a-custom-installer"></a><a name="Custom"></a> Creare un programma di installazione personalizzato
 È possibile creare un programma di installazione personalizzato per la soluzione Office, anziché usare il programma di installazione creato automaticamente quando si pubblica la soluzione. Ad esempio, è possibile usare uno script di accesso per avviare l'installazione oppure è possibile usare un file batch per installare la soluzione senza interazione dell'utente. Questi scenari offrono i risultati migliori se i prerequisiti sono già installati nei computer degli utenti finali.

 Come parte del processo di installazione personalizzato, chiamare lo strumento di installazione per le soluzioni Office (*VSTOInstaller.exe*), che viene installato nel percorso seguente per impostazione predefinita:

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Se lo strumento non è presente in tale posizione, è possibile usare la chiave del registro di sistema **HKEY_LOCAL_MACHINE \Software\microsoft\vsto Runtime Setup\v4\InstallerPath** o **HKEY_LOCAL_MACHINE \software\wow6432node\microsoft\vsto Runtime Setup\v4\InstallerPath** per trovare il percorso di tale strumento.

 È possibile usare i parametri seguenti con *VSTOinstaller.exe*.

| Parametro | Definizione |
|------------------| - |
| /Install o /I | Installa la soluzione. È necessario seguire questa opzione con il percorso di un manifesto di distribuzione. È possibile specificare un percorso sul computer locale o di una condivisione file UNC (Universal Naming Convention). È possibile specificare un percorso locale (*C:\FolderName\PublishFolder*), un percorso relativo (*Publish \\ *) o un percorso completo (* \\ \ServerName\FolderName* o http://<em>ServerName/FolderName</em>). |
| /Uninstall o /U | Disinstalla la soluzione. È necessario seguire questa opzione con il percorso di un manifesto di distribuzione. È possibile specificare che un percorso che può essere nel computer locale o in una condivisione file UNC. È possibile specificare un percorso locale (*c:\FolderName\PublishFolder*), un percorso relativo (*Publish \\ *) o un percorso completo (* \\ \ServerName\FolderName* o http://<em>ServerName/FolderName</em>). |
| /Silent o /S | Installa o disinstalla senza richiedere input da parte dell'utente o visualizzare un messaggio. Se è richiesta una richiesta di attendibilità, la personalizzazione non viene installata o aggiornata. |
| /Help o /? | Visualizza le informazioni della Guida. |

 Quando si esegue *VSTOinstaller.exe*, è possibile che vengano visualizzati i codici di errore seguenti.

|Codice di errore|Definizione|
|----------------|----------------|
|0|La soluzione è stata installata o disinstallata correttamente oppure è stata visualizzata la Guida di VSTOInstaller.|
|-100|Una o più opzioni della riga di comando non sono valide o sono state impostate più di una volta. Per ulteriori informazioni, immettere "VSTOInstaller/?". in alternativa, vedere [creare un programma di installazione personalizzato per una soluzione Office ClickOnce](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e).|
|-101|Una o più opzioni della riga di comando non sono valide. Per altre informazioni, immettere "vstoinstaller /?".|
|-200|L'URI del manifesto di distribuzione non è valido. Per altre informazioni, immettere "vstoinstaller /?".|
|-201|Non è stato possibile installare la soluzione perché il manifesto di distribuzione non è valido. Vedere [manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md).|
|-202|Non è stato possibile installare la soluzione perché la sezione Strumenti di Visual Studio per Office del manifesto dell'applicazione non è valida. Vedere [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).|
|-203|Non è stato possibile installare la soluzione perché si è verificato un errore di download. Controllare l'URI o il percorso del file di rete del manifesto di distribuzione, quindi provare di nuovo.|
|-300|Non è stato possibile installare la soluzione perché si è verificata un'eccezione di sicurezza. Vedere [proteggere le soluzioni Office](../vsto/securing-office-solutions.md).|
|-400|Non è stato possibile installare la soluzione.|
|-401|Non è stato possibile disinstallare la soluzione.|
|-500|L'operazione è stata annullata perché non è stato possibile installare o disinstallare la soluzione o scaricare il manifesto di distribuzione.|

## <a name="publish-an-update"></a><a name="Update"></a> Pubblicare un aggiornamento
 Per aggiornare una soluzione, è necessario pubblicarla di nuovo utilizzando **Progettazione progetti** o **pubblicazione guidata**, quindi copiare la soluzione aggiornata nel percorso di installazione. Quando si copiano i file nel percorso di installazione, assicurarsi di sovrascrivere i file precedenti.

 Alla successiva verifica della presenza di un aggiornamento, la soluzione troverà e caricherà automaticamente la nuova versione.

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a> Modificare il percorso di installazione di una soluzione
 È possibile aggiungere o modificare il percorso di installazione dopo la pubblicazione di una soluzione. È possibile che si desideri modificare il percorso di installazione per uno o più dei motivi seguenti:

- Il percorso di installazione non era noto quando il programma di installazione è stato compilato.

- I file della soluzione sono stati copiati in un percorso diverso.

- Il server che ospita i file di installazione ha un nome o un percorso nuovo.

  Per modificare il percorso di installazione di una soluzione, è necessario aggiornare il programma di installazione e successivamente gli utenti devono eseguirlo. Per le personalizzazioni a livello di documento, gli utenti devono aggiornare anche una proprietà nel proprio documento in modo che punti al nuovo percorso.

> [!NOTE]
> Se non si vuole chiedere agli utenti di aggiornare le proprietà del documento, è possibile chiedere agli utenti di ottenere il documento aggiornato dal percorso di installazione.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Per modificare il percorso di installazione nel programma di installazione

1. Aprire una finestra del **prompt dei comandi** , quindi passare alla cartella di installazione.

2. Eseguire il programma di installazione e includere il parametro `/url`, che assumerà come stringa il nuovo percorso di installazione.

    Nell'esempio seguente viene illustrato come modificare il percorso di installazione in un percorso sul sito Web di Fabrikam, ma è possibile sostituire tale URL con il percorso desiderato:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Se viene visualizzato un messaggio per segnalare che la firma dell'eseguibile sarà invalidata, il certificato usato per firmare la soluzione non è più valido e l'editore è sconosciuto. Di conseguenza, gli utenti dovranno confermare l'attendibilità dell'origine della soluzione prima di poterla installare.

   > [!NOTE]
   > Per visualizzare il valore corrente dell'URL, eseguire `setup.exe /url`.

   Per le personalizzazioni a livello di documento, gli utenti devono aprire il documento e quindi aggiornare la relativa proprietà _AssemblyLocation. Di seguito viene descritta la procedura che gli utenti devono seguire per eseguire questa attività.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>Per aggiornare la proprietà _AssemblyLocation in un documento

1. Nella scheda **file** scegliere **info**, mostrata nella figura seguente.

     ![Scheda Informazioni in Excel](../vsto/media/vsto-infotab.png "Scheda Informazioni in Excel")

2. Nell'elenco **Proprietà** scegliere **proprietà avanzate**, mostrate nella figura seguente.

     ![Proprietà avanzate in Excel.](../vsto/media/vsto-advanceddocumentproperties.png "Proprietà avanzate in Excel.")

3. Nella scheda **personalizzata** dell'elenco **Proprietà** scegliere _AssemblyLocation, come illustrato nella figura seguente.

     ![Proprietà AssemblyLocation.](../vsto/media/vsto-assemblylocationproperty.png "Proprietà AssemblyLocation.")

     La casella **valore** contiene l'identificatore del manifesto della distribuzione.

4. Prima dell'identificatore, immettere il percorso completo del documento, seguito da una barra, nell'identificatore del *percorso*di formato, | *Identifier* ad esempio *file://ServerName/FolderName/filename|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.

     Per altre informazioni su come formattare questo identificatore, vedere [Cenni preliminari sulle proprietà personalizzate del documento](../vsto/custom-document-properties-overview.md).

5. Scegliere il pulsante **OK** , quindi salvare e chiudere il documento.

6. Eseguire il programma di installazione senza il parametro /url per installare la soluzione nel percorso specificato.

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a> Eseguire il rollback di una soluzione a una versione precedente
 Eseguire il rollback di una soluzione significa riportare gli utenti a una versione precedente di tale soluzione.

#### <a name="to-roll-back-a-solution"></a>Per eseguire il rollback di una soluzione

1. Aprire il percorso di installazione della soluzione.

2. Nella cartella di pubblicazione di primo livello eliminare il manifesto di distribuzione (il file con *estensione VSTO* ).

3. Individuare la sottocartella della versione che si desidera ripristinare.

4. Copiare il manifesto di distribuzione da tale sottocartella alla cartella di pubblicazione di primo livello.

     Ad esempio, per eseguire il rollback di una soluzione denominata **OutlookAddIn1** dalla versione 1.0.0.1 alla versione 1.0.0.0, copiare il file **OutlookAddIn1. vsto** dalla cartella **OutlookAddIn1_1_0_0_0** . Incollare il file nella cartella di pubblicazione di primo livello, sovrascrivendo il manifesto di distribuzione specifico della versione per **OutlookAddIn1_1_0_0_1** già presente.

     Nell'illustrazione seguente viene mostrata la struttura della cartella di pubblicazione di questo esempio.

     ![Struttura della cartella di pubblicazione](../vsto/media/publishfolderstructure.png "Struttura della cartella di pubblicazione")

     Alla successiva apertura del documento personalizzato o dell'applicazione da parte dell'utente, verrà rilevata la modifica al manifesto di distribuzione. La versione precedente della soluzione Office viene eseguita dalla cache ClickOnce.

> [!NOTE]
> I dati locali vengono salvati soltanto per una versione precedente di una soluzione. Se si esegue il rollback di due versioni, i dati locali non vengono conservati. Per altre informazioni sui dati locali, vedere [accedere ai dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Vedere anche

- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
- [Pubblicare soluzioni Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Procedura: pubblicare una soluzione Office tramite ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Procedura: installare una soluzione Office ClickOnce](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)
- [Procedura: pubblicare una soluzione Office a livello di documento in un server SharePoint tramite ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)
- [Creare un programma di installazione personalizzato per una soluzione Office ClickOnce](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)