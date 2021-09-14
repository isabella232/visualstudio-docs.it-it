---
title: Distribuzione di una soluzione VSTO con Windows installer
description: Informazioni su come distribuire un componente aggiuntivo Microsoft Visual Studio Tools for Office (VSTO) o una soluzione a livello di documento usando un Programma di installazione di Visual Studio progetto.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d3145e17eb63417c13ffa9292ec6de50ae3ef88e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634147"
---
# <a name="deploying-a-vsto-solution-using-windows-installer"></a>Distribuzione di una soluzione VSTO con Windows installer

## <a name="summary"></a>Riepilogo

Informazioni su come distribuire un componente aggiuntivo Microsoft Visual Studio Tools for Office (VSTO) o una soluzione a livello di documento usando un Programma di installazione di Visual Studio progetto.

Wouter van Vugt, Code Counsel

Ted Pattison, Ted Pattison Group

Questo articolo è stato aggiornato da Microsoft con l'autorizzazione degli autori originali.

**Si applica a: Visual Studio Tools per Office,** Microsoft Office, Microsoft Visual Studio.

## <a name="overview"></a>Panoramica

È possibile sviluppare una soluzione VSTO e distribuirne una usando un pacchetto Windows Installer. Questa discussione include i passaggi per la distribuzione di un componente Office componente aggiuntivo.

## <a name="deployment-methods"></a>Metodi di distribuzione

ClickOnce possibile usare facilmente per creare configurazioni per i componenti aggiuntivi e le soluzioni. Tuttavia, non può installare componenti aggiuntivi che richiedono privilegi amministrativi, ad esempio componenti aggiuntivi a livello di computer.

I componenti aggiuntivi che richiedono privilegi amministrativi possono essere installati usando Windows Installer, ma richiede più impegno per creare l'installazione.

Per una panoramica su come distribuire una soluzione VSTO usando ClickOnce, vedere Distribuire una soluzione Office usando ClickOnce [.](deploying-an-office-solution-by-using-clickonce.md)

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Distribuzione di Office soluzioni che hanno come destinazione il VSTO runtime

ClickOnce e Windows del programma di installazione devono eseguire le stesse attività rudimentari durante l'installazione di una Office soluzione.

1. Installare i componenti dei prerequisiti nel computer utente.
2. Distribuire i componenti specifici per la soluzione.
3. Per i componenti aggiuntivi, creare voci del Registro di sistema.
4. Considerare attendibile la soluzione per consentire l'esecuzione.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Componenti prerequisiti necessari nel computer di destinazione

Ecco l'elenco del software che deve essere installato nel computer per eseguire VSTO soluzioni:

- Microsoft Office 2010 o versione più recente.
- Microsoft .NET Framework 4 o versione più recente.
- Microsoft Visual Studio 2010 Tools per Office Runtime.
  Il runtime fornisce un ambiente che gestisce componenti aggiuntivi e soluzioni a livello di documento. Una versione del runtime viene Microsoft Office ma è possibile ridistribuire una versione specifica con il componente aggiuntivo.
- Gli assembly di interoperabilità primari per Microsoft Office, se non si usano tipi di interoperabilità incorporati.
- Qualsiasi assembly di utilità a cui fanno riferimento i progetti.

### <a name="specific-components-for-the-solution"></a>Componenti specifici per la soluzione

Il pacchetto del programma di installazione deve installare questi componenti nel computer dell'utente:

- Il Microsoft Office documento, se si crea una soluzione a livello di documento.
- Assembly di personalizzazione ed eventuali assembly necessari.
- Componenti aggiuntivi, ad esempio i file di configurazione.
- Manifesto dell'applicazione (con estensione manifest).
- Manifesto della distribuzione (con estensione vsto).

### <a name="registry-entries-for-add-ins"></a>Voci del Registro di sistema per i componenti aggiuntivi

Microsoft Office le voci del Registro di sistema per individuare e caricare i componenti aggiuntivi. Queste voci del Registro di sistema devono essere create come parte del processo di distribuzione. Per altre informazioni su queste voci del Registro di sistema, vedere Voci del Registro di sistema [VSTO componenti aggiuntivi](registry-entries-for-vsto-add-ins.md).

Outlook I componenti aggiuntivi che visualizzano aree modulo personalizzate richiedono voci del Registro di sistema aggiuntive che consentono di identificare le aree del modulo. Per altre informazioni sulle voci del Registro di sistema, vedere [Voci del Registro di sistema per Outlook modulo](registry-entries-for-vsto-add-ins.md#OutlookEntries).

Le soluzioni a livello di documento non richiedono voci del Registro di sistema. Al contrario, le proprietà all'interno del documento vengono usate per individuare la personalizzazione. Per altre informazioni su queste proprietà, vedere [Panoramica delle proprietà dei documenti personalizzate](custom-document-properties-overview.md).

### <a name="trusting-the-vsto-solution"></a>Attendibilità della soluzione VSTO

Per consentire l'esecuzione di una personalizzazione, una soluzione deve essere attendibile dal computer. Il componente aggiuntivo può essere considerato attendibile firmando il manifesto con un certificato, creando una relazione di trust con un elenco di inclusione o installarlo in un percorso attendibile nel computer.

Per altre informazioni su come ottenere un certificato per la firma, vedere distribuzione ClickOnce [e Authenticode](../deployment/clickonce-and-authenticode.md). Per altre informazioni sulle soluzioni attendibili, vedere [Trusting Office Solutions by Using Inclusion Lists](trusting-office-solutions-by-using-inclusion-lists.md). È possibile aggiungere una voce dell'elenco di inclusione con un'azione personalizzata nel file Windows Installer. Per altre informazioni sull'abilitazione dell'elenco di inclusione, vedere [Procedura: Configurare la sicurezza dell'elenco di inclusione](how-to-configure-inclusion-list-security.md).

Se non viene usata nessuna delle due opzioni, viene visualizzata una richiesta di attendibilità all'utente per consentire loro di decidere se considerare attendibile la soluzione.

Per altre informazioni sulla sicurezza correlata alle soluzioni a livello di documento, vedere [Concessione di attendibilità ai documenti](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Creazione di un programma di installazione di base

I modelli di progetto di installazione e distribuzione sono inclusi [nell'estensione Microsoft Visual Studio Installer Projects](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) disponibile per il download.

Per creare un programma di installazione per Office soluzione, è necessario eseguire queste attività:

- Aggiungere i componenti della Office soluzione che verrà distribuita.
- Per i componenti aggiuntivi a livello di applicazione, configurare le chiavi del Registro di sistema.
- Configurare i componenti prerequisiti in modo che possano essere installati nei computer degli utenti finali.
- Configurare le condizioni di avvio per verificare che siano disponibili i componenti prerequisiti necessari. Le condizioni di avvio possono essere usate per bloccare l'installazione se non sono installati tutti i prerequisiti necessari.

Il primo passaggio consiste nel creare il progetto di installazione.

### <a name="to-create-the-addin-setup-project"></a>Per creare il progetto installazione AddIn

1. Aprire il Office AddIn Project da distribuire. Per questo esempio si usa un componente Excel componente aggiuntivo denominato ExcelAddIn.
2. Con il Office Project apri scegliere Aggiungi dal  menu **File** e fare clic su **Nuovo Project** per aggiungere un nuovo progetto.
::: moniker range="=vs-2017"
3. Nella finestra **di dialogo Aggiungi** nuovo Project espandere Altri  Project **tipi** di Project ,  quindi espandere Installazione e distribuzione e quindi **selezionare Programma di installazione di Visual Studio**.
4. Nel riquadro **Modelli** selezionare Configurazione **Project** nel gruppo Visual Studio **modelli** installati.
::: moniker-end
::: moniker range="=vs-2019"
3. Nella finestra **di dialogo Aggiungi un nuovo Project** selezionare il modello **Project** configurazione.
4. Fare clic su **Avanti**.
::: moniker-end

5. Nella casella **Nome** digitare **OfficeAddInSetup**.
::: moniker range="=vs-2017"
6. Fare **clic su** Apri per creare il nuovo progetto di installazione.
::: moniker-end
::: moniker range="=vs-2019"
6. Fare **clic su** Crea per creare il nuovo progetto di installazione.
::: moniker-end

Visual Studio apre Esplora file system per il nuovo progetto di installazione. Esplora file system consente di aggiungere file al progetto di installazione.

   ![Screenshot di Esplora file system per il progetto di installazione](media/setup-project-figure-1.png)

   **Figura 1: Esplora file system per il progetto di installazione**

Il progetto di installazione deve distribuire ExcelAddIn. È possibile configurare il progetto di installazione per questa attività aggiungendo l'output del progetto ExcelAddIn al progetto di installazione.

### <a name="to-add-the-exceladdin-project-output"></a>Per aggiungere l'output del progetto ExcelAddIn

1. Nella finestra **Esplora soluzioni** fare clic con il pulsante  destro del mouse su **OfficeAddInSetup**, scegliere Aggiungi e quindi **Project Output**.
2. Nella finestra **di dialogo Aggiungi Project output** primario selezionare **ExcelAddIn** nell'elenco del progetto e **Output primario**.
3. Fare **clic su OK** per aggiungere l'output del progetto al progetto di installazione.

    ![Screenshot della finestra di dialogo Aggiungi Project gruppo di output Project configurazione](media/setup-project-figure-2.png)

    **Figura 2: Finestra di dialogo Project aggiungi gruppo di output Project configurazione**

Il progetto di installazione deve distribuire il manifesto della distribuzione e il manifesto dell'applicazione. Aggiungere questi due file al progetto di installazione come file autonomi dalla cartella di output del progetto ExcelAddIn.

### <a name="to-add-the-deployment-and-application-manifests"></a>Per aggiungere i manifesti della distribuzione e dell'applicazione

1. Nella finestra **Esplora soluzioni** fare clic con il pulsante destro del mouse su **OfficeAddInSetup**, scegliere **Aggiungi** e fare clic su **File**.
2. Nella finestra **di dialogo** Aggiungi file passare alla directory di output **ExcelAddIn.** In genere la directory di output è la **sottocartella \\ della** versione bin della directory radice del progetto, a seconda della configurazione di compilazione selezionata.
3. Selezionare i **file ExcelAddIn.vsto** **eExcelAddIn.dll.manifest** e fare clic su **Apri** per aggiungere questi due file al progetto di installazione.

    ![Screenshot dei manifesti dell'applicazione e della distribuzione in Esplora soluzioni](media/setup-project-figure-3.jpg)

    **Figura 3: Manifesti dell'applicazione e della distribuzione per il componente aggiuntivo in Esplora soluzioni**

Facendo riferimento a ExcelAddIn sono inclusi tutti i componenti richiesti da ExcelAddIn. Questi componenti devono essere esclusi e distribuiti usando i pacchetti prerequisiti per consentire la corretta registrazione. Inoltre, le Condizioni di licenza software devono essere visualizzate e accettate prima dell'inizio dell'installazione.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>Per escludere le dipendenze del progetto ExcelAddIn

1. Nel **Esplora soluzioni**, nel **nodo OfficeAddInSetup** , selezionare tutti  gli elementi di dipendenza sotto l'elemento Dipendenze rilevate ad eccezione di **Microsoft .NET Framework** o di qualsiasi assembly che termina con **\* .Utilities.dll**. Gli assembly di utilità devono essere distribuiti insieme all'applicazione.
2. Fare clic con il pulsante destro del mouse sul gruppo e **scegliere Proprietà.**
3. Nella finestra **Proprietà** impostare la proprietà **Exclude su** **True** per escludere gli assembly dipendenti dal progetto di installazione. Assicurarsi di non escludere gli assembly di utilità.

    ![Screenshot della Esplora soluzioni che mostra le dipendenze da escludere](media/setup-project-figure-4.jpg)

    **Figura 4: Esclusione delle dipendenze**

È possibile configurare il pacchetto Windows Installer per installare i componenti prerequisiti aggiungendo un programma di installazione, noto anche come programma di avvio automatico. Questo programma di installazione può installare i componenti prerequisiti, un processo denominato bootstrap.

Per **ExcelAddIn**, è necessario installare questi prerequisiti prima che il componente aggiuntivo possa essere eseguito correttamente:

- Versione di Microsoft .NET Framework a cui è destinata Office soluzione.
- Microsoft Visual Studio 2010 Tools per Office Runtime.

Per configurare i componenti dipendenti come prerequisiti

1. Nella finestra **Esplora soluzioni** fare clic con il pulsante destro del mouse sul **progetto OfficeAddInSetup** e **scegliere Proprietà.**
2. Verrà visualizzata la finestra di dialogo Pagine delle proprietà **OfficeAddInSetup** .
3. Fare clic **sul pulsante** Prerequisiti.
4. Nella finestra di dialogo Prerequisiti selezionare la versione corretta del .NET Framework e il Microsoft Visual Studio Tools for Office Runtime.

    ![Screenshot della finestra di dialogo Prerequisiti](media/setup-project-figure-5.png)

    **Figura 5: Finestra di dialogo Prerequisiti**

    > [!NOTE]
    >Alcuni dei pacchetti prerequisiti configurati nel Visual Studio di installazione Project dipendono dalla configurazione della build selezionata. È necessario selezionare i componenti prerequisiti per ogni configurazione di build in uso.

Microsoft Office individua i componenti aggiuntivi usando le chiavi del Registro di sistema. Le chiavi nell'hive HKEY \_ CURRENT USER vengono usate per \_ registrare il componente aggiuntivo per ogni singolo utente. Le chiavi \_ nell'hive HKEY LOCAL MACHINE vengono usate per registrare il componente \_ aggiuntivo per tutti gli utenti del computer. Per altre informazioni sulle chiavi del Registro di sistema, vedere [Registry entries for VSTO Add-ins](registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-the-registry"></a>Per configurare il Registro di sistema

1. Nella finestra di **Esplora soluzioni** fare clic con il pulsante destro **del mouse su OfficeAddInSetup.**
2. Espandere **Visualizza**.
3. Fare clic **su Registro di** sistema per aprire la finestra dell'editor del Registro di sistema.
4. Nell'editor **Registro di sistema (OfficeAddInSetup)** espandere **HKEY LOCAL \_ \_ MACHINE** e quindi **Software**.
5. Eliminare il **\[ produttore \]**?chiave trovato in **HKEY \_ LOCAL MACHINE \_ \\ Software**.
6. Espandere **HKEY \_ CURRENT USER \_ e** quindi **Software**.
7. Eliminare la **\[ chiave Manufacturer \]** disponibile in **HKEY CURRENT USER \_ \_ \\ Software**.
8. Per aggiungere le chiavi del Registro di sistema per l'installazione del componente aggiuntivo, fare clic con il pulsante destro del mouse sulla chiave **Hive utente/computer,** **selezionare Nuova chiave.** Usare il testo **Software** come nome della nuova chiave. Fare clic con il pulsante destro del mouse sulla **chiave software** appena creata e creare una nuova chiave con il testo **Microsoft**.
9. Usare un processo simile per creare l'intera gerarchia di chiavi necessaria per la registrazione del componente aggiuntivo:

    **User/Machine Hive \\ Software Microsoft Office Excel \\ \\ \\ \\ \\ Addins SampleCompany.ExcelAddIn**

    Il nome della società viene spesso usato come prefisso per il nome del componente aggiuntivo per garantire l'univocità.

10. Fare clic con il pulsante destro del mouse sulla chiave **SampleCompany.ExcelAddIn,** **scegliere Nuovo** e fare clic su **Valore stringa**. Usare il testo **Descrizione** per Nome.
11. Usare questo passaggio per aggiungere altri tre valori:
    - **FriendlyName** di tipo **String**
    - **LoadBehavior** di tipo **DWORD**
    - **Manifesto** di tipo **String**

12. Fare clic con il pulsante destro **del mouse** sul valore Descrizione nell'editor del Registro di sistema e scegliere **Finestra Proprietà**. Nella finestra **Proprietà** immettere Excel **Demo AddIn** per la proprietà Value.
13. Selezionare la **chiave FriendlyName** nell'editor del Registro di sistema. Nella finestra **Proprietà modificare** la proprietà **Value** in Excel **Demo AddIn**.
14. Selezionare la chiave **LoadBehavior** nell'editor del Registro di sistema. Nella finestra **Proprietà** impostare la **proprietà Value** su **3.** Il valore 3 per LoadBehavior indica che il componente aggiuntivo deve essere caricato all'avvio dell'applicazione host. Per altre informazioni sul comportamento di caricamento, vedere [Registry entries for VSTO Add-ins](registry-entries-for-vsto-add-ins.md).

15. Selezionare la chiave **Manifest** nell'editor del Registro di sistema. Nella finestra **Proprietà modificare** la proprietà **Value** in **file:///[TARGETDIR]ExcelAddIn.vsto|vstolocal**

    ![Screenshot dell'editor del Registro di sistema](media/setup-project-figure-6.png)

    **Figura 6: Configurazione delle chiavi del Registro di sistema**

      Il VSTO runtime usa questa chiave del Registro di sistema per individuare il manifesto della distribuzione. La macro [TARGETDIR] verrà sostituita con la cartella in cui è installato il componente aggiuntivo. La macro includerà il carattere \ finale, quindi il nome file del manifesto della distribuzione deve essere ExcelAddIn.vsto senza il carattere \.
      Il **suffisso vstolocal** indica al runtime VSTO che il componente aggiuntivo deve essere caricato da questo percorso anziché dalla cache ClickOnce. La rimozione di questo suffisso causerà la copia della personalizzazione nella cache ClickOnce runtime.

   >[!WARNING]
   >È necessario prestare molta attenzione con l'editor del Registro di sistema Visual Studio. Ad esempio, se si imposta accidentalmente DeleteAtUninstall per la chiave errata, è possibile eliminare una parte attiva del Registro di sistema, lasciando il computer utente in uno stato incoerente, o ancora peggiore, danneggiato.

Le versioni a 64 bit Office useranno l'hive del Registro di sistema a 64 bit per cercare i componenti aggiuntivi. Per registrare i componenti aggiuntivi nell'hive del Registro di sistema a 64 bit, la piattaforma di destinazione del progetto di installazione deve essere impostata solo su 64 bit.

1. Selezionare il **progetto OfficeAddInSetup** in Esplora soluzioni.
2. Passare alla **finestra** Proprietà e impostare la **proprietà TargetPlatform** su **x64.**

L'installazione di un componente aggiuntivo per le versioni a 32 bit e a 64 bit di Office richiede la creazione di due pacchetti MSI separati. Uno per 32 bit e uno per 64 bit.

  ![Screenshot della finestra Proprietà che mostra la piattaforma di destinazione per la registrazione di componenti aggiuntivi con componenti Office](media/setup-project-figure-7.jpg)

  **Figura 7: Piattaforma di destinazione per la registrazione di componenti aggiuntivi con componenti Office**

Se il pacchetto MSI viene usato per installare il componente aggiuntivo o la soluzione, può essere installato senza i prerequisiti necessari. È possibile usare condizioni di avvio nel file MSI per bloccare l'installazione del componente aggiuntivo se i prerequisiti non sono installati.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>Configurare una condizione di avvio per rilevare il VSTO runtime

1. Nella finestra di **Esplora soluzioni** fare clic con il pulsante destro **del mouse su OfficeAddInSetup.**
2. Espandere **Visualizza**.
3. Fare clic **su Condizioni di avvio**.
4. Nell'editor **Condizioni di avvio (OfficeAddInSetup)** fare clic con il pulsante destro del mouse su **Requisiti** nel computer di destinazione e quindi scegliere Aggiungi condizione di avvio **registro**. Questa condizione di ricerca può cercare nel Registro di sistema una chiave installata VSTO runtime. Il valore della chiave è quindi disponibile per le varie parti del programma di installazione tramite una proprietà denominata. La condizione di avvio usa la proprietà definita dalla condizione di ricerca per verificare la presenza di un determinato valore.
5. Nell'editor **Condizioni di avvio (OfficeAddInSetup)** selezionare la condizione di ricerca **Cerca RegistryEntry1,** fare clic con il pulsante destro del mouse sulla condizione e **scegliere Finestra Proprietà.**

6. Nella finestra **Proprietà** impostare queste proprietà:
   1. Impostare il valore di **(Name)** su **Search for VSTO 2010 Runtime**.
   2. Modificare il valore di **Property** in **VSTORUNTIMEREDIST.**
   3. Impostare il valore di **RegKey** su **SOFTWARE Microsoft VSTO Runtime Setup \\ \\ \\ v4R**
   4. Lasciare la **proprietà Radice** impostata su **vsdrrHKLM**.
   5. Modificare la **proprietà Value** in **Version.**

7. Nell'editor **Condizioni di avvio (OfficeAddInSetup)** selezionare la condizione di **avvio Condition1,** fare clic con il pulsante destro del mouse sulla condizione e **scegliere Finestra Proprietà.**
8. Nella finestra Proprietà impostare queste proprietà:
   1. Impostare **(Name) su** **Verify VSTO 2010 Runtime availability ( Verifica disponibilità runtime 2010).**
   2. Modificare il valore della **condizione** in **VSTORUNTIMEREDIST \> ="10.0.30319"**
   3. Lasciare vuota **la proprietà InstallURL.**
   4. Impostare Message **su** **The Visual Studio 2010 Tools for Office Runtime non è installato. Eseguire Setup.exe per installare il componente aggiuntivo**.

        ![Screenshot della finestra Proprietà per la condizione di avvio Verifica disponibilità runtime](media/setup-project-figure-8.jpg)

        **Figura 8: Finestra Proprietà per la condizione di avvio Verifica disponibilità runtime**

 La condizione di avvio precedente verifica in modo esplicito la presenza VSTO runtime quando viene installato dal pacchetto del programma di avvio automatico.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Configurare una condizione di avvio per rilevare il runtime VSTO installato da Office

1. Nell'editor **Condizioni di avvio (OfficeAddInSetup)** fare clic con il pulsante destro del mouse su Cerca computer **di** destinazione e quindi scegliere Aggiungi **ricerca registro**.
2. Selezionare la **condizione di ricerca Cerca RegistryEntry1,** fare clic con il pulsante destro del mouse sulla condizione e scegliere Finestra **Proprietà**.
3. Nella finestra **Proprietà** impostare queste proprietà:
    1. Impostare il valore di **(Name)** su **Search for Office VSTO Runtime**.
    2. Modificare il valore di **Property in** **OfficeRuntime**.
    3. Impostare il valore di **RegKey** su **SOFTWARE Microsoft VSTO Runtime Setup \\ \\ \\ v4**.
    4. Lasciare la **proprietà Root** impostata su **vsdrrHKLM**.
    5. Modificare la **proprietà Value** in **Version**.

4. Nell'editor Condizioni di avvio **(OfficeAddInSetup)** selezionare la condizione di avvio Verifica disponibilità **VSTO runtime 2010** definita in precedenza, fare clic con il pulsante destro del mouse sulla condizione e scegliere Finestra **Proprietà**.

5. Modificare il valore della proprietà **Condition** in **VSTORUNTIMEREDIST \> ="10.0.30319" OR OFFICERUNTIME \> ="10.0.21022"**. I numeri di versione possono essere diversi a seconda delle versioni del runtime necessarie per il componente aggiuntivo.

    ![Screenshot del riquadro Proprietà Windows per la condizione di avvio](media/setup-project-figure-9.jpg)
  
    **Figura 9: Proprietà Windows verifica disponibilità del runtime tramite redist o Office di avvio**

Se un componente aggiuntivo è destinato .NET Framework 4 o versione più recente, i tipi all'interno degli assembly di interoperabilità primari a cui viene fatto riferimento possono essere incorporati nell'assembly VSTO primario.

Per verificare se i tipi di interoperabilità verranno incorporati nel componente aggiuntivo, seguire questa procedura:

1. Espandere il nodo Riferimenti in Esplora soluzioni
2. Selezionare uno dei riferimenti PIA, ad esempio, **Office**.
3. Visualizzare le finestre delle proprietà premendo F4 o selezionando Proprietà dal menu di scelta rapida Assembly.
4. Controllare il valore della proprietà **Incorpora tipi di interoperabilità**.

Se il valore è impostato su **True,** i tipi vengono incorporati ed è possibile passare alla sezione [**Per compilare il progetto di installazione.**](#to-build-the-setup-project)

Per altre informazioni, vedere [Equivalenza dei tipi e Tipi di interoperabilità incorporati](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Per configurare le condizioni di avvio per rilevare questo Office personali

1. Nell'editor **Condizioni di avvio (OfficeAddInSetup)** fare clic con il pulsante destro del mouse su **Requisiti** nel computer di destinazione e quindi scegliere Aggiungi condizione di avvio Windows programma **di installazione**. Questa condizione di avvio cerca un Office piA cercando l'ID componente specifico.
2. Fare clic con **il pulsante destro del mouse su Cerca Componente1** e scegliere Finestra **Proprietà** per visualizzare le proprietà della condizione di avvio.
3. Nella finestra **Proprietà impostare** queste proprietà:

    1. Modificare il valore della proprietà **(Name)** in **Search for Office Shared PIA**
    2. Modificare il valore di **ComponentID** in Id componente per Office componente in uso. È possibile trovare l'elenco di ID componente nella tabella seguente, ad esempio **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}**.
    3. Modificare il valore della **proprietà Property** in **HASSHAREDPIA**.

4. Nell'editor **Condizioni di avvio (OfficeAddInSetup)** fare  clic con il pulsante destro del mouse su **Condizione1** e scegliere Finestra Proprietà per visualizzare le proprietà della condizione di avvio.

5. Modificare queste proprietà di **Condition1:**

    1. Modificare **(Name)** in Verify Office Shared PIA availability (Verifica **disponibilità dell'account di** interoperabilità Office condiviso).
    2. Impostare **Condizione su** **HASSHAREDPIA**.
    3. Lasciare **vuoto InstallUrl.**
    4. Modificare Il **messaggio** in **Un componente obbligatorio per l'interazione con Excel non è disponibile. Eseguire setup.exe**.

    ![Screenshot della finestra Proprietà per la condizione di avvio verify Office PIA condiviso](media/setup-project-figure-10.jpg)
  
    **Figura 10: Finestra Proprietà per la condizione di Office di avvio dell'app pia condivisa**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>ID componente degli assembly di interoperabilità primari per Microsoft Office

|Assembly di interoperabilità primario|Office 2010|Office 2013|Office 2013 (64 bit)|Office 2016|Office 2016 (64 bit)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26E4FC2223FF}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153F732-D670-4E44-8AB7-500F2B576BDA}|{0F825A16-25B2-4771-A497-FC8AF3B355D8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1D844339-3DAE-413E-BC13-62D6A52816B2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824A03F-28CC-4371-BC54-93D15EFC1E7F}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|
|PowerPoint|{EECBA6B8-3A62-44AD-99EB-86662654666F9}|{813139AD-6DAB-4DDD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3EA123B5-6316-452E-9D51-A489E06E2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2CC0B221-22D2-4C15-A9FB-DE818E51AF75}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|
|Word|{8B74A499-37F8-4DEA-B5A0-D72FC501CEFA}|{9FE736B7-B1EE-410C-8D07-082891C3DAC8}|{13C07AF5-B206-4A48-BB5B-B802233E3CA}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|
|Microsoft Forms 2.0|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52DA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510}|-|-|
|smart tag|{7102C98C-EF47-4F04-A227-FE33650BF954}|{487A7921-EB3A-4262-BB5B-A5736B732486}|{74EFC1F9-747D-4867-B951-EFCF29F51AF7}|-|-|
|Office Condiviso|{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E}|{76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|
|Project|{957A4EC0-E67B-4E86-A383-6AF7270B216A}|{1C50E422-24FA-44A9-A120-E88280C8C341}|{706D7F44-8231-489D-9B25-3025ADE9F114}|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![Screenshot delle condizioni di avvio finale](media/setup-project-figure-11.jpg)

  **Figura 11: Condizioni di lancio finali**

È possibile perfezionare ulteriormente le condizioni di avvio per l'installazione di ExcelAddIn. Ad esempio, può essere utile controllare se l'applicazione di destinazione Office è installata.

### <a name="to-build-the-setup-project"></a>Per compilare il progetto di installazione

1. Nella finestra di **Esplora soluzioni** fare clic con il pulsante destro del mouse sul **progetto OfficeAddInSetup** e scegliere **Compila.**
2. Usando **Windows,** passare alla directory di output del progetto **OfficeAddInSetup** e passare alla cartella Release o Debug, a seconda della configurazione della build selezionata. Copiare tutti i file dalla cartella in un percorso a cui gli utenti possono accedere.

Per testare l'installazione di ExcelAddIn

1. Passare al percorso in cui è stato copiato **OfficeAddInSetup.**
2. Fare doppio clic sul file setup.exe per installare il **componente aggiuntivo OfficeAddInSetup.** Accettare le condizioni di licenza software visualizzate e completare l'installazione guidata per installare il componente aggiuntivo nel computer utente.

La Excel Office deve essere installata ed eseguita dal percorso specificato durante l'installazione.

## <a name="additional-requirements-for-document-level-solutions"></a>Requisiti aggiuntivi per le soluzioni a livello di documento

La distribuzione di soluzioni a livello di documento richiede alcuni passaggi di configurazione diversi nel Windows di installazione del programma di installazione.

Ecco un elenco dei passaggi di base necessari per distribuire una soluzione a livello di documento:

- Creare il Visual Studio di installazione Project.
- Aggiungere l'output primario della soluzione a livello di documento. L'output primario include anche Microsoft Office documento.
- Aggiungere i manifesti di distribuzione e dell'applicazione come file loose.
- Escludere i componenti dipendenti dal pacchetto del programma di installazione (ad eccezione di eventuali assembly di utilità).
- Configurare i pacchetti dei prerequisiti.
- Configurare le condizioni di avvio.
- Compilare il progetto di installazione e copiare i risultati nel percorso di distribuzione.
- Distribuire la soluzione a livello di documento nel computer utente eseguendo il programma di installazione.
- Se necessario, aggiornare le proprietà personalizzate del documento.

### <a name="changing-the-location-of-the-deployed-document"></a>Modifica del percorso del documento distribuito

Le proprietà all'interno Office documento vengono usate per individuare soluzioni a livello di documento. Se il documento viene installato nella stessa cartella dell'assembly VSTO, non sono necessarie modifiche. Tuttavia, se è installato in una cartella diversa, queste proprietà dovranno essere aggiornate durante l'installazione.

Per altre informazioni su queste proprietà del documento, vedere [Cenni preliminari sulle proprietà personalizzate dei documenti.](custom-document-properties-overview.md)

Per modificare queste proprietà, è necessario usare un'azione personalizzata durante l'installazione.

L'esempio seguente usa una soluzione a livello di documento denominata ExcelWorkbookProject e un progetto di installazione denominato ExcelWorkbookSetup. Il progetto ExcelWorkbookSetup viene configurato usando gli stessi passaggi descritti in precedenza, ad eccezione dell'impostazione delle chiavi del Registro di sistema.

Per aggiungere il progetto di azione personalizzata alla soluzione Visual Studio personalizzata

1. Aggiungere un nuovo progetto console .NET alla soluzione facendo clic con il pulsante destro del mouse sul Office **distribuzione** Project documento nella **Esplora soluzioni**
2. Espandere **Aggiungi** e fare clic **su Nuovo Project**.
3. Selezionare il modello App console e assegnare al progetto il **nome AddCustomizationCustomAction**.

    ![Screenshot della Esplora soluzioni - AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **Figura 12: Esplora soluzioni - AddCustomizationCustomAction**

4. Aggiungere un riferimento a questi assembly:
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

Per aggiungere la personalizzazione al documento, è necessario disporre dell'ID soluzione della VSTO a livello di documento. Questo valore viene recuperato dal file Visual Studio progetto.

Per recuperare l'ID soluzione

1. Scegliere **Compila** soluzione  dal menu Compila per compilare la soluzione a livello di documento e aggiungere la proprietà ID soluzione al file di progetto.
2. Nella finestra di **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto a livello di documento **ExcelWorkbookProject**
3. Fare **clic su ScaricaProgetto** per accedere al file di progetto dall'interno Visual Studio.

    ![Screenshot della Esplora soluzioni di un documento Excel documento](media/setup-project-figure-16.jpg)

    **Figura 13: Scaricamento della Excel documento**

4. Nel **Esplora soluzioni** fare clic con il pulsante destro del mouse su **ExcelWorkbookProject** e scegliere **ModificaExcelWorkbookProject.vbproj** o Modifica **ExcelWorkbookProject.csproj.**
5. Nell'editor **ExcelWorkbookProject** individuare **l'elemento SolutionID** all'interno dell'elemento **PropertyGroup.**
6. Copiare il valore GUID di questo elemento.

    ![Recupero dell'ID soluzione](media/setup-project-figure-17.jpg)

    **Figura 14: Recupero dell'ID soluzione**

7. Nella finestra di **Esplora soluzioni** fare clic con il pulsante destro del mouse **su ExcelWorkbookProject** e scegliere **Ricarica** Project .
8. Fare **clic su** Sì nella finestra di dialogo visualizzata per chiudere l'editor **ExcelWorkbookProject.**
9. **L'ID soluzione** verrà usato in Installa azione personalizzata.

L'ultimo passaggio consiste nel configurare l'azione personalizzata per la **procedura di** installazione **e** disinstallazione.

### <a name="to-configure-the-setup-project"></a>Per configurare il progetto di installazione

1. Nella finestra **di Esplora soluzioni** fare clic con il pulsante destro del mouse su **ExcelWorkbookSetup**, espandere **Aggiungi** e fare clic Project **Output**.
2. Nella finestra **di Project aggiungi gruppo di output** fare clic su **AddCustomizationCustomAction** **nell'elenco** Project di output.
3. Selezionare **Output primario e** fare clic su **OK** per chiudere la finestra di dialogo e aggiungere l'assembly contenente l'azione personalizzata al progetto di installazione.

    ![Screenshot dell'azione personalizzata Manifesto del documento - Aggiungi Project gruppo di output](media/setup-project-figure-18.jpg)

    **Figura 15: Azione personalizzata del manifesto del documento - Aggiungere Project output del documento**

4. Nella finestra di **Esplora soluzioni** fare clic con il pulsante destro **del mouse su ExcelWorkbookSetup**.
5. Espandere **Visualizza e** fare clic su Azioni **personalizzate.**
6. Nell'editor **Azioni personalizzate (ExcelWorkbookSetup)** fare clic con il pulsante destro **del mouse su Azioni personalizzate** e scegliere Aggiungi azione **personalizzata.**
7. Nella finestra **di dialogo Seleziona elemento in**  Project fare clic su Cartella applicazione nell'elenco **Cerca in**. Selezionare **Output primario da AddCustomizationCustomAction(active) e** fare clic su **OK** per aggiungere l'azione personalizzata al passaggio Installa.
8. Nel nodo **Installa fare** clic con il pulsante destro del mouse su Output primario da **AddCustomizationCustomAction(Active)** e scegliere **Rinomina.** Assegnare all'azione personalizzata **il nome Copy document to Documenti e associare la personalizzazione**.
9. Nel nodo **Disinstalla fare** clic con il pulsante destro del mouse su Output primario **da AddCustomizationCustomAction(Active)** e scegliere **Rinomina.** Assegnare all'azione **personalizzata il nome Remove document dalla cartella Documents**.

    ![Screenshot della finestra Azioni personalizzate del manifesto del documento](media/setup-project-figure-19.jpg)

    **Figura 16: Azioni personalizzate del manifesto del documento**

10. Nell'editor **Azioni personalizzate (ExcelWorkbookSetup)** fare clic con il pulsante destro del mouse su Copia documento in Documenti allegare la **personalizzazione** e scegliere **Finestra Proprietà.**
11. Nella finestra **Proprietà CustomActionData**  immettere il percorso della DLL di personalizzazione, il manifesto della distribuzione e il percorso del Microsoft Office personalizzato. È necessario anche SolutionID.
12. Se si desidera registrare eventuali errori di installazione in un file, includere un parametro LogFile.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Screenshot dell'azione personalizzata per copiare un documento Documenti Finestra Proprietà](media/setup-project-figure-20.jpg)

    **Figura 17: Azione personalizzata per copiare un documento Documenti**

13. L'azione personalizzata per la disinstallazione richiede il nome del documento, che è possibile specificare usando lo stesso parametro documentLocation in **CustomActionData**

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. Compilare e distribuire **il progetto ExcelWorkbookSetup.**
15. Cercare nella **Documenti** e aprire il file ExcelWorkbookProject.xlsx.

## <a name="additional-resources"></a>Risorse aggiuntive

[Procedura: Installare il runtime Visual Studio Tools per Office](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Office Primary Interop Assemblies](office-primary-interop-assemblies.md)

[Voci del Registro di sistema VSTO componenti aggiuntivi](registry-entries-for-vsto-add-ins.md)

[Custom Document Properties Overview](custom-document-properties-overview.md)

[Specifica di aree del modulo nel Registro Windows dati](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Granting Trust to Documents](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>Informazioni sugli autori

Wouter van Vugt è un Microsoft MVP con tecnologie Open XML Office e un consulente indipendente che si concentra sulla creazione di Office Business Applications (OBA) con SharePoint, Microsoft Office e tecnologie .NET correlate.
Wouter è un collaboratore frequente ai siti della community di sviluppatori, ad esempio [MSDN.](/previous-versions/office/developer/office-2007/bb879915(v=office.12)) Ha pubblicato diversi white paper e articoli, nonché un libro disponibile on line intitolato Open XML: Explained e-book.
Wouter è il cofondatore di Code-Counsel, una società olandese che si concentra sulla distribuzione di contenuti tecnici all'avanguardia tramite diversi canali. Per altre informazioni su Wouter, leggere il suo blog.

Ted Pattison è SharePoint MVP, autore, trainer e il creatore di Ted Pattison Group. Nell'autunno del 2005, Ted è stato assunto dal gruppo Developer Platform Evangelism di Microsoft per creare il programma di formazione per sviluppatori Ascend per Windows SharePoint Services 3.0 e Microsoft Office SharePoint Server 2007. Da quel momento, Ted è stato interamente incentrato sull'istruzione degli sviluppatori professionisti SharePoint tecnologie del 2007. Ted ha terminato la scrittura di un libro per Microsoft Press intitolato Inside Windows SharePoint Services 3.0 che illustra come usare SharePoint come piattaforma di sviluppo per la creazione di soluzioni aziendali. Ted scrive anche una colonna incentrata sugli sviluppatori per MSDN Magazine intitolata Office Space.
