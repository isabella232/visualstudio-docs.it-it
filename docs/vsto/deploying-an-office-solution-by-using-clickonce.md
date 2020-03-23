---
title: Distribuire una soluzione Office tramite ClickOnceDeploy an Office solution by using ClickOnce
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
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416562"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Distribuire una soluzione Office tramite ClickOnceDeploy an Office solution by using ClickOnce
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

  Per ulteriori informazioni su come distribuire una soluzione Office creando un file di Windows Installer, vedere [Distribuire una soluzione Office utilizzando Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="publish-the-solution"></a><a name="Publish"></a>Pubblicare la soluzione
 È possibile pubblicare la soluzione utilizzando la **Pubblicazione guidata** o **Progettazione progetti**. In questa procedura verrà utilizzato **Progettazione progetti** perché viene fornito il set completo di opzioni di pubblicazione. Vedere [Pubblicazione guidata &#40;sviluppo di Office in Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>Per pubblicare la soluzione

1. In **Esplora soluzioni**scegliere il nodo denominato per il progetto.

2. Sulla barra dei menu scegliere **Progetto**, *Proprietà* **NomeProgetto**.

3. In **Progettazione progetti**scegliere la scheda **Pubblica,** come illustrato nella figura seguente.

    ![Scheda Pubblica in Progettazione progetti](../vsto/media/vsto-publishtab.png "Scheda Pubblica in Progettazione progetti")

4. Nella casella Percorso cartella di **pubblicazione (server ftp o percorso file)** immettere il percorso della cartella in cui si desidera copiare i file della soluzione in **Progettazione progetti.**

    È possibile fornire uno dei seguenti tipi di percorso.

   - Un percorso locale (ad esempio, *C:, NomeCartella o NomeCartella*).

   - Un percorso UNC (Uniform Naming Convention) di una cartella della rete , ad esempio, il percorso un'unT (Uniform Naming Convention) di una cartella della rete, ad esempio * \\.*

   - Un percorso relativo, ad esempio *PublishFolder\\*, ovvero la cartella in cui il progetto viene pubblicato per impostazione predefinita.

5. Nella casella **URL cartella** di installazione immettere il percorso completo del percorso in cui gli utenti finali troveranno la soluzione.

    Se non si conosce ancora la posizione, non immettere nulla in questo campo. Per impostazione predefinita, quando si usa ClickOnce, gli aggiornamenti vengono cercati nella cartella da cui gli utenti installano la soluzione.

6. Scegliere il pulsante **Prerequisiti** .

7. Nella finestra di dialogo **Prerequisiti verificare** che la casella di controllo **Crea programma di installazione per installare i componenti dei prerequisiti** sia selezionata.

8. Nell'elenco **Scegliere i prerequisiti da installare** selezionare le caselle di controllo per Windows Installer **4.5** e il pacchetto .NET Framework appropriato.

    Se ad esempio la [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]soluzione è destinata a , selezionare le caselle di controllo per **Windows Installer 4.5** e **Microsoft .NET Framework 4.5 Full**.

9. Se la soluzione è destinata a .NET Framework 4.5, selezionare anche la casella di controllo **Visual Studio 2010 Tools per Office Runtime.**

    > [!NOTE]
    > Per impostazione predefinita, questa casella di controllo non viene visualizzata. Per visualizzarla, è necessario creare un pacchetto di programma di avvio automatico. Vedere Creare un pacchetto del programma di avvio automatico per un componente aggiuntivo VSTO di [Office 2013 con Visual Studio 2012.](create-vsto-add-ins-for-office-by-using-visual-studio.md)

10. In Specificare il percorso di **installazione per i prerequisiti**scegliere una delle opzioni visualizzate e quindi fare clic sul pulsante **OK.**

     Nella tabella seguente viene descritta ciascuna opzione.

    |Opzione|Descrizione|
    |------------|-----------------|
    |**Scarica prerequisiti dal sito Web del fornitore del componente**|All'utente viene chiesto di scaricare e installare questi prerequisiti dal fornitore.|
    |**Scarica prerequisiti dallo stesso percorso dell'applicazione**|Il software prerequisito viene installato insieme alla soluzione. Se si seleziona questa opzione, tutti i pacchetti di prerequisiti vengono copiati automaticamente da Visual Studio nel percorso di pubblicazione. Per il corretto funzionamento di questa opzione, i pacchetti di prerequisiti devono essere presenti nel computer di sviluppo.|
    |**Scarica prerequisiti dal seguente percorso**|Tutti i pacchetti di prerequisiti vengono copiati da Visual Studio nella posizione specificata e vengono installati insieme alla soluzione.|

     Vedere [La finestra di dialogo Prerequisiti](../ide/reference/prerequisites-dialog-box.md).

11. Scegliere il pulsante **Aggiornamenti,** specificare la frequenza con cui si vuole che il componente aggiuntivo VSTO di ogni utente finale o la personalizzazione verifichi la disponibilità di aggiornamenti, quindi scegliere **OK.**

    > [!NOTE]
    > Se si esegue la distribuzione utilizzando un CD o un'unità rimovibile, scegliere il pulsante di opzione **Non verificare mai la** disponibilità di aggiornamenti.

     Per informazioni su come pubblicare un aggiornamento, consultate [Pubblicare un aggiornamento.](#Update)

12. Scegliere il pulsante **Opzioni,** rivedere le opzioni nella finestra di dialogo **Opzioni,** quindi scegliere **OK.**

13. Scegliere il pulsante **Pubblica ora.**

     Le cartelle e i file seguenti vengono aggiunti automaticamente da Visual Studio nella cartella di pubblicazione specificata precedentemente in questa procedura.

    - La cartella **File applicazione.**

    - Programma di installazione.

    - Manifesto di distribuzione che punta al manifesto di distribuzione della versione più recente.

      La cartella **File applicazione** contiene una sottocartella per ogni versione pubblicata. Ogni sottocartella relativa a una versione specifica contiene i file indicati di seguito.

    - Un manifesto dell'applicazione.

    - Un manifesto di distribuzione.

    - Assembly di personalizzazione.

      Nell'illustrazione seguente viene mostrata la struttura della cartella di pubblicazione di un componente aggiuntivo VSTO di Outlook.

      ![Pubblica struttura cartella](../vsto/media/publishfolderstructure.png "Struttura della cartella di pubblicazione")

    > [!NOTE]
    > ClickOnceClickOnce aggiunge l'estensione *.deploy* agli assembly in modo che un'installazione protetta di Internet Information Services (IIS) non blocchi i file a causa di un'estensione non sicura. Quando l'utente installa la soluzione, ClickOnceClickOnce rimuove l'estensione *deploy.*

14. Copiare i file della soluzione nel percorso di installazione specificato precedentemente in questa procedura.

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a>Decidere come concedere l'attendibilità alla soluzione
 Prima che una soluzione possa essere eseguita nei computer degli utenti, è necessario concedere l'attendibilità oppure gli utenti devono rispondere a una richiesta di attendibilità quando installano la soluzione. Per concedere l'attendibilità alla soluzione, firmare i manifesti usando un certificato che identifichi un editore conosciuto e attendibile. Vedere [Considerare attendibile la soluzione firmando i manifesti dell'applicazione e di distribuzione](../vsto/granting-trust-to-office-solutions.md#Signing).

 Se si distribuisce una personalizzazione a livello di documento e si desidera inserire il documento in una cartella nel computer dell'utente o rendere il documento disponibile in un sito di SharePoint, assicurarsi che Office consideri attendibile il percorso del documento. Vedere [Concedere l'attendibilità ai documenti](../vsto/granting-trust-to-documents.md).

## <a name="help-users-install-the-solution"></a><a name="Helping"></a>Aiutare gli utenti a installare la soluzione
 Gli utenti possono installare la soluzione eseguendo il programma di installazione, aprendo il manifesto di distribuzione o durante la personalizzazione a livello di documento, aprendo direttamente il documento. Come procedura consigliata, gli utenti devono installare la soluzione usando il programma di installazione. Gli altri due approcci non garantiscono che il software prerequisito sia installato. Se gli utenti desiderano aprire il documento dal percorso di installazione, devono aggiungerlo all'elenco dei percorsi attendibili nel Centro protezione dell'applicazione di Office.

### <a name="opening-the-document-of-a-document-level-customization"></a>Apertura del documento di una personalizzazione a livello di documento
 Gli utenti possono aprire il documento di una personalizzazione a livello di documento direttamente dal percorso di installazione oppure copiando il documento nei propri computer locali e aprendo quindi la copia.

 Come procedura consigliata, gli utenti devono aprire una copia del documento nei computer locali per evitare che più utenti tentino di aprire la stessa copia contemporaneamente. Per applicare questo approccio, è possibile configurare il programma di installazione in modo da copiare il documento nei computer degli utenti. Vedere [Inserire il documento di una soluzione nel computer dell'utente finale (solo personalizzazioni](#Put)a livello di documento).

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Installare la soluzione aprendo il manifesto di distribuzione da un sito Web IIS
 Gli utenti possono installare una soluzione Office aprendo il manifesto di distribuzione dal Web. Tuttavia, un'installazione protetta di Internet Information Services (IIS) bloccherà i file con estensione *vsto.* Il tipo MIME deve essere definito in IIS prima di poter distribuire una soluzione Office tramite IIS.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Per aggiungere il tipo MIME .vsto a IIS 6.0

1. Nel server che esegue IIS 6.0 scegliere **Start** > **All Programs** > **Administrative Tools** >  **Internet Information Services (IIS) Manager**.

2. Scegliere il nome del computer, la cartella **Siti Web** o il sito Web che si sta configurando.

3. Nella barra dei menu scegliere**Proprietà** **azione** > .

4. Nella scheda **Intestazioni HTTP** scegliere il pulsante **Tipi MIME.**

5. Nella finestra **Tipi MIME** scegliere il pulsante **Nuovo.**

6. Nella finestra **Tipo MIME** immettere **.vsto** come estensione, immettere **application/x-ms-vsto** come tipo MIME, quindi applicare le nuove impostazioni.

    > [!NOTE]
    > Per rendere effettive le modifiche è necessario riavviare il servizio Pubblicazione sul Web o attendere il riciclo del processo di lavoro. È quindi necessario scaricare la cache del disco del browser e quindi provare ad aprire nuovamente il file *vsto.*

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Per aggiungere il tipo MIME .vsto a IIS 7.0

1. Nel server che esegue IIS 7.0 scegliere **Start** > **All Programs** > **Accessories**.

2. Aprire il menu di scelta rapida per **Prompt dei comandi**, quindi scegliere Esegui come **amministratore.**

3. Nella casella **Apri** immettere il percorso seguente, quindi scegliere **OK.**

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Immettere il seguente comando, quindi applicare le nuove impostazioni.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > Per rendere effettive le modifiche è necessario riavviare il servizio Pubblicazione sul Web o attendere il riciclo del processo di lavoro. È quindi necessario scaricare la cache del disco del browser e quindi provare ad aprire nuovamente il file *vsto.*

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a>Inserire il documento di una soluzione nel computer dell'utente finale (solo personalizzazioni a livello di documento)
 È possibile copiare il documento della soluzione nel computer dell'utente finale creando un'azione post-distribuzione. In questo modo, l'utente non deve copiare manualmente il documento dal percorso di installazione al computer dopo aver installato la soluzione. È necessario creare una classe che definisce l'azione post-distribuzione, compilare e pubblicare la soluzione, modificare il manifesto dell'applicazione e firmare nuovamente il manifesto dell'applicazione e di distribuzione.

 Le procedure seguenti presuppongono che il nome del progetto sia **ExcelWorkbook** e che si pubblica la soluzione in una cartella creata denominata **C:.**

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Creare una classe che definisca l'azione post-distribuzione

1. Nella barra dei **File** > menu scegliere**Aggiungi** > **nuovo progetto**.

2. Nel riquadro **Modelli installati** della finestra di dialogo Aggiungi **nuovo progetto** scegliere la cartella **Windows.**

3. Nel riquadro **Modelli** scegliere il modello **Libreria di** classi.

4. Nel campo **Nome** immettere **FileCopyPDA**, quindi scegliere **OK.**

5. In **Esplora soluzioni**scegliere il progetto **FileCopyPDA.**

6. Nella barra dei menu scegliere**Aggiungi riferimento al** **progetto** > .

7. Nella scheda **.NET** aggiungere `Microsoft.VisualStudio.Tools.Applications.Runtime` riferimenti `Microsoft.VisualStudio.Tools.Applications.ServerDocument`a e .

8. Rinominare la classe in `FileCopyPDA`, quindi sostituire il contenuto del file con il codice. Il codice esegue queste operazioni:

   - Copia del documento sul desktop dell'utente.

   - Modifica la proprietà _AssemblyLocation da un percorso relativo a un percorso completo per il manifesto di distribuzione.

   - Eliminazione del file se l'utente disinstalla la soluzione.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>Compilare e pubblicare la soluzione

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **FileCopyPDA,** quindi scegliere **Compila**.

2. Aprire il menu di scelta rapida per il progetto **ExcelWorkbook** e quindi scegliere **Compila**.

3. Aprire il menu di scelta rapida per il progetto **ExcelWorkbook** e quindi scegliere **Aggiungi riferimento**.

4. Nella finestra di dialogo **Aggiungi riferimento** scegliere la scheda **Progetti** , quindi **FileCopyPDA**, quindi fare clic sul pulsante **OK.**

5. In **Esplora soluzioni**scegliere il progetto **ExcelWorkbook.In** Solution Explorer , choose the ExcelWorkbook project.

6. Nella barra dei menu scegliere **Proietta** > **nuova cartella**.

7. Immettere **Dati**, quindi premere **INVIO.**

8. In **Esplora soluzioni**scegliere la cartella **Dati.**

9. Nella barra dei menu scegliere **Aggiungi** > **elemento esistente**.

10. Nella finestra di dialogo **Aggiungi elemento esistente** passare alla directory di output per il progetto **ExcelWorkbook,** scegliere il file **ExcelWorkbook.xlsx,** quindi scegliere il pulsante **Aggiungi.**

11. In **Esplora soluzioni** scegliere il file **ExcelWorkbook.xlsx.**

12. Nella finestra **Proprietà** modificare la proprietà Operazione di **compilazione** in **Contenuto** e la proprietà **Copia nella directory di output** in Copia se più **recente**.

     Dopo aver completato questi passaggi, il progetto sarà simile alla figura seguente.

     ![Struttura progetto dell'azione post-distribuzione.](../vsto/media/vsto-postdeployment.png "Struttura progetto dell'azione post-distribuzione.")

13. Pubblicare il progetto **ExcelWorkbook.Publish** the ExcelWorkbook project.

### <a name="modify-the-application-manifest"></a>Modificare il manifesto dell'applicazione

1. Aprire la directory della soluzione, **c:, pubblica**, utilizzando **Esplora file**.

2. Aprire la cartella **File applicazione** e quindi aprire la cartella corrispondente alla versione pubblicata più recente della soluzione.

3. Aprire il file **ExcelWorkbook.dll.manifest** in un editor di testo, ad esempio Blocco note.

4. Dopo l'elemento `</vstav3:update>` aggiungere il codice seguente. Per l'attributo `<vstav3:entryPoint>` class dell'elemento, utilizzare la sintassi seguente: *NamespaceName.ClassName*. Nell'esempio riportato di seguito il nome dello spazio dei nomi è uguale a quello della classe. Pertanto, il nome del punto di ingresso risultante è `FileCopyPDA.FileCopyPDA`.

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

1. Nella cartella **%USERPROFILE%, Documents, Visual Studio 2013, Projects, ExcelWorkbook, ExcelWorkbook,** copiare il file di certificato **ExcelWorkbook_TemporaryKey.pfx** e quindi incollarlo nella cartella *PublishFolder* **, Application Files , ExcelWorkbook**\__MostRecentPublishedVersion_ .

2. Aprire il prompt dei comandi di Visual Studio e quindi passare alla cartella c: , publish , **Application Files , ExcelWorkbook**\__MostRecentPublishedVersion (ad_ esempio, **c:**, publish , Application Files ExcelWorkbook_1_0_0_4 ).

3. Firmare il manifesto dell'applicazione modificato usando il comando seguente:

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     Verrà visualizzato il messaggio "ExcelWorkbook.dll.manifest firmato correttamente".

4. Passare alla cartella **c:,** quindi aggiornare e firmare il manifesto di distribuzione eseguendo il comando seguente:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > Nell'esempio precedente sostituire MostRecentVersionNumber con il numero di versione della versione pubblicata più di recente della soluzione, ad esempio **1_0_0_4**.

     Verrà visualizzato il messaggio "ExcelWorkbook.vsto firmato correttamente".

5. Copiare il file *ExcelWorkbook.vsto* nella_directory_ **c:.**\_

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a>Inserire il documento di una soluzione in un server che esegue SharePoint (solo personalizzazioni a livello di documento)
 È possibile pubblicare la personalizzazione a livello di documento agli utenti finali tramite SharePoint. Quando gli utenti visitano il sito di SharePoint e aprono il documento, la soluzione viene automaticamente installata dalla cartella di rete condivisa nei computer locali degli utenti. Una volta che la soluzione è installata localmente, la personalizzazione continuerà a essere valida anche se il documento viene copiato in un'altra posizione, ad esempio sul desktop.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Per inserire il documento in un server in cui è eseguito SharePoint

1. Aggiungere il documento della soluzione a una raccolta documenti su un sito di SharePoint.

2. Effettuare i passaggi per uno degli approcci indicati di seguito:

    - Usare lo strumento di configurazione di Office per aggiungere il server in cui è eseguito SharePoint al Centro protezione in Word o Excel in tutti i computer degli utenti.

         Vedere Criteri e impostazioni di [sicurezza in Office 2010.](/previous-versions/office/office-2010/cc178946(v=office.14))

    - Assicurarsi che ogni utente esegua i passaggi indicati di seguito.

        1. Nel computer locale aprire Word o Excel, scegliere la scheda **File** e quindi fare clic sul pulsante **Opzioni.**

        2. Nella finestra di dialogo **Centro protezione** scegliere il pulsante **Percorsi attendibili.**

        3. Selezionare la casella di controllo **Consenti percorsi attendibili nella rete (scelta non consigliata),** quindi scegliere il pulsante **Aggiungi nuovo percorso.**

        4. Nella casella **Percorso** immettere l'URL della raccolta documenti di SharePoint contenente *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*il documento caricato, ad esempio .

             Non aggiungere il nome della pagina Web predefinita, ad esempio *default.aspx* o *AllItems.aspx*.

        5. Selezionare la casella di controllo **Considera attendibili anche le sottocartelle di questo percorso,** quindi scegliere OK. **OK**

             Nel momento in cui gli utenti aprono il documento dal sito di SharePoint, il documento viene aperto e la personalizzazione viene installata. Gli utenti possono copiare il documento sul proprio desktop. L'esecuzione della personalizzazione continuerà perché le proprietà nel documento puntano al percorso di rete del documento.

## <a name="create-a-custom-installer"></a><a name="Custom"></a>Creare un programma di installazione personalizzatoCreate a custom installer
 È possibile creare un programma di installazione personalizzato per la soluzione Office, anziché utilizzare il programma di installazione creato automaticamente quando si pubblica la soluzione. Ad esempio, è possibile utilizzare uno script di accesso per avviare l'installazione oppure un file batch per installare la soluzione senza l'interazione dell'utente. Questi scenari offrono i risultati migliori se i prerequisiti sono già installati nei computer degli utenti finali.

 Come parte del processo di installazione personalizzato, chiamare lo strumento di installazione per le soluzioni Office (*VSTOInstaller.exe*), che viene installato nel seguente percorso per impostazione predefinita:

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Se lo strumento non si trova in tale percorso, è possibile utilizzare la chiave del Registro di sistema HKEY_LOCAL_MACHINE SOFTWARE , Microsoft **HKEY_LOCAL_MACHINE** **.**

 È possibile utilizzare i seguenti parametri con *VSTOinstaller.exe*.

| Parametro | Definizione |
|------------------| - |
| /Install o /I | Installa la soluzione. È necessario seguire questa opzione con il percorso di un manifesto di distribuzione. È possibile specificare un percorso sul computer locale o di una condivisione file UNC (Universal Naming Convention). È possibile specificare un percorso locale (*C:, NomeCartella o CartellaPubblicazione*), un percorso relativo (*Pubblica\\*) o un percorso completo (*\\NomeServer/NomeCartella* o http://<em>NomeServer/NomeCartella</em>). |
| /Uninstall o /U | Disinstalla la soluzione. È necessario seguire questa opzione con il percorso di un manifesto di distribuzione. È possibile specificare che un percorso che può essere nel computer locale o in una condivisione file UNC. È possibile specificare un percorso locale (*c:, NomeCartella/CartellaPubblicazione),* un percorso relativo (*Pubblica\\*) o un percorso completo (*\\NomeServer/NomeCartella* o http://<em>NomeServer/NomeCartella</em>). |
| /Silent o /S | Installa o disinstalla senza richiedere input da parte dell'utente o visualizzare un messaggio. Se è necessaria una richiesta di attendibilità, la personalizzazione non viene installata o aggiornata. |
| /Help o /? | Visualizza le informazioni della Guida. |

 Quando si esegue *VSTOinstaller.exe*, è possibile che vengano visualizzati i seguenti codici di errore.

|Codice di errore|Definizione|
|----------------|----------------|
|0|La soluzione è stata installata o disinstallata correttamente oppure è stata visualizzata la Guida di VSTOInstaller.|
|-100|Una o più opzioni della riga di comando non sono valide o sono state impostate più di una volta. Per ulteriori informazioni, immettere "vstoinstaller /?" in [alternativa, vedere Creare un programma di installazione personalizzato per una soluzione Office ClickOnce](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e).|
|-101|Una o più opzioni della riga di comando non sono valide. Per altre informazioni, immettere "vstoinstaller /?".|
|-200|L'URI del manifesto di distribuzione non è valido. Per altre informazioni, immettere "vstoinstaller /?".|
|-201|Impossibile installare la soluzione perché il manifesto di distribuzione non è valido. Vedere Manifesti di [distribuzione per soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md).|
|-202|Impossibile installare la soluzione perché la sezione Visual Studio Tools for Office del manifesto dell'applicazione non è valida. Vedere [Manifesti dell'applicazione per soluzioni Office](../vsto/application-manifests-for-office-solutions.md).|
|-203|Impossibile installare la soluzione perché si è verificato un errore di download. Controllare l'URI o il percorso del file di rete del manifesto di distribuzione, quindi provare di nuovo.|
|-300|Impossibile installare la soluzione perché si è verificata un'eccezione di sicurezza. Vedere [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md).|
|-400|Impossibile installare la soluzione.|
|-401|Impossibile disinstallare la soluzione.|
|-500|L'operazione è stata annullata perché non è stato possibile installare o disinstallare la soluzione o scaricare il manifesto di distribuzione.|

## <a name="publish-an-update"></a><a name="Update"></a>Pubblicare un aggiornamento
 Per aggiornare una soluzione, pubblicarla nuovamente utilizzando **Progettazione progetti** o **Pubblicazione guidata**, quindi copiare la soluzione aggiornata nel percorso di installazione. Quando si copiano i file nel percorso di installazione, assicurarsi di sovrascrivere i file precedenti.

 La volta successiva che la soluzione verifica la disponibilità di un aggiornamento, troverà e caricherà automaticamente la nuova versione.

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a>Modificare il percorso di installazione di una soluzione
 È possibile aggiungere o modificare il percorso di installazione dopo la pubblicazione di una soluzione. È possibile che si desideri modificare il percorso di installazione per uno o più dei motivi seguenti:

- Il percorso di installazione non era noto quando il programma di installazione è stato compilato.

- I file della soluzione sono stati copiati in un percorso diverso.

- Il server che ospita i file di installazione ha un nome o un percorso nuovo.

  Per modificare il percorso di installazione di una soluzione, è necessario aggiornare il programma di installazione e successivamente gli utenti devono eseguirlo. Per le personalizzazioni a livello di documento, gli utenti devono aggiornare anche una proprietà nel proprio documento in modo che punti al nuovo percorso.

> [!NOTE]
> Se non si desidera chiedere agli utenti di aggiornare le proprietà del documento, è possibile chiedere agli utenti di ottenere il documento aggiornato dal percorso di installazione.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Per modificare il percorso di installazione nel programma di installazione

1. Aprire una finestra **del prompt dei comandi** e quindi passare alla cartella di installazione.

2. Eseguire il programma di installazione e includere il parametro `/url`, che assumerà come stringa il nuovo percorso di installazione.

    Nell'esempio seguente viene illustrato come modificare il percorso di installazione in un percorso sul sito Web di Fabrikam, ma è possibile sostituire tale URL con il percorso desiderato:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Se viene visualizzato un messaggio per segnalare che la firma dell'eseguibile sarà invalidata, il certificato usato per firmare la soluzione non è più valido e l'editore è sconosciuto. Di conseguenza, gli utenti dovranno confermare l'attendibilità dell'origine della soluzione prima di poterla installare.

   > [!NOTE]
   > Per visualizzare il valore corrente dell'URL, eseguire `setup.exe /url`.

   Per le personalizzazioni a livello di documento, gli utenti devono aprire il documento e quindi aggiornare la proprietà _AssemblyLocation. Di seguito viene descritta la procedura che gli utenti devono seguire per eseguire questa attività.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>Per aggiornare la proprietà _AssemblyLocation in un documento

1. Nella scheda **File** scegliere **Informazioni**, come illustrato nella figura seguente.

     ![Scheda Informazioni in Excel](../vsto/media/vsto-infotab.png "Scheda Informazioni in Excel")

2. Nell'elenco **Proprietà** scegliere **Proprietà avanzate**, come illustrato nella figura seguente.

     ![Proprietà avanzate in Excel.](../vsto/media/vsto-advanceddocumentproperties.png "Proprietà avanzate in Excel.")

3. Nella scheda **Personalizzato** dell'elenco **Proprietà** scegliere _AssemblyLocation, come illustrato nella figura seguente.

     ![Proprietà AssemblyLocation.](../vsto/media/vsto-assemblylocationproperty.png "Proprietà AssemblyLocation.")

     La casella **Valore** contiene l'identificatore del manifesto di distribuzione.

4. Prima dell'identificatore, immettere il percorso completo del documento, seguito da una barra, nel formato*Identificatore* *percorso*|(ad esempio, *File://ServerName/FolderName/FileName|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.

     Per ulteriori informazioni su come formattare questo identificatore, consultate Panoramica delle proprietà personalizzate del [documento.](../vsto/custom-document-properties-overview.md)

5. Scegliere **il** ok pulsante, quindi salvare e chiudere il documento.

6. Eseguire il programma di installazione senza il parametro /url per installare la soluzione nel percorso specificato.

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a>Ripristinare una soluzione a una versione precedente
 Eseguire il rollback di una soluzione significa riportare gli utenti a una versione precedente di tale soluzione.

#### <a name="to-roll-back-a-solution"></a>Per eseguire il rollback di una soluzione

1. Aprire il percorso di installazione della soluzione.

2. Nella cartella di pubblicazione di primo livello eliminare il manifesto di distribuzione (il file *vsto).*

3. Individuare la sottocartella della versione che si desidera ripristinare.

4. Copiare il manifesto di distribuzione da tale sottocartella alla cartella di pubblicazione di primo livello.

     Ad esempio, per eseguire il rollback di una soluzione denominata **OutlookAddIn1** dalla versione 1.0.0.1 alla versione 1.0.0.0, copiare il file **OutlookAddIn1.vsto** dalla cartella **OutlookAddIn1_1_0_0_0.** Incollare il file nella cartella di pubblicazione di primo livello, sovrascrivendo il manifesto di distribuzione specifico della versione per **OutlookAddIn1_1_0_0_1** già presente.

     Nell'illustrazione seguente viene mostrata la struttura della cartella di pubblicazione di questo esempio.

     ![Pubblica struttura cartella](../vsto/media/publishfolderstructure.png "Struttura della cartella di pubblicazione")

     Alla successiva apertura del documento personalizzato o dell'applicazione da parte dell'utente, verrà rilevata la modifica al manifesto di distribuzione. La versione precedente della soluzione Office viene eseguita dalla cache ClickOnce.

> [!NOTE]
> I dati locali vengono salvati soltanto per una versione precedente di una soluzione. Se si esegue il rollback di due versioni, i dati locali non vengono mantenuti. Per ulteriori informazioni sui dati locali, vedere [Accedere a dati locali e remoti nelle applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Vedere anche

- [Distribuire una soluzione OfficeDeploy an Office solution](../vsto/deploying-an-office-solution.md)
- [Pubblicare soluzioni Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Procedura: pubblicare una soluzione Office tramite ClickOnceHow to: Publish an Office solution by using ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Procedura: installare una soluzione Office ClickOnceHow to: Install a ClickOnce Office solution](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)
- [Procedura: pubblicare una soluzione Office a livello di documento in un server SharePoint tramite ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)
- [Creare un programma di installazione personalizzato per una soluzione Office ClickOnceCreate a custom installer for a ClickOnce office solution](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)