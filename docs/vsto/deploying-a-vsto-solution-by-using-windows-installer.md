---
title: Distribuzione di una soluzione Visual Studio Tools per Office utilizzando Windows InstallerDeploying a Visual Studio Tools for Office Solution Using Windows Installer
ms.date: 08/18/2010
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
ms.openlocfilehash: 46bfa808cbf99e942d7aadd2802f51eecfcefae8
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444906"
---
# <a name="deploying-a-visual-studio-tools-for-office-solution-using-windows-installer"></a>Distribuzione di una soluzione Visual Studio Tools per Office utilizzando Windows InstallerDeploying a Visual Studio Tools for Office Solution Using Windows Installer

## <a name="summary"></a>Summary

Informazioni su come distribuire un componente aggiuntivo di Microsoft Visual Studio Tools per Office (VSTO) o una soluzione a livello di documento usando un progetto di installazione di Visual Studio.Learn how to deploy a Microsoft Visual Studio Tools for Office (VSTO) add-in or document-level solution using a Visual Studio Installer project.

Wouter van Vugt, Code Counsel

Ted Pattison, Gruppo Ted Pattison

Questo articolo è stato aggiornato da Microsoft con l'autorizzazione degli autori originali.

**Si applica a:** Visual Studio Tools per Office, Microsoft Office, Microsoft Visual Studio.

## <a name="overview"></a>Panoramica

È possibile sviluppare una soluzione VSTO e distribuire la soluzione utilizzando un pacchetto di Windows Installer.You can develop a VSTO solution and deploy the solution by using a Windows Installer package. Questa discussione include i passaggi per la distribuzione di un semplice componente aggiuntivo di Office.

## <a name="deployment-methods"></a>Metodi di distribuzione

ClickOnceClickOnce può essere facilmente utilizzato per creare configurazioni per i componenti aggiuntivi e soluzioni. Tuttavia, non è possibile installare componenti aggiuntivi che richiedono privilegi amministrativi, ad esempio componenti aggiuntivi a livello di computer.

I componenti aggiuntivi che richiedono privilegi amministrativi possono essere installati utilizzando Windows Installer, ma richiede uno sforzo maggiore per creare l'installazione.

Per una panoramica su come distribuire una soluzione VSTO utilizzando ClickOnceClickOnce, vedere [Distribuire una soluzione Office tramite ClickOnce](deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Distribuzione di soluzioni Office destinate al runtime VSTODeploying Office solutions that target the VSTO runtime

I pacchetti ClickOnce e Windows Installer devono eseguire le stesse attività rudimentali durante l'installazione di una soluzione Office.

1. Installare i componenti prerequisiti nel computer dell'utente.
2. Distribuire i componenti specifici per la soluzione.
3. Per i componenti aggiuntivi, creare voci del Registro di sistema.
4. Considerare attendibile la soluzione per consentirne l'esecuzione.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Componenti prerequisiti necessari nel computer di destinazione

Ecco l'elenco dei software che devono essere installati nel computer per eseguire soluzioni VSTO:

- Microsoft Office 2010 o versione più recente.
- Microsoft .NET Framework 4 o versione più recente.
- Microsoft Visual Studio 2010 Tools per Office Runtime.
  Il runtime fornisce un ambiente che gestisce i componenti aggiuntivi e le soluzioni a livello di documento. Una versione del runtime viene distribuita con Microsoft Office, ma è possibile ridistribuire una versione specifica con il componente aggiuntivo.
- Assembly di interoperabilità primario per Microsoft Office, se non si utilizzano tipi di interoperabilità incorporati.
- Tutti gli assembly di utilità a cui fanno riferimento i progetti.

### <a name="specific-components-for-the-solution"></a>Componenti specifici per la soluzione

Il pacchetto di installazione deve installare questi componenti nel computer dell'utente:

- Il documento di Microsoft Office, se si crea una soluzione a livello di documento.
- L'assembly di personalizzazione e tutti gli assembly necessari.
- Componenti aggiuntivi, ad esempio i file di configurazione.
- Manifesto dell'applicazione (manifest).
- Manifesto di distribuzione (.vsto).

### <a name="registry-entries-for-add-ins"></a>Voci del Registro di sistema per i componenti aggiuntiviRegistry Entries for Add-ins

Microsoft Office utilizza le voci del Registro di sistema per individuare e caricare i componenti aggiuntivi. Queste voci del Registro di sistema devono essere create come parte del processo di distribuzione. Per altre informazioni su queste voci del Registro di sistema, vedere Voci del Registro di sistema per i componenti [aggiuntivi VSTO.](registry-entries-for-vsto-add-ins.md)

Componenti aggiuntivi di Outlook che visualizzano aree del modulo personalizzate richiedono voci del Registro di sistema aggiuntive che consentono di identificare le aree del modulo. Per ulteriori informazioni sulle voci del Registro di sistema, vedere [Voci del Registro di sistema per le aree del modulo](registry-entries-for-vsto-add-ins.md#OutlookEntries)di Outlook .

Le soluzioni a livello di documento non richiedono alcuna voce del Registro di sistema. Al contrario, le proprietà all'interno del documento vengono utilizzate per individuare la personalizzazione. Per ulteriori informazioni su queste proprietà, vedere [Cenni preliminari](custom-document-properties-overview.md)sulle proprietà personalizzate dei documenti .

### <a name="trusting-the-vsto-solution"></a>Fiducia nella soluzione VSTO

Affinché una personalizzazione venga eseguita, una soluzione deve essere considerata attendibile dal computer. Il componente aggiuntivo può essere considerato attendibile firmando il manifesto con un certificato, creando una relazione di trust con un elenco di inclusione o installandolo in un percorso attendibile nel computer.

Per ulteriori informazioni su come ottenere un certificato per la firma, vedere [ClickOnce Deployment e Authenticode](../deployment/clickonce-and-authenticode.md). Per ulteriori informazioni sull'attendibilità di soluzioni, vedere [Trusting Office Solutions by Using Inclusion Lists](trusting-office-solutions-by-using-inclusion-lists.md). È possibile aggiungere una voce dell'elenco di inclusione con un'azione personalizzata nel file di Windows Installer. Per ulteriori informazioni sull'abilitazione dell'elenco di inclusione, vedere [Procedura: Configurare la protezione dell'elenco di inclusione](how-to-configure-inclusion-list-security.md).

Se non viene utilizzata alcuna opzione, viene visualizzata una richiesta di attendibilità per consentire loro di decidere se considerare attendibile la soluzione.

Per ulteriori informazioni sulla sicurezza relativa alle soluzioni a livello di documento, vedere [Concessione dell'attendibilità ai documenti](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Creazione di un programma di installazione di baseCreating a Basic Installer

I modelli di progetto di installazione e distribuzione sono inclusi con l'estensione Progetti di installazione di [Microsoft Visual Studio](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) disponibile per il download.

Per creare un programma di installazione per una soluzione Office, è necessario eseguire queste attività:To create an installer for an Office solution, these tasks must be accomplished:

- Aggiungere i componenti della soluzione Office che verranno distribuiti.
- Per i componenti aggiuntivi a livello di applicazione, configurare le chiavi del Registro di sistema.
- Configurare i componenti prerequisiti in modo che possano essere installati nei computer degli utenti finali.
- Configurare le condizioni di avvio per verificare che i componenti prerequisiti necessari siano disponibili. Le condizioni di avvio possono essere utilizzate per bloccare l'installazione se non sono installati tutti i prerequisiti necessari.

Il primo passaggio consiste nel creare il progetto di installazione.

### <a name="to-create-the-addin-setup-project"></a>Per creare il progetto AddIn Setup

1. Aprire il progetto Componente aggiuntivo di Office che si desidera distribuire. Per questo esempio, si usa un componente aggiuntivo di Excel denominato ExcelAddIn.For this example, we're using an Excel Add-in called ExcelAddIn.
2. Con Office Project Open, scegliere **Aggiungi** dal menu **File** e fare clic su **Nuovo progetto** per aggiungere un nuovo progetto.
::: moniker range="=vs-2017"
3. Nella finestra di dialogo **Aggiungi nuovo progetto** espandere Altri tipi di **progetto** nel riquadro **Tipi** progetto, quindi espandere Installazione **e distribuzione** e selezionare Programma di installazione di **Visual Studio**.
4. Nel riquadro Modelli selezionare **Progetto di installazione** dal gruppo Modelli installati di Visual Studio.In the **Templates** pane, select Setup Project from the **Visual Studio installed** templates group.
::: moniker-end
::: moniker range="=vs-2019"
3. Nella finestra di dialogo **Aggiungi nuovo progetto** selezionare il modello Imposta **progetto.**
4. Fare clic su **Avanti**.
::: moniker-end

5. Nella casella **Nome** digitare **OfficeAddInSetup**.
::: moniker range="=vs-2017"
6. Fare clic su **Apri** per creare il nuovo progetto di impostazione.
::: moniker-end
::: moniker range="=vs-2019"
6. Fare clic su **Crea** per creare il nuovo progetto di impostazione.
::: moniker-end

Visual Studio apre Esplora risorse del file system per il nuovo progetto di installazione. Esplora risorse file system consente di aggiungere file al progetto di installazione.

   ![Screenshot di Esplora sistema per il progetto di installazione](media/setup-project-figure-1.png)

   **Figura 1: Esplora sistema di file system per il progetto di installazione**

The setup project needs to deploy the ExcelAddIn. È possibile configurare il progetto di installazione per questa attività aggiungendo l'output del progetto ExcelAddIn al progetto di installazione.

### <a name="to-add-the-exceladdin-project-output"></a>Per aggiungere l'output del progetto ExcelAddIn

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **OfficeAddInSetup**, **scegliere Aggiungi,** quindi **Output progetto**.
2. Nella finestra di dialogo **Aggiungi gruppo output progetto** selezionare **ExcelAddIn** dall'elenco dei progetti e **Output primario**.
3. Fare clic **su OK** per aggiungere l'output del progetto al progetto di installazione.

    ![Screenshot della finestra di dialogo Imposta gruppo di output progetto Aggiungi gruppo output progetto](media/setup-project-figure-2.png)

    **Figura 2: finestra di dialogo Imposta gruppo output progetto aggiungi progetto**

Il progetto di installazione deve distribuire il manifesto di distribuzione e il manifesto dell'applicazione. Aggiungere questi due file al progetto di installazione come file autonomi dalla cartella di output del progetto ExcelAddIn.

### <a name="to-add-the-deployment-and-application-manifests"></a>Per aggiungere i manifesti di distribuzione e applicazione

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **OfficeAddInSetup**, **scegliere Aggiungi**, quindi **File**.
2. Nella finestra di dialogo **Aggiungi file** passare alla directory di output di **ExcelAddIn.** In genere la directory di output è la sottocartella **bin\\release** della directory radice del progetto, a seconda della configurazione di compilazione selezionata.
3. Selezionare i file **ExcelAddIn.vsto** e **ExcelAddIn.dll.manifest** e fare clic su **Apri** per aggiungere questi due file al progetto di installazione.

    ![Screenshot dei manifesti dell'applicazione e della distribuzione in Esplora soluzioni](media/setup-project-figure-3.jpg)

    **Figura 3: Manifesti di applicazione e distribuzione per il componente aggiuntivo in Esplora soluzioniFigure 3: Application and deployment manifests for the Add-in in Solution Explorer**

Il riferimento a ExcelAddIn include tutti i componenti necessari per ExcelAddIn. Questi componenti devono essere esclusi e distribuiti utilizzando pacchetti prerequisiti per consentirne la corretta registrazione. Inoltre, le Condizioni di licenza software devono essere visualizzate e accettate prima dell'inizio dell'installazione.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>Per escludere le dipendenze del progetto ExcelAddInTo exclude the ExcelAddIn project dependencies

1. In **Esplora soluzioni**, nel nodo **OfficeAddInSetup** , selezionare tutti gli elementi di dipendenza al di sotto dell'elemento **Dipendenze rilevate,** ad eccezione di **Microsoft .NET Framework** o di qualsiasi assembly che termina con ** \*. Utilities.dll**. Gli assembly di utilità devono essere distribuiti insieme all'applicazione.
2. Fare clic con il pulsante destro del mouse sul gruppo e scegliere **Proprietà**.
3. Nella finestra **Proprietà** modificare la proprietà **Exclude** su **True** per escludere gli assembly dipendenti dal progetto di installazione. Assicurarsi di non escludere alcun assembly di utilità.

    ![Screenshot di Esplora soluzioni che mostra le dipendenze da escludere](media/setup-project-figure-4.jpg)

    **Figura 4: Esclusione delle dipendenze**

È possibile configurare il pacchetto di Windows Installer per installare i componenti prerequisiti aggiungendo un programma di installazione, noto anche come programma di avvio automatico. Questo programma di installazione può installare i componenti prerequisiti, un processo chiamato bootstrap.

Per **L'ExcelAddIn,** questi prerequisiti devono essere installati prima che il componente aggiuntivo possa essere eseguito correttamente:

- Versione di Microsoft .NET Framework di destinazione della soluzione Office.
- Microsoft Visual Studio 2010 Tools per Office Runtime.

Per configurare i componenti dipendenti come prerequisiti

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto **OfficeAddInSetup** e scegliere **Proprietà**.
2. Verrà visualizzata la finestra di dialogo **Pagine delle proprietà OfficeAddInSetup.**
3. Fare clic sul **pulsante Prerequisiti.**
4. Nella finestra di dialogo Prerequisiti selezionare la versione corretta di .NET Framework e Microsoft Visual Studio Tools per Office Runtime.

    ![Screenshot della finestra di dialogo Prerequisiti](media/setup-project-figure-5.png)

    **Figura 5: Finestra di dialogo Prerequisiti**

    > [!NOTE]
    >Alcuni dei pacchetti dei prerequisiti configurati nel progetto di installazione di Visual Studio dipendono dalla configurazione di compilazione selezionata. È necessario selezionare i componenti dei prerequisiti corretti per ogni configurazione di compilazione utilizzata.

Microsoft Office individua i componenti aggiuntivi utilizzando le chiavi del Registro di sistema. Le chiavi nell'hive HKEY\_CURRENT\_USER vengono utilizzate per registrare il componente aggiuntivo per ogni singolo utente. Le chiavi nell'hive HKEY\_LOCAL\_MACHINE vengono utilizzate per registrare il componente aggiuntivo per tutti gli utenti del computer. Per altre informazioni sulle chiavi del Registro di sistema, vedere Voci del Registro di sistema per i componenti [aggiuntivi VSTO.](registry-entries-for-vsto-add-ins.md)

### <a name="to-configure-the-registry"></a>Per configurare il Registro di sistema

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **OfficeAddInSetup**.
2. Espandere **Visualizza**.
3. Fare clic su **Registro** di sistema per aprire la finestra dell'editor del Registro di sistema.
4. Nell'editor Registro di **sistema (OfficeAddInSetup),** espandere **HKEY\_LOCAL\_MACHINE** e quindi **Software**.
5. Eliminare ** \[la\]chiave del produttore**?chiave trovata in **HKEY\_LOCAL\_\\MACHINE Software**.
6. Espandere **\_HKEY\_CURRENT USER** e quindi **Software**.
7. Eliminare ** \[la\] ** chiave Produttore trovata in **HKEY\_CURRENT\_USER\\Software**.
8. Per aggiungere chiavi del Registro di sistema per l'installazione del componente aggiuntivo, fare clic con il pulsante destro del mouse sulla chiave **User/Machine Hive,** selezionare **New Key**. Utilizzare il testo **Software** per il nome della nuova chiave. Fare clic con il pulsante destro del mouse sulla chiave **Software** appena creata e creare una nuova chiave con il testo **Microsoft**.
9. Utilizzare un processo simile per creare l'intera gerarchia di chiavi necessaria per la registrazione del componente aggiuntivo:Use a similar process to create the entire key hierarchy required for the add-in registration:

    **User/Machine Hive\\Software\\Microsoft\\Office\\Excel\\Addins\\SampleCompany.ExcelAddIn**

    Il nome della società viene spesso utilizzato come prefisso per il nome del componente aggiuntivo per fornire univocità.

10. Fare clic con il pulsante destro del mouse sulla chiave **SampleCompany.ExcelAddIn** , scegliere **Nuovo**e fare clic su **Valore stringa**. Utilizzare il testo **Descrizione** per il nome.
11. Utilizzare questo passaggio per aggiungere altri tre valori:Use this step to add three more values:
    - **FriendlyName** di tipo **String**
    - **LoadBehavior** di tipo **DWORD**
    - **Manifesto** di tipo **StringManifest** of type String

12. Fare clic con il pulsante destro del mouse sul valore **Description** nell'editor del Registro di sistema e **scegliere Finestra Proprietà**. Nella **finestra Proprietà**immettere **Excel Demo AddIn** per la proprietà Value .
13. Selezionare la chiave **FriendlyName** nell'editor del Registro di sistema. Nella **finestra Proprietà**modificare la proprietà **Value** in Excel **Demo AddIn**.
14. Selezionare la chiave **LoadBehavior** nell'editor del Registro di sistema. Nella **finestra Proprietà**modificare la proprietà **Value** su **3.** Il valore 3 per LoadBehavior indica che il componente aggiuntivo deve essere caricato all'avvio dell'applicazione host. Per altre informazioni sul comportamento di caricamento, vedere Voci del Registro di sistema per i componenti [aggiuntivi VSTO.](registry-entries-for-vsto-add-ins.md)

15. Selezionare la chiave **Manifest** nell'editor del Registro di sistema. Nella **finestra Proprietà**, modificare la proprietà **Value** in **file:///[TARGETDIR]ExcelAddIn.vsto**

    ![Screenshot dell'Editor del Registro di sistema](media/setup-project-figure-6.png)

    **Figura 6: Impostazione delle chiavi del Registro di sistema**

      Il runtime VSTO utilizza questa chiave del Registro di sistema per individuare il manifesto di distribuzione. La macro [TARGETDIR] verrà sostituita con la cartella in cui è installato il componente aggiuntivo. La macro includerà il carattere finale , pertanto il nome del file del manifesto di distribuzione deve essere ExcelAddIn.vsto senza il carattere .
      Il suffisso **vstolocal** indica al runtime VSTO che il componente aggiuntivo deve caricare da questa posizione anziché dalla cache ClickOnce. La rimozione di questa suffissa causerà il runtime per copiare la personalizzazione nella cache ClickOnce.

   >[!WARNING]
   >È necessario prestare molta attenzione con l'Editor del Registro di sistema in Visual Studio.You should be careful with the Registry Editor in Visual Studio. Ad esempio, se si imposta accidentalmente DeleteAtUninstall per la chiave errata, è possibile eliminare una parte attiva del Registro di sistema, lasciando il computer dell'utente in uno stato incoerente o peggio ancora rotto.

Le versioni a 64 bit di Office utilizzeranno l'hive del Registro di sistema a 64 bit per cercare i componenti aggiuntivi. Per registrare i componenti aggiuntivi nell'hive del Registro di sistema a 64 bit, la piattaforma di destinazione del progetto di installazione deve essere impostata solo su 64 bit.

1. Selezionare il progetto **OfficeAddInSetup** in Esplora soluzioni.
2. Passare alla finestra **Proprietà** e impostare la proprietà **TargetPlatform** su **x64**.

L'installazione di un componente aggiuntivo per entrambe le versioni a 32 bit e a 64 bit di Office richiede la creazione di due pacchetti MSI separati. Uno per 32 bit e uno per 64 bit.

  ![Screenshot della finestra Proprietà che mostra la piattaforma di destinazione per la registrazione dei componenti aggiuntivi con Office a 64 bit](media/setup-project-figure-7.jpg)

  **Figura 7: Piattaforma di destinazione per la registrazione di componenti aggiuntivi con Office a 64 bitFigure 7: Target Platform for registering Add-ins with 64-bit Office**

Se il pacchetto MSI viene utilizzato per installare il componente aggiuntivo o la soluzione, è possibile che venga installato senza installare i prerequisiti necessari. È possibile utilizzare le condizioni di avvio nel file MSI per bloccare l'installazione del componente aggiuntivo se i prerequisiti non sono installati.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>Configurare una condizione di avvio per rilevare il runtime VSTOConfigure a launch condition to detect the VSTO Runtime

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **OfficeAddInSetup**.
2. Espandere **Visualizza**.
3. Fare clic su **Condizioni di avvio**.
4. Nell'editor Condizioni di **avvio (OfficeAddInSetup)** fare clic con il pulsante destro del mouse su **Requisiti nel computer**di destinazione , quindi scegliere Aggiungi condizione di **avvio del Registro**di sistema . Questa condizione di ricerca può cercare nel Registro di sistema una chiave installata dal runtime VSTO. Il valore della chiave è quindi disponibile per le varie parti del programma di installazione tramite una proprietà denominata. La condizione di avvio utilizza la proprietà definita dalla condizione di ricerca per verificare la presenza di un determinato valore.
5. Nell'editor Condizioni di **avvio (OfficeAddInSetup)** selezionare la condizione di ricerca **Cerca RegistryEntry1** , fare clic con il pulsante destro del mouse sulla condizione e **scegliere Finestra Proprietà**.

6. Nella finestra **Proprietà** impostare queste proprietà:
   1. Impostare il valore di **(Name)** su **Search for VSTO 2010 Runtime**.
   2. Modificare il valore di **Property** in **VSTORUNTIMEREDIST**.
   3. Impostare il valore di **RegKey** su **SOFTWARE\\Microsoft\\VSTO Runtime Setup\\v4R**
   4. Lasciare la proprietà **Root** impostata su **vsdrrHKLM**.
   5. Modificare la proprietà **Valore** in **Versione**.

7. Nell'editor Condizioni di **avvio (OfficeAddInSetup)** selezionare la condizione di avvio **Condizione1,** fare clic con il pulsante destro del mouse sulla condizione e scegliere **Finestra Proprietà**.
8. Nella finestra Proprietà impostare queste proprietà:
   1. Impostare **(Name)** su **Verify VSTO 2010 Runtime availability**.
   2. Modificare il valore della **condizione** **in\>VSTORUNTIMEREDIST " 10.0.30319"**
   3. Lasciare vuota la proprietà **InstallURL.**
   4. Impostare il **messaggio** su **Visual Studio 2010 Tools per Office Runtime non è installato. Eseguire Setup.exe per installare il componente aggiuntivo**.

        ![Screenshot della finestra Proprietà per la condizione di avvio Verifica disponibilità runtime](media/setup-project-figure-8.jpg)

        **Figura 8: Finestra Proprietà per la condizione di avvio Verifica disponibilità runtimeFigure 8: Properties Window for the Verify Runtime Availability launch condition**

 La condizione di avvio precedente verifica in modo esplicito la presenza del runtime VSTO quando viene installato dal pacchetto del programma di avvio automatico.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Configurare una condizione di avvio per rilevare il runtime VSTO installato da Office

1. Nell'editor Condizioni di **avvio (OfficeAddInSetup)** fare clic con il pulsante destro del mouse su **Computer di destinazione della ricerca**, quindi scegliere Aggiungi ricerca nel **Registro di sistema**.
2. Selezionare la condizione di ricerca **Cerca RegistryEntry1** , fare clic con il pulsante destro del mouse sulla condizione e **scegliere Finestra Proprietà**.
3. Nella finestra **Proprietà** impostare queste proprietà:
    1. Impostare il valore di **(Name)** su **Search for Office VSTO Runtime**.
    2. Modificare il valore di **Property** in **OfficeRuntime**.
    3. Impostare il valore di **RegKey** su **SOFTWARE\\Microsoft\\VSTO Runtime Setup\\v4**.
    4. Lasciare la proprietà **Root** impostata su **vsdrrHKLM**.
    5. Modificare la proprietà **Valore** in **Versione**.

4. Nell'editor Condizioni di **avvio (OfficeAddInSetup)** selezionare la condizione di avvio **Verifica disponibilità VSTO 2010** definito in precedenza, fare clic con il pulsante destro del mouse sulla condizione e **scegliere Finestra Proprietà**.

5. Modificare il valore della proprietà **Condition** in **VSTORUNTIMEREDIST \>-"10.0.30319" OPPURE OFFICERUNTIME\>"10.0.21022"**. I numeri di versione possono essere diversi a seconda delle versioni del runtime necessarie per il componente aggiuntivo.

    ![Screenshot della finestra Proprietà per la condizione di avvio](media/setup-project-figure-9.jpg)
  
    **Figura 9: Finestre delle proprietà per la condizione Verifica disponibilità runtime tramite Redist o Office**

Se un componente aggiuntivo è destinato a .NET Framework 4 o versione più recente, i tipi all'interno degli assembly di interoperabilità primari (PIA, Primary Interop Assemblies), a cui viene fatto riferimento, possono essere incorporati nell'assembly VSTO.

Per verificare se i tipi di interoperabilità verranno incorporati nel componente aggiuntivo eseguendo la procedura seguente:

1. Espandere il nodo Riferimenti in Esplora soluzioniExpand the References Node in Solution Explorer
2. Selezionare uno dei riferimenti PIA, ad esempio **Office**.
3. Visualizzare le finestre delle proprietà premendo F4 o selezionando Proprietà dal menu di scelta rapida Assembly.
4. Controllare il valore della proprietà **Incorpora tipi di interoperabilità**.

Se il valore è impostato su **True**, i tipi vengono incorporati ed è possibile passare alla sezione [**Per compilare il progetto**](#to-build-the-setup-project) di installazione .

Per altre informazioni, vedere Equivalenza dei tipi [e tipi di interoperabilità incorporatiFor](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types) more information, see Type Equivalence and Embedded Interop Types

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Per configurare le condizioni di avvio per rilevare tale per gli interoperabili utente di Office

1. Nell'editor Condizioni di **avvio (OfficeAddInSetup)** fare clic con il pulsante destro del mouse su **Requisiti nel computer**di destinazione , quindi scegliere Aggiungi condizione di **avvio**di Windows Installer . Questa condizione di avvio cerca un assembly di interoperabilità utente di Office cercando l'ID componente specifico.
2. Fare clic con il pulsante destro del mouse su **Cerca Componente1** e **scegliere Finestra Proprietà** per visualizzare le proprietà della condizione di avvio.
3. Nella **finestra Proprietà**impostare le proprietà seguenti:

    1. Modificare il valore della proprietà **(Nome)** in **Cerca PIA condiviso di Office**
    2. Modificare il valore di **ComponentID** in ID componente per il componente di Office in uso. È possibile trovare l'elenco degli ID dei componenti nella tabella seguente, ad esempio **: 64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4**.
    3. Modificare il valore della proprietà **Property** in **HASSHAREDPIA**.

4. Nell'editor Condizioni di **avvio (OfficeAddInSetup)** fare clic con il pulsante destro del mouse su **Condition1** e **scegliere Finestra Proprietà** per visualizzare le proprietà della condizione di avvio.

5. Modificare queste proprietà di **Condition1**:

    1. Modificare il **(Nome)** in **Verifica disponibilità PIA condiviso**di Office .
    2. Modificare la **condizione** **in HASSHAREDPIA**.
    3. Lasciare vuoto **InstallUrl.**
    4. Modificare il **messaggio** in **un componente necessario per l'interazione con Excel non è disponibile. Eseguire setup.exe**.

    ![Screenshot della finestra Proprietà per la condizione di avvio Verifica office Shared](media/setup-project-figure-10.jpg)
  
    **Figura 10: Finestra delle proprietà per la condizione di avvio Verifica dell'ANI condivisa di OfficeFigure 10: Properties Window for the Verify Office Shared PIA launch condition**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>GLI DLL dei componenti degli assembly di interoperabilità primari per Microsoft Office

|Assembly di interoperabilità primario|Office 2010|Office 2013|Office 2013 (64 bit)|Office 2016|Office 2016 (64 bit)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|EA7564AC-C67D-4868-BE5C-26E4FC2223FF|C8A65ABE-3270-4FD7-B854-50C8082C8F39|E3BD1151-B9CA-4D45-A77E-51A6E0ED322A|C4ACE6DB-AA99-401F-8BE6-8784BD09F003|C4ACE6DB-AA99-401F-8BE6-8784BD09F003|
|InfoPath|4153F732-D670-4E44-8AB7-500F2B576BDA|0F825A16-25B2-4771-A497-FC8AF3B355D8|C5BBD36E-B320-47EF-A512-556B99CB7E41|-|-|
|Outlook|1D844339-3DAE-413E-BC13-62D6A52816B2|F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136|N. 7824A03F-28CC-4371-BC54-93D15EFC1E7F|7C6D92EF-7B45-46E5-8670-819663220E4E|7C6D92EF-7B45-46E5-8670-819663220E4E|
|PowerPoint|EECBA6B8-3A62-44AD-99EB-866265466F9|- 813139AD-6DAB-4DDD-8C6D-0CA30D073B41|05758318-BCFD-4288-AD8D-81185841C235|E0A76492-0FD5-4EC2-8570-AE1BAA61DC88|E0A76492-0FD5-4EC2-8570-AE1BAA61DC88|
|Visio|3EA123B5-6316-452E-9D51-A489E06E2347|C1713368-12A8-41F1-ACA1-934B01AD6EEB|2CC0B221-22D2-4C15-A9FB-DE818E51AF75|2D4540EC-2C88-4C28-AE88-2614B5460648|2D4540EC-2C88-4C28-AE88-2614B5460648|
|Word|8B74A499-37F8-4DEA-B5A0-D72FC501CEFA|9FE736B7-B1EE-410C-8D07-082891C3DAC8|13C07AF5-B206-4A48-BB5B-B8022333E3CA|CD5CCACD-A7AC-4FD3-9F70-9454B5DE5161|CD5CCACD-A7AC-4FD3-9F70-9454B5DE5161|
|Microsoft Forms 2.0|B2279272-3FD2-434D-B94E-E4E0F8561AC4|B2279272-3FD2-434D-B94E-E4E0F8561AC4|A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC|-|-|
|Microsoft Graph|011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E|52DA4B37-B8EB-4B7F-89C1-824654CE4C70|24706F33-F0CE-4EB4-BC91-9E935394F510|-|-|
|smart tag|7102C98C-EF47-4F04-A227-FE33650BF954|487A7921-EB3A-4262-BB5B-A5736B732486|74EFC1F9-747D-4867-B951-EFCF29F51AF7|-|-|
|Office Condiviso|64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4|- 6A174BDB-0049-4D1C-86EF-3114CB0C4C4E|76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05|625F5772-C1B3-497E-8ABE-7254EDB00506|625F5772-C1B3-497E-8ABE-7254EDB00506|
|Project|- 957A4EC0-E67B-4E86-A383-6AF7270B216A|1C50E422-24FA-44A9-A120-E88280C8C341|706D7F44-8231-489D-9B25-3025ADE9F114|107BCD9A-F1DC-4004-A444-33706FC10058|107BCD9A-F1DC-4004-A444-33706FC10058|

  ![Screenshot delle condizioni di avvio finale](media/setup-project-figure-11.jpg)

  **Figura 11: Condizioni di lancio finali**

È possibile perfezionare ulteriormente le condizioni di avvio per l'installazione di ExcelAddIn.You can further refine the launch conditions for the ExcelAddIn installation. Ad esempio, potrebbe essere utile verificare se è installata l'applicazione di Office di destinazione effettiva.

### <a name="to-build-the-setup-project"></a>Per compilare il progetto di installazione

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto **OfficeAddInSetup** e **scegliere Compila**.
2. Utilizzando **Esplora risorse,** passare alla directory di output del progetto **OfficeAddInSetup** e passare alla cartella Release o Debug, a seconda della configurazione di compilazione selezionata. Copiare tutti i file dalla cartella in un percorso a cui gli utenti possono accedere.

Per testare l'installazione di ExcelAddIn

1. Passare al percorso in cui è stato copiato **OfficeAddInSetup.**
2. Fare doppio clic sul file setup.exe per installare il componente aggiuntivo **OfficeAddInSetup.** Accettare le Condizioni di licenza software visualizzate e completare l'installazione guidata per installare il componente aggiuntivo nel computer dell'utente.

La soluzione Excel Office deve essere installata ed eseguita dal percorso specificato durante l'installazione.

## <a name="additional-requirements-for-document-level-solutions"></a>Requisiti aggiuntivi per le soluzioni a livello di documentoAdditional Requirements for Document-Level Solutions

La distribuzione di soluzioni a livello di documento richiede alcuni passaggi di configurazione diversi nel progetto di installazione di Windows Installer.Deploying document-level solutions require a few different configuration steps in the Windows Installer setup project.

Ecco un elenco di passaggi di base necessari per distribuire una soluzione a livello di documento:Here's a list of basic steps required to deploy a document-level solution:

- Creare il progetto di installazione di Visual Studio.Create the Visual Studio Setup Project.
- Aggiungere l'output principale della soluzione a livello di documento. L'output primario include anche il documento di Microsoft Office.
- Aggiungere i manifesti di distribuzione e dell'applicazione come file non andati.
- Escludere i componenti dipendenti dal pacchetto di installazione (ad eccezione di eventuali assembly di utilità).
- Configurare i pacchetti dei prerequisiti.
- Configurare le condizioni di avvio.
- Compilare il progetto di installazione e copiare i risultati nel percorso di distribuzione.
- Distribuire la soluzione a livello di documento nel computer dell'utente eseguendo il programma di installazione.
- Se necessario, aggiornare le proprietà personalizzate del documento.

### <a name="changing-the-location-of-the-deployed-document"></a>Modifica della posizione del documento distribuito

Le proprietà all'interno di un documento di Office vengono utilizzate per individuare le soluzioni a livello di documento. Se il documento è installato nella stessa cartella dell'assembly VSTO, non sono necessarie modifiche. Tuttavia, se è installato in una cartella diversa, queste proprietà dovranno essere aggiornate durante l'installazione.

Per ulteriori informazioni su queste proprietà del documento, vedere [Cenni preliminari](custom-document-properties-overview.md)sulle proprietà personalizzate del documento .

Per modificare queste proprietà, è necessario utilizzare un'azione personalizzata durante l'installazione.

Nell'esempio seguente viene utilizzata una soluzione a livello di documento denominata ExcelWorkbookProject e un progetto di installazione denominato ExcelWorkbookSetup.The following example uses a document-level solution called ExcelWorkbookProject and a setup project called ExcelWorkbookSetup. Il progetto ExcelWorkbookSetup viene configurato utilizzando la stessa procedura descritta in precedenza, ad eccezione dell'impostazione delle chiavi del Registro di sistema.

Per aggiungere il progetto di azione personalizzata alla soluzione di Visual StudioTo add the custom action project to your Visual Studio solution

1. Aggiungere un nuovo progetto di console .NET alla soluzione facendo clic con il pulsante destro del mouse sul progetto di distribuzione di documenti di **Office** in **Esplora soluzioni**
2. Espandere **Aggiungi** e fare clic su **Nuovo progetto**.
3. Selezionare il modello App console e denominare il progetto **AddCustomizationCustomAction**.

    ![Screenshot di Esplora soluzioni - AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **Figura 12: Esplora soluzioni - AddCustomizationCustomActionFigure 12: Solution Explorer - AddCustomizationCustomAction**

4. Aggiungere un riferimento a questi assembly:Add a Reference to these assemblies:
    1. System.ComponentModel
    2. System.Configuration.Install
    3. Microsoft.VisualStudio.Tools.Applications
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. Copiare questo codice in Program.cs o Program.vb

```csharp
    using System;
    using System.IO;
    using System.Collections;
    using System.ComponentModel;
    using System.Configuration.Install;
    using Microsoft.VisualStudio.Tools.Applications;
    using Microsoft.VisualStudio.Tools.Applications.Runtime;

    namespace AddCustomizationCustomAction
    {
        [RunInstaller(true)]
        public class AddCustomizations : Installer
        {
            public AddCustomizations() : base() { }

            public override void Install(IDictionary savedState)
            {
                base.Install(savedState);

                //Get the CustomActionData Parameters
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;
                string assemblyLocation = Context.Parameters.ContainsKey("assemblyLocation") ? Context.Parameters["assemblyLocation"] : String.Empty;
                string deploymentManifestLocation = Context.Parameters.ContainsKey("deploymentManifestLocation") ? Context.Parameters["deploymentManifestLocation"] : String.Empty;
                Guid solutionID = Context.Parameters.ContainsKey("solutionID") ? new Guid(Context.Parameters["solutionID"]) : new Guid();

                string newDocLocation = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation));

                try
                {
                    //Move the file and set the Customizations
                    if (Uri.TryCreate(deploymentManifestLocation, UriKind.Absolute, out Uri docManifestLocationUri))
                    {
                        File.Move(documentLocation, newDocLocation);
                        ServerDocument.RemoveCustomization(newDocLocation);
                        ServerDocument.AddCustomization(newDocLocation, assemblyLocation,
                                                        solutionID, docManifestLocationUri,
                                                        true, out string[] nonpublicCachedDataMembers);
                    }
                    else
                    {
                        LogMessage("The document could not be customized.");
                    }
                }
                catch (ArgumentException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (DocumentNotCustomizedException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (InvalidOperationException)
                {
                    LogMessage("The customization could not be removed.");
                }
                catch (IOException)
                {
                    LogMessage("The document does not exist or is read-only.");
                }
            }

            public override void Rollback(IDictionary savedState)
            {
                base.Rollback(savedState);
                DeleteDocument();
            }
            public override void Uninstall(IDictionary savedState)
            {
                base.Uninstall(savedState);
                DeleteDocument();
            }
            private void DeleteDocument()
            {
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;

                try
                {
                    File.Delete(Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation)));
                }
                catch (Exception)
                {
                    LogMessage("The document doesn't exist or is read-only.");
                }
            }
            private void LogMessage(string Message)
            {
                if (Context.Parameters.ContainsKey("LogFile"))
                {
                    Context.LogMessage(Message);
                }
            }

            static void Main() { }
            }
    }
```

Per aggiungere la personalizzazione al documento, è necessario disporre dell'ID soluzione della soluzione a livello di documento VSTO. Questo valore viene recuperato dal file di progetto di Visual Studio.This value is retrieved from the Visual Studio project file.

Per recuperare l'ID della soluzioneTo retrieve the solution ID

1. Scegliere **Compila soluzione** dal menu **Compila** per compilare la soluzione a livello di documento e aggiungere la proprietà ID soluzione al file di progetto.
2. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto a livello di documento **ExcelWorkbookProject**
3. Fare clic su UnloadProject per accedere al file di progetto dall'interno di Visual Studio.Click **UnloadProject** to access the project file from inside Visual Studio.

    ![Screenshot di Esplora soluzioni che scarica la soluzione di documenti Excel](media/setup-project-figure-16.jpg)

    **Figura 13: Scaricamento della soluzione documento ExcelFigure 13: Sloading Excel Document Solution**

4. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **ExcelWorkbookProject** e **scegliere ModificaExcelWorkbookProject.vbproj** o **ModificaProgettoCartellaExcel.csproj**.
5. Nell'editor **ExcelWorkbookProject** individuare l'elemento **SolutionID** all'interno dell'elemento **PropertyGroup** .
6. Copiare il valore GUID di questo elemento.

    ![Recupero di SolutionIDRetrieving the SolutionID](media/setup-project-figure-17.jpg)

    **Figura 14: Recupero di SolutionIDFigure 14: Retrieving the SolutionID**

7. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **ExcelWorkbookProject** e scegliere **Ricarica progetto**.
8. Fare clic su **Sì** nella finestra di dialogo visualizzata per chiudere l'editor **ExcelWorkbookProject.**
9. **L'ID soluzione** verrà utilizzato nell'azione di installazione personalizzata.

L'ultimo passaggio consiste nel configurare l'azione personalizzata per i passaggi di **installazione** e **disinstallazione.**

### <a name="to-configure-the-setup-project"></a>Per configurare il progetto di installazione

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **ExcelWorkbookSetup**, scegliere **Aggiungi** e fare clic su **Output progetto**.
2. Nell'elenco **Progetto** della finestra di dialogo **Aggiungi gruppo output progetto** fare clic su **AggiungiCustomizationCustomAction**.
3. Selezionare **Output primario** e fare clic **su OK** per chiudere la finestra di dialogo e aggiungere l'assembly contenente l'azione personalizzata al progetto di installazione.

    ![Screenshot della finestra Azione personalizzata manifesto del manifesto - Aggiungi gruppo output progetto](media/setup-project-figure-18.jpg)

    **Figura 15: Azione personalizzata del manifesto del documento - Aggiungi gruppo output progetto**

4. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **ExcelWorkbookSetup**.
5. Espandere **Visualizza** e fare clic su **Azioni personalizzate**.
6. Nell'editor **Azioni personalizzate(ExcelWorkbookSetup)** fare clic con il pulsante destro del mouse su **Azioni personalizzate** e scegliere Aggiungi **azione personalizzata**.
7. Nell'elenco **Cerca in** della finestra di dialogo Seleziona elemento **nel progetto** fare clic su **Cartella applicazione.** Selezionare **Output primario da AddCustomizationCustomAction(attivo)** e fare clic **su OK** per aggiungere l'azione personalizzata al passaggio Installa.Select Primary Output from AddCustomizationCustomAction(active) and click OK to add the custom action to the Install step.
8. Nel **nodo Installa**fare clic con il pulsante destro del mouse su **Output primario di AddCustomizationCustomAction(Active)** e scegliere **Rinomina**. Assegnare all'azione personalizzata il nome **Copia documento in Documenti e allega personalizzazione**.
9. Nel **nodo Disinstalla**fare clic con il pulsante destro del mouse su **Output primario di AddCustomizationCustomAction(Active)** e **scegliere Rinomina**. Assegnare all'azione personalizzata il nome **Rimuovi documento dalla cartella Documenti**.

    ![Screenshot della finestra Azioni personalizzate del manifesto del documento](media/setup-project-figure-19.jpg)

    **Figura 16: Azioni personalizzate del manifesto del documento**

10. Nell'editor **Azioni personalizzate(ExcelWorkbookSetup)** fare clic con il pulsante destro del mouse su **Copia documento in Documenti e allegare** la personalizzazione e **scegliere Finestra Proprietà**.
11. Nella finestra **Proprietà** **CustomActionData** immettere il percorso della DLL di personalizzazione, il manifesto di distribuzione e il percorso del documento di Microsoft Office. È necessario anche SolutionID.
12. Se si desidera registrare eventuali errori di installazione in un file, includere un parametro LogFile.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Screenshot della finestra Azione personalizzata per la copia del documento nelle proprietà dei documenti](media/setup-project-figure-20.jpg)

    **Figura 17: Azione personalizzata per copiare il documento in documenti**

13. L'azione personalizzata per la disinstallazione richiede il nome del documento, è possibile fornire che utilizzando lo stesso parametro documentLocation nel **CustomActionData**

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. Compilare e distribuire il progetto **ExcelWorkbookSetup.Compile** and deploy the ExcelWorkbookSetup project.
15. Cercare nella cartella **Documenti** e aprire il file ExcelWorkbookProject.xlsx.

## <a name="additional-resources"></a>Risorse aggiuntive

[Procedura: installare Visual Studio Tools per Office RuntimeHow to: Install the Visual Studio Tools for Office Runtime](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Assembly di interoperabilità primari di OfficeOffice Primary Interop Assemblies](office-primary-interop-assemblies.md)

[Voci del Registro di sistema per i componenti aggiuntivi VSTORegistry entries for VSTO Add-ins](registry-entries-for-vsto-add-ins.md)

[Custom Document Properties Overview](custom-document-properties-overview.md)

[Specifica delle aree del modulo nel Registro di sistema di WindowsSpecifying Form Regions in the Windows Registry](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Granting Trust to Documents](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>Informazioni sugli autori

Wouter van Vugt è un Microsoft MVP con tecnologie Office Open XML e un consulente indipendente che si concentra sulla creazione di applicazioni Office Business (OAS) con SharePoint, Microsoft Office e le relative tecnologie .NET.
Wouter è un collaboratore frequente di siti di comunità di sviluppatori come [MSDN](/previous-versions/office/developer/office-2007/bb879915(v=office.12)). Ha pubblicato diversi white paper e articoli, nonché un libro disponibile on line intitolato Open XML: Explained e-book.
Wouter è il fondatore di Code-Counsel, una società olandese che si concentra sulla distribuzione di contenuti tecnici all'avanguardia attraverso una varietà di canali. Puoi saperne di più su Wouter leggendo il suo blog.

Ted Pattison è un MVP di SharePoint, autore, formatore e il fondatore di Ted Pattison Group. Nell'autunno del 2005, Ted è stato assunto dal gruppo Evangelismo piattaforma per sviluppatori di Microsoft per creare il programma di formazione Per sviluppatori Ascend per Windows SharePoint Services 3.0 e Microsoft Office SharePoint Server 2007. Da allora, Ted si è concentrato interamente sull'educazione degli sviluppatori professionisti sulle tecnologie SharePoint 2007. Ted ha terminato di scrivere un libro per Microsoft Press intitolato Inside Windows SharePoint Services 3.0 che si concentra su come utilizzare SharePoint come piattaforma di sviluppo per la creazione di soluzioni aziendali. Ted scrive anche un articolo incentrato sugli sviluppatori per MSDN Magazine intitolato Office Space.
