---
title: Distribuire una soluzione Office tramite Windows Installer
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, setup project
- Office development in Visual Studio, MSI
- deploying applications [Office development in Visual Studio], setup project
- deploying applications [Office development in Visual Studio], MSI
- ClickOnce deployment [Office development in Visual Studio], MSI
- publishing Office solutions [Office development in Visual Studio], setup project
- Office applications [Office development in Visual Studio], MSI
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 91349edaeb864e913351e79846825fb67f2d7d97
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864085"
---
# <a name="deploy-an-office-solution-by-using-windows-installer"></a>Distribuire una soluzione Office tramite Windows Installer
Informazioni su come creare un file di Windows Installer per la soluzione Office mediante [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  

Se si usa Visual Studio per creare un file di Windows Installer, è possibile distribuire una soluzione Office che richiede accesso amministrativo nel computer dell'utente finale. Ad esempio, è possibile usare tale file per installare una soluzione solo una volta per tutti gli utenti di un computer. È inoltre possibile distribuire una soluzione Office usando ClickOnce, ma tale soluzione deve essere installata separatamente per ogni utente del computer.  


## <a name="in-this-topic"></a>Contenuto dell'argomento  

- [Scaricare esempi di componente aggiuntivo VSTO](#Download)  

- [Ottenere InstallShield Limited Edition](#Obtain)  

- [Scegliere come concedere l'attendibilità alla soluzione](#ApplySecurity)  

- [Creare un progetto di installazione](#Create)  

- [Aggiungere l'output del progetto](#Add)  

- [Aggiungere i manifesti dell'applicazione e della distribuzione](#AddD)  

- [Configurare i componenti dipendenti come prerequisiti](#Configure)  

- [Specificare dove si desidera distribuire la soluzione nel computer dell'utente](#Location)  

- [Configurare un componente aggiuntivo VSTO](#ConfigureRegistry)  

- [Configure a document-level customization](#ConfigureDocument)  

- [Build the setup project](#Build)  

Per altre informazioni su come distribuire una soluzione Office usando ClickOnce, vedere [distribuire una soluzione Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  

Per informazioni su come creare un file Windows Installer tramite [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], vedere [distribuire un Visual Studio 2010 Tools per la soluzione Office mediante Windows Installer](http://go.microsoft.com/fwlink/?LinkId=201807).  


## <a name="Download"></a>Scaricare esempi  
Questo argomento si riferisce ai seguenti esempi scaricabili.  



|Esempio<br /><br />|Descrizione<br /><br />|  
|----------|---------------|  
|[ExcelAddIn](http://go.microsoft.com/fwlink/?LinkID=275492)<br /><br />|Componente aggiuntivo VSTO di Excel che può essere installato in un computer che esegue una versione di Office a 32 o 64 bit.<br /><br />|  
|[ExcelWorkbook](http://go.microsoft.com/fwlink/?LinkID=275493)<br /><br />|Personalizzazione a livello di documento di Excel che è possibile installare su un computer che esegue una versione di Office a 32 o a 64 bit.<br /><br />|  

## <a name="ApplySecurity"></a>Scegliere come concedere l'attendibilità alla soluzione  
Prima che una soluzione possa essere eseguita nei computer degli utenti, è necessario concedere l'attendibilità in una delle modalità seguenti oppure gli utenti devono rispondere a una richiesta di attendibilità quando installano la soluzione.  


- Firmare i manifesti con un certificato che identifica un editore conosciuto e attendibile. Per altre informazioni, vedere [considerare attendibile la soluzione firmando i manifesti dell'applicazione e distribuzione](../vsto/granting-trust-to-office-solutions.md#Signing).  

- Installare la soluzione per la directory dei file di programma nel computer dell'utente.  

> [!NOTE]  
> Per le personalizzazioni a livello di documento, anche il percorso del documento deve essere considerato attendibile. Per altre informazioni, vedere [concedere l'attendibilità a documenti](../vsto/granting-trust-to-documents.md).  


## <a name="Obtain"></a>Ottenere InstallShield Limited Edition  
È possibile creare un file di Windows Installer tramite InstallShield Limited Edition (ISLE), che è gratuito se è stato installato Visual Studio. ISLE sostituisce la funzionalità dei modelli di progetto per l'installazione e la distribuzione offerta dalle versioni precedenti di Visual Studio.  


### <a name="to-get-installshield-limited-edition"></a>Per ottenere InstallShield Limited Edition  

1. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.  

   Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  

2. Nel riquadro dei modelli espandere **Altri tipi di progetto**, quindi selezionare il modello **Installazione e distribuzione** .  

3. Nell'elenco dei tipi di progetto per **Installazione e distribuzione**scegliere **Abilita InstallShield Limited Edition**, quindi scegliere il pulsante **OK** .  

   Viene visualizzata una pagina che fornisce informazioni su come ottenere InstallShield Limited Edition.  

4. In questa pagina scegliere il collegamento **Visitare il sito Web di download** .  

5. Nella pagina di download di InstallShield Limited Edition, immettere le informazioni necessarie nei campi appropriati, quindi scegliere il collegamento **Scarica ora** .  

   Dopo avere scaricato, installato e attivato il prodotto, in Visual Studio viene visualizzato il modello **Progetto InstallShield Limited Edition** .  


## <a name="Create"></a>Creare un progetto di installazione  

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]aprire il progetto di Office che si desidera distribuire.  

   Gli esempi di componente aggiuntivo VSTO associati a questo argomento contengono un progetto chiamato **ExcelAddIn**. Gli esempi di personalizzazione a livello di documento contengono un progetto denominato **ExcelWorkbook**. In questo argomento sarà fatto riferimento al progetto di Office nella soluzione usando uno dei due nomi.  

2. Nella barra dei menu, scegliere **File** > **Add** > **nuovo progetto**.  

   Verrà aperta la finestra di dialogo **Aggiungi nuovo progetto** .  

3. Nel riquadro dei modelli espandere **Altri tipi di progetto**, quindi selezionare il modello **Installazione e distribuzione** .  

4. Nell'elenco dei tipi di progetto per **Installazione e distribuzione**scegliere **Progetto InstallShield Limited Edition**, assegnare un nome al progetto, quindi scegliere il pulsante **OK** .  

   Il progetto di installazione di InstallShield creato viene visualizzato nella soluzione.  

   Gli esempi di questo argomento contengono un progetto di installazione denominato **OfficeAddInSetup**. In questo argomento sarà fatto riferimento al progetto di installazione nella soluzione usando lo stesso nome.  


## <a name="Add"></a>Aggiungere l'output del progetto  
Configurare il progetto **OfficeAddInSetup** per includere l'output del progetto di Office. Per i progetti di componente aggiuntivo VSTO, l'output del progetto è solo l'assembly della soluzione. Per i progetti di personalizzazione a livello di documento, l'output del progetto include non solo l'assembly della soluzione ma anche il documento stesso.  


### <a name="to-add-the-project-output"></a>Per aggiungere l'output del progetto  

1. In **Esplora soluzioni**, espandere il nodo del progetto **OfficeAddInSetup** , quindi scegliere il file **Project Assistant** illustrato nell'immagine seguente.  

   ![Project Assistant File in Esplora soluzioni](../vsto/media/installshield-projectassistant.png "Project Assistant File in Esplora soluzioni")  

2. Nella barra dei menu, scegliere **View** > **Open**.  

3. Nella parte inferiore della pagina **Project Assistant** , scegliere il pulsante **File applicazione** mostrato nell'immagine seguente.  

   ![Il pulsante con i file dell'applicazione. ](../vsto/media/installshield-applicationfiles.png "Pulsante il file dell'applicazione.")  

4. Nella pagina **File applicazione** selezionare il pulsante **Aggiungi output progetto** .  

5. Nella finestra di dialogo **Selettore output di Visual Studio** selezionare la casella di controllo **Output primario** , quindi fare clic sul pulsante **OK** .  


## <a name="AddD"></a>Aggiungere i manifesti dell'applicazione e della distribuzione  

###  
1. Nella pagina **File applicazione** selezionare il pulsante **Aggiungi file** .  

2. Nella finestra di dialogo **Apri** individuare la directory di output del progetto **ExcelAddIn** .  

   In genere, la directory di output è la sottocartella **bin\release** della directory radice del progetto, a seconda della configurazione di compilazione selezionata.  

3. Nella directory di output selezionare i file **ExcelAddIn.vsto** e **ExcelAddIn.dll.manifest** , quindi scegliere il pulsante **Apri** .  

   La pagina **File applicazione** ora contiene il file di output del progetto, il manifesto di distribuzione e il manifesto dell'applicazione, come mostrato nella figura seguente.  

   ![I file di output del progetto di installazione. ](../vsto/media/installshield-outputfiles.png "i file di output del progetto di installazione.")  


## <a name="Configure"></a>Configurare i componenti dipendenti come prerequisiti  
Nell'applicazione di installazione è necessario includere, oltre ai componenti seguenti, anche tutti gli altri necessari per consentire l'esecuzione della soluzione.  


- Versione di .NET Framework a cui è destinata la soluzione Office.  

- Microsoft Visual Studio 2010 Tools per Office Runtime.  


### <a name="add-the-net-framework-4-or-the-net-framework-45-as-a-prerequisite"></a>Aggiungere .NET Framework 4 o .NET Framework 4.5 come prerequisito  

1. In **Esplora soluzioni**, espandere il nodo di progetto **OfficeAddInSetup** , espandere il nodo **Specifica dati applicazione** , quindi selezionare il file **Ridistribuibili** illustrato nell'immagine seguente.  

   ![File ridistribuibili in Esplora soluzioni](../vsto/media/installshield-redistributablesfile.png "ridistribuibili di file in Esplora soluzioni")  

2. Nella barra dei menu, scegliere **View** > **Open**.  

   Verrà visualizzata la pagina **Ridistribuibili** .  

3. Nell'elenco di componenti ridistribuibili, selezionare la casella di controllo appropriata per la versione di .NET Framework a cui è destinata la soluzione.  

   Ad esempio, se la soluzione è destinata a [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], selezionare la casella di controllo **Microsoft .NET Framework 4.5 Full** . Potrebbe essere visualizzata una finestra di dialogo in cui viene chiesto se si desidera installare il componente ridistribuibile che InstallShield richiede come prerequisito prima che sia possibile aggiungere il componente. Se non viene visualizzata questa finestra di dialogo, il componente esiste già nel computer.  

4. Se viene visualizzata questa finestra di dialogo, selezionare il pulsante **No** .  


### <a name="AddToolsForOffice"></a>Aggiungere Visual Studio 2010 Tools per Office Runtime  
La pagina **Ridistribuibili** contiene un elemento denominato **Runtime di Microsoft VSTO 2010**, ma fa riferimento a una versione precedente del runtime. Pertanto, è possibile creare manualmente un file di configurazione che fa riferimento alla versione più recente. È quindi necessario inserire il file nella stessa directory dei file di configurazione per tutti gli altri elementi visualizzati nella pagina **Ridistribuibili** .  


#### <a name="to-add-the-visual-studio-2010-tools-for-office-runtime-as-a-prerequisite"></a>Per aggiungere Visual Studio 2010 Tools per Office runtime come prerequisito  

1. Aprire il Blocco note, quindi incollare il seguente XML in un file di testo.  


   ```xml  
   <?xml version="1.0" encoding="UTF-8"?>  
   <SetupPrereq>  
   <conditions>  
       <condition Type="32" Comparison="2" Path="HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4R" FileName="Version" ReturnValue="10.0.50903" Bits="2"></condition>  
   <condition Type="32" Comparison="2" Path="HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4R" FileName="Version" ReturnValue="10.0.50903" Bits="2"></condition>  
   </conditions>  
   <files>  
       <file LocalFile="<ISProductFolder>\SetupPrerequisites\VSTOR\vstor_redist.exe" URL="http://download.microsoft.com/download/C/0/0/C001737F-822B-48C2-8F6A-CDE13B4B9E9C/vstor_redist.exe" CheckSum="88b8aa9e8c90818f98c80ac4dd998b88" FileSize=" 0,40117912"></file>  
   </files>  
   <execute file="vstor_redist.exe" returncodetoreboot="1641,3010" requiresmsiengine="1">  
   </execute>  
   <properties Id="{15965040-56BB-49B8-A88F-3525C48D9BA8}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >  
   </properties>  

   </SetupPrereq>  
   ```  

2. Generare un GUID in Visual Studio. Scegliere **Crea GUID** dal menu **Strumenti**.  

3. Nel programma **Generatore di GUID** , scegliere il pulsante di opzione **Formato del registro di sistema** , scegliere il pulsante **Copia** , quindi scegliere il pulsante **Esci** .  

4. Nel Blocco note, sostituire il testo **Your GUID goes here** incollando il GUID al suo posto.  

   Verrà visualizzata la finestra di dialogo **&lt;properties&gt;** del file è simile all'esempio seguente.  


   ```xml  
   <properties Id="{87989B73-21DC-4403-8FD1-0C68A41A6D8C}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >  
   </properties>  
   ```  

5. Nella barra dei menu nel blocco note, scegliere **File** > **salvare**.  

6. Nella finestra di dialogo **Salva con nome** selezionare la cartella **Desktop** .  

7. Nel **Salva come tipo** casella di riepilogo **tutti i file (&#42;.&#42;)** .  

8. Nella casella **Nome file** immettere **Visual Studio 2010 Tools per Office Runtime.prq**, quindi scegliere il pulsante **Salva** .  

   > [!NOTE]  
   >    Accertarsi di aggiungere **.prq** alla fine del nome file per identificare il file di prerequisiti.  

9. Chiudere il Blocco note.  

10. Dalle **Desktop** copiare il *Visual Studio 2010 Tools per Office Runtime. prq* file a una delle seguenti directory nel computer.  

   Per i sistemi operativi a 32 bit: *%ProgramFiles%\InstallShield\2013LE\SetupPrerequisites\\*  

   Per i sistemi operativi a 64 bit: *% ProgramFiles (x86) %\2013LE\SetupPrerequisites\\*  

11. Nella pagina **Ridistribuibile** del progetto InstallShield, scegliere il pulsante **Aggiorna** per aggiornare l'elenco dei componenti ridistribuibili, come mostrato nella figura seguente.  

   ![Pulsante di aggiornamento. ](../vsto/media/installshield-refreshbutton.png "Pulsante Aggiorna.")  

12. Nell'elenco di componenti ridistribuibili, selezionare la casella di controllo **Visual Studio 2010 Tools per Office Runtime** .  

   Può essere visualizzata una finestra di dialogo in cui viene chiesto se si desidera installare il componente ridistribuibile. Se non viene visualizzata questa finestra di dialogo, è possibile ignorare per il [in cui si desidera distribuire la soluzione nel computer dell'utente specificare](#Location) sezione di questo argomento.  

13. Se viene visualizzata questa finestra di dialogo, selezionare il pulsante **No** .  


## <a name="Location"></a>Specificare il percorso in cui installare la soluzione nel computer dell'utente  

1. In **Esplora soluzioni**espandere il nodo **OfficeAddInSetup** , espandere il nodo **Organizza l'installazione** , quindi selezionare il file **Informazioni generali** .  

2. Nella barra dei menu, scegliere **View** > **Open**.  

3. Nell'elenco di proprietà scegliere il pulsante **Sfoglia** accanto alla proprietà **INSTALLDIR** .  

4. Nel **imposta INSTALLDIR** finestra di dialogo scegliere una cartella nel computer dell'utente in cui si desidera installare la soluzione.  

   > [!NOTE]  
   >    È inoltre possibile creare sottodirectory nella finestra di dialogo **Imposta INSTALLDIR** aprendo il menu di scelta rapida per qualsiasi cartella dell'elenco.  


## <a name="ConfigureRegistry"></a>Configurare un componente aggiuntivo VSTO  
È possibile specificare se installare il componente aggiuntivo VSTO per tutti gli utenti del computer (per computer) o soltanto per l'utente che esegue l'installazione (per utente).  

Se si desidera supportare le installazioni per computer, creare due programmi di installazione separati. È possibile suddividere i programmi di installazione in base alla versione di Office (a 32 bit e a 64 bit) o alla versione di Windows (a 32 bit e a 64 bit) che usa l'utente.  

Le installazioni per utente richiedono un solo programma di installazione indipendentemente dalla versione di Office o Windows.  

> [!NOTE]  
> Questa sezione si applica solo se si distribuisce un componente aggiuntivo VSTO. Se si distribuisce una personalizzazione a livello di documento, è possibile passare immediatamente al [configurare una personalizzazione a livello di documento](#ConfigureDocument) sezione.  


### <a name="to-specify-whether-you-want-to-support-per-user-or-per-computer-installations"></a>Per specificare se si desidera supportare le installazioni per utente o per computer.  

1. In **Esplora soluzioni**espandere il nodo di progetto **OfficeAddInSetup** , espandere il nodo **Organizza l'installazione** , quindi selezionare il file **Informazioni generali** .  

2. Nella barra dei menu, scegliere **View** > **Open**.  

   Vengono visualizzate le proprietà del progetto di installazione.  

3. Nell'elenco per la proprietà **AllUSERS** specificare se si desidera che questa soluzione venga installata per tutti gli utenti del computer o solo per l'utente che installa la soluzione.  

   Per installare il componente aggiuntivo VSTO per l'utente corrente, scegliere **ALLUSERS = "" (installazione Per utente)**. Per installare il componente aggiuntivo VSTO per tutti gli utenti del computer, scegliere **ALLUSERS=1 (installazione per computer)**.  

   Nella procedura successiva, si creerà le chiavi del Registro di sistema per consentire l'applicazione di Office di individuare e caricare il componente aggiuntivo VSTO. Visualizzare [voci del Registro di sistema per componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  


### <a name="to-create-registry-keys"></a>Per creare chiavi del Registro di sistema  

1. In **Esplora soluzioni**scegliere il nodo **Project Assistant** .  

   Nella barra dei menu, scegliere **View** > **Open**.  

2. Nella parte inferiore della pagina **Project Assistant** , scegliere il pulsante **Registro di sistema dell'applicazione** mostrato nell'immagine seguente.  

   ![Il pulsante di applicazione del Registro di sistema. ](../vsto/media/installshield-applicationregistry.gif "Pulsante dell'applicazione del Registro di sistema.")  

   Viene visualizzata la pagina **Registro di sistema dell'applicazione** .  

3. In **Si desidera configurare i dati del Registro di sistema che verranno installati dall'applicazione?** scegliere il pulsante di opzione **Sì** .  

4. Nel **visualizzazione del Registro di sistema del computer di destinazione** elencare, aggiungere la gerarchia principale che attiva il tipo di programma di installazione che si desidera creare.  

   Il percorso che si configura in questa sezione varia se si crea un programma di installazione per utente o un programma di installazione per computer.  

   **Programma di installazione per utente**  

   **HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**  

   **Programmi di installazione per computer in base alla versione di Office**  



| Versione di Office<br /><br /> | Percorso di configurazione di InstallShield<br /><br /> |
|----------------------------| - |
| 32 bit<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64 bit<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(64-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   **Programmi di installazione per computer in base alla versione di Windows**  



| Versione di Windows<br /><br /> | Percorso di configurazione di InstallShield<br /><br /> |
|-----------------------------| - |
| 32 bit<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64 bit<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />**HKEY_LOCAL_MACHINE\SOFTWARE(64-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   > [!NOTE]  
   >    Un programma di installazione per Windows a 64 bit richiede due percorsi del Registro di sistema perché è possibile che agli utenti di eseguire le versioni a 32 e 64 bit di Office in un computer che esegue Windows a 64 bit.  

   > [!NOTE]  
   >    È buona norma che il nome del componente aggiuntivo VSTO inizi con il nome della società. Questa convenzione aumenta la probabilità che la chiave sia univoca e riduce la possibilità di conflitto con un componente aggiuntivo VSTO da un altro fornitore. I componenti aggiuntivi con lo stesso nome possono, ad esempio, sovrascrivere i rispettivi codici di registrazione. Questo approccio non può garantire che la chiave sia univoca ma può ridurre i potenziali conflitti di denominazione.  

5. Dopo aver creato la gerarchia delle chiavi, aprire il menu di scelta rapida per il **samplecompany. ExcelAddIn** chiave, scegliere **New**, quindi scegliere **valore stringa**.  

   Il nuovo valore stringa viene visualizzato nella **i dati del Registro di sistema del computer di destinazione** elenco. Il nome del valore stringa è evidenziato in modo che sia possibile rinominarlo.  

6. Rinominare il valore in **Descrizione**.  

7. Ripetere la procedura per creare i seguenti valori:  



|Tipo di valore<br /><br />|Nome<br /><br />|  
|--------------|--------|  
|Valore stringa<br /><br />|**FriendlyName**<br /><br />|  
|Valore DWORD<br /><br />|**LoadBehavior**<br /><br />|  
|Valore stringa<br /><br />|**Manifesto**<br /><br />|  

8. Aprire il menu di scelta rapida per il valore **Descrizione** , quindi scegliere **Modifica**.  

   Viene visualizzata la finestra di dialogo **Modifica dati** .  

9. Nella casella di testo **Dati valore** immettere **Componente aggiuntivo Demo Excel**, quindi scegliere il pulsante **OK** .  

   Questa descrizione viene visualizzata quando l'utente apre l'applicazione di Office, apre la finestra di dialogo **Opzioni** e quindi sceglie il componente aggiuntivo VSTO nel riquadro **Componenti aggiuntivi** .  

10. Aprire il menu di scelta rapida per il valore **FriendlyName** , quindi scegliere **Modifica**.  

   Viene visualizzata la finestra di dialogo **Modifica dati** .  

11. Nella casella di testo **Dati valore** immettere **Componente aggiuntivo Demo Excel**, quindi scegliere il pulsante **OK** .  

   Questa stringa viene visualizzata nella finestra di dialogo **Componenti aggiuntivi COM** nell'applicazione di Office. Per impostazione predefinita, il valore della stringa è l'ID del componente aggiuntivo VSTO.  

12. Aprire il menu di scelta rapida per il valore **LoadBehavior** , quindi scegliere **Modifica**.  

   Viene visualizzata la finestra di dialogo **Modifica dati** .  

13. Nella casella di testo **Dati valore** immettere **3**, quindi scegliere il pulsante **OK** .  

   Il valore 3 carica il componente aggiuntivo VSTO all'avvio dell'applicazione. Per altre informazioni sui valori LoadBehavior, vedere [voci del Registro di sistema per componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  

14. Aprire il menu di scelta rapida per il valore **Manifesto** , quindi scegliere **Modifica**.  

   Viene visualizzata la finestra di dialogo **Modifica dati** .  

15. Nella casella di testo **Dati valore** immettere **file:///[INSTALLDIR]ExcelAddIn.vsto|vstolocal**, quindi scegliere il pulsante **OK** .  

   Visual Studio 2010 Tools per Office Runtime usa questo percorso per individuare il manifesto di distribuzione. La parte **[INSTALLDIR]** di questo percorso è una macro che esegue il mapping alla proprietà **INSTALLDIR** nella pagina delle proprietà **Informazioni generali** del progetto di installazione di InstallShield. Questa proprietà specifica il percorso nel computer di destinazione per installare il componente aggiuntivo VSTO. Il suffisso **|vstolocal** garantisce che la soluzione venga caricata dalla cartella di installazione anziché dalla cache ClickOnce.  

> [!IMPORTANT]  
> Se si crea un'area del modulo personalizzata in un componente aggiuntivo VSTO per Outlook, è necessario creare altre voci del Registro di sistema per registrare l'area con Outlook. Per altre informazioni, vedere [aree del modulo le voci del Registro di sistema per Outlook](../vsto/registry-entries-for-vsto-add-ins.md#OutlookEntries).  


## <a name="ConfigureDocument"></a>Configure a document-level customization  
In questa sezione si applica solo se si distribuisce una personalizzazione a livello di documento. Se si distribuisce un componente aggiuntivo VSTO, è possibile passare immediatamente al [compila il progetto di installazione](#Build) sezione.  

Le personalizzazioni a livello di documento non usano le chiavi del Registro di sistema. Al contrario, le proprietà del documento personalizzate contengono la posizione del manifesto di distribuzione.  

Per modificare le proprietà personalizzate, si crea un programma che rimuove la personalizzazione a livello di documento dal documento, modifica le proprietà appropriate e quindi ricollega personalizzazione al documento. Occorre quindi creare un'azione personalizzata che esegue il programma e aggiungere tale azione al progetto di installazione.  

### <a name="to-create-a-program-that-modifies-document-properties"></a>Per creare un programma che modifica le proprietà del documento  

1. Nella barra dei menu, scegliere **File** > **Add** > **nuovo progetto**.  

   Verrà visualizzata la finestra di dialogo **Aggiungi nuovo progetto** .  

2. Nel riquadro dei modelli nel nodo per il linguaggio che si desidera usare, scegliere la cartella **Windows** .  

3. Nell'elenco dei tipi di progetto per **Windows**, scegliere il modello **Applicazione console** .  

4. Assegnare il nome **SetExcelDocumentProperties**al progetto, quindi selezionare il pulsante **OK** .  

5. In **Esplora soluzioni**, selezionare il pulsante **Mostra tutti i file** , aprire il menu di scelta rapida per il nodo di progetto **SetExcelDocumentProperties** , quindi scegliere **Aggiungi riferimento**.  

6. Nella finestra di dialogo **Gestione riferimenti** scegliere la scheda **Estensioni** , quindi selezionare la casella di controllo accanto agli assembly seguenti, quindi scegliere il pulsante **OK** .  


   - Microsoft.VisualStudio.Tools.Applications.Runtime  

   - Microsoft.VisualStudio.Tools.Applications.ServerDocument  

7. In **Esplora soluzioni**, scegliere il file **Program.cs** (per le applicazioni C#) o il file **Module1.vb** (per le applicazioni Visual Basic).  

8. Nella barra dei menu, scegliere **View** > **Open**.  

9. Sostituire tutti i contenuti dell'intero file con il codice seguente.  

[!code-vb[Trin_CustomAction#1](../vsto/codesnippet/VisualBasic/setexceldocumentproperties/module1.vb#1)]
[!code-csharp[Trin_CustomAction#1](../vsto/codesnippet/CSharp/setexceldocumentproperties/program.cs#1)]  

10. Compilare il progetto.  


### <a name="to-add-a-custom-action-that-runs-your-program"></a>Per aggiungere un'azione personalizzata che esegue il programma  

1. In **Esplora soluzioni**, espandere il nodo del progetto **OfficeAddInSetup** , quindi scegliere il file **Project Assistant** illustrato nell'immagine seguente.  

   ![Project Assistant File in Esplora soluzioni](../vsto/media/installshield-projectassistant.png "Project Assistant File in Esplora soluzioni")  

2. Nella barra dei menu, scegliere **View** > **Open**.  

3. Nella parte inferiore della pagina **Project Assistant** , scegliere il pulsante **File applicazione** mostrato nell'immagine seguente.  

   ![Il pulsante con i file dell'applicazione. ](../vsto/media/installshield-applicationfiles.png "Pulsante il file dell'applicazione.")  

4. Nella pagina **File applicazione** selezionare il pulsante **Aggiungi output progetto** .  

   Verrà aperta la finestra di dialogo **Selettore output di Visual Studio** .  

5. Nel nodo **SetExcelDocumentProperties** , selezionare la casella di controllo **Output primario** , quindi scegliere il pulsante **OK** .  

6. In **Esplora soluzioni**, nel nodo **OfficeAddInSetup** , espandere il nodo **Definisci azioni e requisiti di installazione** , quindi selezionare la cartella **Azioni personalizzate** .  

7. Nella barra dei menu, scegliere **View** > **Open**.  

   Verrà visualizzato un elenco di eventi in un riquadro laterale dello schermo.  

   > [!NOTE]  
   >    Solo alcuni eventi visualizzati in questo elenco sono disponibili in InstallShield Limited Edition. In questa procedura verrà eseguito il programma usando il **finestra di dialogo programma di installazione avvenuto completamento** evento.  

8. Nell'elenco di eventi, in **Azioni personalizzate durante l'installazione**, aprire il menu di scelta rapida per l'evento **Finestra di dialogo di avvenuto completamento dell'installazione** , quindi scegliere **Nuovo EXE**.  

   Un'azione personalizzata denominata **NewCustomAction1** verrà visualizzata nell'evento **Finestra di dialogo di avvenuto completamento dell'installazione** . Un set di proprietà per l'azione personalizzata viene visualizzato in un riquadro accanto agli eventi.  

   > [!IMPORTANT]  
   >    Due eventi **Finestra di dialogo di avvenuto completamento dell'installazione** vengono visualizzati nell'elenco degli eventi. Verificare di aver selezionato l'istanza dell'evento **Finestra di dialogo di avvenuto completamento dell'installazione** che viene visualizzato nel nodo **Azioni personalizzate durante l'installazione** .  

9. Nell'elenco per la proprietà **Percorso di origine** , scegliere **Installato con il prodotto**.  

10. Selezionare il pulsante **Sfoglia** accanto alla proprietà **Nome file** .  

11. Nella finestra di dialogo **Cerca file di destinazione** , individuare il file **SetExcelDocumentProperties.Primary.output** , quindi scegliere il pulsante **Apri** .  

    Il percorso del file dipende dalla cartella specificata per la proprietà **INSTALLDIR** del progetto di installazione. Ad esempio, se si imposta tale proprietà su una cartella denominata **[PersonalFolder]DemoWorkbookApp**, è possibile trovare il file **SetExcelDocumentProperties.Primary.output** cercando in **[ProgramFilesFolder]\DemoWorkbookApp**.  

    In passaggi successivi, si ottiene l'ID soluzione del documento e si passerà tale ID come parametro per l'applicazione console. Inoltre, si passerà il percorso del documento, il manifesto di distribuzione e l'assembly del documento.  

12. Aprire il menu di scelta rapida per il progetto **ExcelWorkbook** , quindi scegliere **Apri cartella in Esplora risorse** o **Apri cartella in Esplora file** in base al sistema operativo.  

    Verrà aperta la cartella che contiene la soluzione.  

13. Aprire il file di progetto della soluzione nel Blocco note. Per i progetti di Visual Basic, è il nome del file *ExcelWorkbook*. Per i progetti c#, è il nome del file *ExcelWorkbook*.  

14. Nel file di progetto, cercare il **&lt;SolutionID&gt;** elemento, copiare il valore negli Appunti e quindi chiudere Blocco note.  

    Passare questo valore nell'applicazione console come parametro.  

15. Nella pagina delle proprietà di **NewCustomAction1**impostare la proprietà **Riga di comando** nella seguente riga di testo.  


   ```cmd
   /assemblyLocation="[INSTALLDIR]ExcelWorkbook.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbook.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbook.xlsx" /solutionID="Your Solution ID"  
   ```  

16. Sostituire **Your Solution ID** con l'ID soluzione copiato negli Appunti.  

   > [!IMPORTANT]  
   >    Testare il programma di installazione per verificare che l'applicazione console eseguita da questa azione personalizzata possa accedere ai documenti nella directory [INSTALLDIR]. Alcune directory nel computer dell'utente potrebbe richiedere l'accesso amministrativo (ad esempio, la directory di file di programma). Se si distribuisce la soluzione in una directory che richiede accesso amministrativo, è necessario aprire il **delle proprietà** della finestra di dialogo il *setup.exe* file, scegliere il **compatibilità** scheda e quindi selezionare il **Esegui questo programma come amministratore** casella di controllo prima di distribuire il programma di installazione. Se non si desidera che gli utenti eseguano il programma di installazione con autorizzazioni amministrative, impostare la proprietà [INSTALLDIR] su una directory a cui l'utente ha probabilmente accesso già, ad esempio la **documenti** directory. Per altre informazioni, vedere la [specificare dove si desidera installare la soluzione nel computer dell'utente](#Location) sezione di questo argomento.  


## <a name="Build"></a>Build the setup project  

1. In **Esplora soluzioni**espandere il nodo **Preparare la versione** , quindi selezionare il file **Versioni** .  

2. Nella barra dei menu, scegliere **View** > **Open**.  

   In un riquadro laterale viene visualizzato Esplora **compilazioni** in cui è possibile scegliere il tipo di versione che si desidera creare.  

3. In Esplora **compilazioni** scegliere la cartella **SingleImage** .  

4. Nel riquadro accanto a Esplora **compilazioni** , scegliere la scheda **Setup.exe** .  

5. Nella pagina delle proprietà **Setup.exe** , dall'elenco **Percorso prerequisiti InstallShield** , scegliere **Scarica dal Web**.  

6. Nella barra dei menu scegliere **Compilazione** > **Gestione configurazione**.  

7. Nell'elenco **Configurazione soluzione attiva** , scegliere **SingleImage**.  

8. Nella colonna **Configurazione** della tabella **Contesti progetto** all'interno del progetto **OfficeAddInSetup** , scegliere **SingleImage**, quindi fare clic sul pulsante **Chiudi** .  

9. Nella barra dei menu, scegliere **compilare** > **compila OfficeAddInSetup**.  

   Dopo il completamento della compilazione, è possibile individuare il *setup.exe* file del **OfficeAddInSetup** progetto nel percorso seguente: <em>OfficeAddInSetupProjectRoot</em>**\OfficeAddInSetup\Express\SingleImage\DiskImages\DISK1\\**  


## <a name="see-also"></a>Vedere anche  
[Prerequisiti per la distribuzione di soluzioni Office](https://msdn.microsoft.com/library/9f672809-43a3-40a1-9057-397ce3b5126e)  
[Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)  
[Voci del Registro di sistema per componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md)  
[Cenni preliminari sulle proprietà personalizzate dei documenti](../vsto/custom-document-properties-overview.md)  
[Concedere l'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)  
[Concedere l'attendibilità ai documenti](../vsto/granting-trust-to-documents.md)  
[Distribuire un Visual Studio 2010 Tools per la soluzione Office mediante il programma di installazione di Windows](http://go.microsoft.com/fwlink/?LinkId=201807)  
