---
title: Distribuzione di una soluzione VSTO con Windows Installer
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a6fd2824ae10ad36a7ed50250620e98575e9ea60
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585693"
---
# <a name="deploying-a-vsto-solution-using-windows-installer"></a>Distribuzione di una soluzione VSTO con Windows Installer

## <a name="summary"></a>Riepilogo

Informazioni su come distribuire un componente aggiuntivo Microsoft Visual Studio Tools per Office (VSTO) o una soluzione a livello di documento usando un progetto Programma di installazione di Visual Studio.

Vugt di stato del codice, code Counsel

Ted Pattison, Ted Pattison Group

Questo articolo è stato aggiornato da Microsoft con l'autorizzazione degli autori originali.

**Si applica a:** Strumenti di Visual Studio per Office, Microsoft Office, Microsoft Visual Studio.

## <a name="overview"></a>Panoramica

È possibile sviluppare una soluzione VSTO e distribuire la soluzione usando un pacchetto di Windows Installer. Questa discussione include i passaggi per la distribuzione di un componente aggiuntivo di Office semplice.

## <a name="deployment-methods"></a>Metodi di distribuzione

ClickOnce può essere usato facilmente per creare configurazioni per i componenti aggiuntivi e le soluzioni. Tuttavia, non può installare i componenti aggiuntivi che richiedono privilegi amministrativi, ad esempio i componenti aggiuntivi a livello di computer.

Per installare i componenti aggiuntivi che richiedono privilegi amministrativi, è possibile usare Windows Installer ma è necessario più lavoro per creare la configurazione.

Per una panoramica su come distribuire una soluzione VSTO usando ClickOnce, vedere [distribuire una soluzione Office tramite ClickOnce](deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Distribuzione di soluzioni Office destinate al runtime di VSTO

I pacchetti ClickOnce e Windows Installer devono eseguire le stesse attività rudimentali quando si installa una soluzione Office.

1. Installare i componenti dei prerequisiti nel computer dell'utente.
2. Distribuire i componenti specifici per la soluzione.
3. Per i componenti aggiuntivi, creare voci del registro di sistema.
4. Considerare attendibile la soluzione per consentirne l'esecuzione.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Componenti dei prerequisiti necessari nel computer di destinazione

Di seguito è riportato l'elenco di software che deve essere installato nel computer per eseguire soluzioni VSTO:

- Microsoft Office 2010 o versione successiva.
- Microsoft .NET Framework 4 o versione successiva.
- Microsoft Visual Studio 2010 Tools per Office Runtime.
  Il runtime fornisce un ambiente che gestisce i componenti aggiuntivi e le soluzioni a livello di documento. Una versione del runtime viene fornita con Microsoft Office, ma potrebbe essere necessario ridistribuire una versione specifica con il componente aggiuntivo.
- Assembly di interoperabilità primari per Microsoft Office, se non si utilizzano tipi di interoperabilità incorporati.
- Tutti gli assembly di utilità a cui fanno riferimento i progetti.

### <a name="specific-components-for-the-solution"></a>Componenti specifici per la soluzione

Il pacchetto del programma di installazione deve installare questi componenti nel computer dell'utente:

- Documento di Microsoft Office, se si crea una soluzione a livello di documento.
- Assembly di personalizzazione e tutti gli assembly necessari.
- Componenti aggiuntivi, ad esempio i file di configurazione.
- Manifesto dell'applicazione (. manifest).
- Manifesto di distribuzione (con estensione VSTO).

### <a name="registry-entries-for-add-ins"></a>Voci del registro di sistema per i componenti aggiuntivi

Microsoft Office USA le voci del registro di sistema per individuare e caricare i componenti aggiuntivi. Queste voci del registro di sistema devono essere create come parte del processo di distribuzione. Per altre informazioni su queste voci del registro di sistema, vedere [voci del registro di sistema per i componenti aggiuntivi VSTO](registry-entries-for-vsto-add-ins.md).

I componenti aggiuntivi di Outlook che visualizzano aree del modulo personalizzate richiedono voci aggiuntive del registro di sistema che consentono di identificare le aree del modulo. Per altre informazioni sulle voci del registro di sistema, vedere [voci del registro di sistema per le aree del modulo Outlook](registry-entries-for-vsto-add-ins.md#OutlookEntries).

Le soluzioni a livello di documento non richiedono alcuna voce del registro di sistema. Al contrario, le proprietà all'interno del documento vengono usate per individuare la personalizzazione. Per altre informazioni su queste proprietà, vedere [Cenni preliminari sulle proprietà personalizzate dei documenti](custom-document-properties-overview.md).

### <a name="trusting-the-vsto-solution"></a>Attendibilità della soluzione VSTO

Per consentire l'esecuzione di una personalizzazione, una soluzione deve essere considerata attendibile dal computer. Il componente aggiuntivo può essere considerato attendibile firmando il manifesto con un certificato, creando una relazione di trust con un elenco di inclusione oppure installando il manifesto in un percorso attendibile nel computer.

Per ulteriori informazioni su come ottenere un certificato per la firma, vedere [ClickOnce Deployment and Authenticode](../deployment/clickonce-and-authenticode.md). Per altre informazioni sull'attendibilità delle soluzioni, vedere [attendibilità delle soluzioni Office tramite gli elenchi di inclusione](trusting-office-solutions-by-using-inclusion-lists.md). È possibile aggiungere una voce dell'elenco di inclusione con un'azione personalizzata nel file di Windows Installer. Per altre informazioni sull'abilitazione dell'elenco di inclusione, vedere [procedura: configurare la sicurezza dell'elenco di inclusione](how-to-configure-inclusion-list-security.md).

Se nessuna delle due opzioni viene utilizzata, all'utente viene visualizzata una richiesta di attendibilità per consentire loro di decidere se considerare attendibile la soluzione.

Per ulteriori informazioni sulla sicurezza relativa alle soluzioni a livello di documento, vedere [concessione dell'attendibilità ai documenti](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Creazione di un programma di installazione di base

I modelli di progetto di installazione e distribuzione sono inclusi nell'estensione per i progetti di installazione di [Microsoft Visual Studio](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) disponibile per il download.

Per creare un programma di installazione per una soluzione Office, è necessario eseguire queste attività:

- Aggiungere i componenti della soluzione Office che verrà distribuita.
- Per i componenti aggiuntivi a livello di applicazione, configurare le chiavi del registro di sistema.
- Configurare i componenti dei prerequisiti in modo che possano essere installati nei computer degli utenti finali.
- Configurare le condizioni di avvio per verificare che siano disponibili i componenti prerequisiti necessari. Le condizioni di avvio possono essere usate per bloccare l'installazione se non sono installati tutti i prerequisiti necessari.

Il primo passaggio consiste nel creare il progetto di installazione.

### <a name="to-create-the-addin-setup-project"></a>Per creare il progetto di installazione del componente aggiuntivo

1. Aprire il progetto di componente aggiuntivo di Office che si desidera distribuire. Per questo esempio viene usato un componente aggiuntivo di Excel denominato ExcelAddIn.
2. Con il progetto di Office aperto, nel menu **file** espandere **Aggiungi** , quindi fare clic su **nuovo progetto** per aggiungere un nuovo progetto.
::: moniker range="=vs-2017"
3. Nella finestra di dialogo **Aggiungi nuovo progetto** espandere **altri tipi di progetto** nel riquadro **Tipi progetto** , quindi espandere **installazione e distribuzione** , quindi selezionare **programma di installazione di Visual Studio**.
4. Nel riquadro **modelli** selezionare progetto di **installazione** dal gruppo modelli di **Visual Studio installati** .
::: moniker-end
::: moniker range="=vs-2019"
3. Nella finestra di dialogo **Aggiungi nuovo progetto** selezionare il modello di **progetto di installazione** .
4. Fare clic su **Avanti**.
::: moniker-end

5. Nella casella **nome** digitare **OfficeAddInSetup**.
::: moniker range="=vs-2017"
6. Fare clic su **Apri** per creare il nuovo progetto di installazione.
::: moniker-end
::: moniker range="=vs-2019"
6. Fare clic su **Crea** per creare il nuovo progetto di installazione.
::: moniker-end

Visual Studio apre il file System Explorer per il nuovo progetto di installazione. Esplora file System consente di aggiungere file al progetto di installazione.

   ![Screenshot di Esplora file System per il progetto di installazione](media/setup-project-figure-1.png)

   **Figura 1: Esplora file System per il progetto di installazione**

Il progetto di installazione deve distribuire ExcelAddIn. Per configurare il progetto di installazione per questa attività, è possibile aggiungere l'output del progetto ExcelAddIn al progetto di installazione.

### <a name="to-add-the-exceladdin-project-output"></a>Per aggiungere l'output del progetto ExcelAddIn

1. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse su **OfficeAddInSetup**, scegliere **Aggiungi** e quindi **output progetto**.
2. Nella finestra di dialogo **Aggiungi gruppo di output del progetto** selezionare **ExcelAddIn** dall'elenco progetto e **output primario**.
3. Fare clic su **OK** per aggiungere l'output del progetto al progetto di installazione.

    ![Screenshot della finestra di dialogo Aggiungi gruppo di output del progetto di installazione](media/setup-project-figure-2.png)

    **Figura 2: finestra di dialogo Imposta progetto Aggiungi gruppo di output progetto**

Il progetto di installazione deve distribuire il manifesto di distribuzione e il manifesto dell'applicazione. Aggiungere questi due file al progetto di installazione come file autonomi dalla cartella di output del progetto ExcelAddIn.

### <a name="to-add-the-deployment-and-application-manifests"></a>Per aggiungere i manifesti dell'applicazione e della distribuzione

1. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse su **OfficeAddInSetup**, scegliere **Aggiungi**e quindi fare clic su **file**.
2. Nella finestra di dialogo **Aggiungi file** passare alla directory di output **ExcelAddIn** . In genere, la directory di output è la sottocartella **bin \\ Release** della directory radice del progetto, a seconda della configurazione di compilazione selezionata.
3. Selezionare i file **ExcelAddIn. VSTO** e **ExcelAddIn.dll. manifest** e fare clic su **Apri** per aggiungere questi due file al progetto di installazione.

    ![Screenshot dei manifesti dell'applicazione e della distribuzione in Esplora soluzioni](media/setup-project-figure-3.jpg)

    **Figura 3: manifesti dell'applicazione e della distribuzione per il componente aggiuntivo in Esplora soluzioni**

Il riferimento a ExcelAddIn include tutti i componenti richiesti da ExcelAddIn. Questi componenti devono essere esclusi e distribuiti usando i pacchetti prerequisiti per consentirne la registrazione corretta. Inoltre, le condizioni di licenza software devono essere visualizzate e accettate prima dell'inizio dell'installazione.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>Per escludere le dipendenze del progetto ExcelAddIn

1. Nel **Esplora soluzioni**, nel nodo **OfficeAddInSetup** , selezionare tutti gli elementi di dipendenza sotto l'elemento **dipendenze rilevate** , ad eccezione di **Microsoft .NET Framework** o di qualsiasi assembly che termina con ** \*.Utilities.dll**. Gli assembly delle utilità sono progettati per essere distribuiti insieme all'applicazione.
2. Fare clic con il pulsante destro del mouse sul gruppo e scegliere **Proprietà**.
3. Nella finestra **Proprietà** modificare la proprietà **Exclude** in **true** per escludere gli assembly dipendenti dal progetto di installazione. Assicurarsi di non escludere gli assembly di utilità.

    ![Screenshot del Esplora soluzioni che mostra le dipendenze da escludere](media/setup-project-figure-4.jpg)

    **Figura 4: esclusione delle dipendenze**

È possibile configurare il pacchetto di Windows Installer per installare i componenti dei prerequisiti aggiungendo un programma di installazione, noto anche come programma di avvio automatico. Questo programma di installazione può installare i componenti dei prerequisiti, un processo denominato bootstrap.

Per **ExcelAddIn**, questi prerequisiti devono essere installati prima che il componente aggiuntivo possa essere eseguito correttamente:

- La versione di Microsoft .NET Framework a cui è destinata la soluzione Office.
- Microsoft Visual Studio 2010 Tools per Office Runtime.

Per configurare i componenti dipendenti come prerequisiti

1. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto **OfficeAddInSetup** e scegliere **proprietà**.
2. Verrà visualizzata la finestra di dialogo **pagine delle proprietà di OfficeAddInSetup** .
3. Fare clic sul pulsante **prerequisiti** .
4. Nella finestra di dialogo Prerequisiti selezionare la versione corretta del .NET Framework e il Microsoft Visual Studio Tools per Office Runtime.

    ![Screenshot della finestra di dialogo Prerequisiti](media/setup-project-figure-5.png)

    **Figura 5: finestra di dialogo Prerequisiti**

    > [!NOTE]
    >Alcuni dei pacchetti prerequisiti configurati nel progetto di installazione di Visual Studio dipendono dalla configurazione della build selezionata. È necessario selezionare i componenti dei prerequisiti corretti per ogni configurazione di compilazione utilizzata.

Microsoft Office individua i componenti aggiuntivi utilizzando le chiavi del registro di sistema. Le chiavi nell'hive dell' \_ \_ utente corrente di HKEY vengono usate per registrare il componente aggiuntivo per ogni singolo utente. \_ \_ Per registrare il componente aggiuntivo per tutti gli utenti del computer vengono usate le chiavi nell'hive locale del computer HKEY. Per altre informazioni sulle chiavi del registro di sistema, vedere [voci del registro di sistema per i componenti aggiuntivi VSTO](registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-the-registry"></a>Per configurare il registro di sistema

1. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse su **OfficeAddInSetup**.
2. Espandi **visualizzazione**.
3. Fare clic su **Registro di sistema** per aprire la finestra Editor del registro di sistema.
4. Nell'editor **del registro di sistema (OfficeAddInSetup)** espandere **HKEY \_ Local \_ Machine** e quindi **software**.
5. Eliminare la chiave del ** \[ produttore \] **, disponibile in **HKEY \_ Local \_ Machine \\ software**.
6. Espandere **HKEY \_ Current \_ User** e quindi **software**.
7. Elimina la chiave del ** \[ produttore \] ** disponibile in **HKEY \_ Current \_ User \\ software**.
8. Per aggiungere chiavi del registro di sistema per l'installazione del componente aggiuntivo, fare clic con il pulsante destro del mouse sulla chiave **hive User/Machine** , quindi scegliere **nuova chiave**. Usare il **software** di testo per il nome della nuova chiave. Fare clic con il pulsante destro del mouse sulla chiave **software** appena creata e creare una nuova chiave con il testo **Microsoft**.
9. Utilizzare un processo simile per creare l'intera gerarchia di chiavi necessaria per la registrazione del componente aggiuntivo:

    **Utente/computer hive \\ software di \\ Microsoft \\ Office \\ Excel \\ AddIns \\ chiave SampleCompany. ExcelAddIn**

    Il nome della società viene spesso utilizzato come prefisso per il nome del componente aggiuntivo per garantire l'univocità.

10. Fare clic con il pulsante destro del mouse sulla chiave **chiave SampleCompany. ExcelAddIn** , scegliere **nuovo**e fare clic su **valore stringa**. Utilizzare la **Descrizione** del testo per il nome.
11. Usare questo passaggio per aggiungere altri tre valori:
    - **FriendlyName** di tipo **String**
    - **LoadBehavior** di tipo **DWORD**
    - **Manifesto** di tipo **stringa**

12. Fare clic con il pulsante destro del mouse sul valore **Description** nell'editor del registro di sistema, quindi scegliere **finestra Proprietà**. Nella **finestra Proprietà**immettere il **componente aggiuntivo demo di Excel** per la proprietà valore.
13. Selezionare la chiave **FriendlyName** nell'editor del registro di sistema. Nella **finestra Proprietà**modificare la proprietà **value** in **componente aggiuntivo demo di Excel**.
14. Selezionare la chiave **LoadBehavior** nell'editor del registro di sistema. Nella **finestra Proprietà**modificare la proprietà **value** in **3.** Il valore 3 per LoadBehavior indica che il componente aggiuntivo deve essere caricato all'avvio dell'applicazione host. Per altre informazioni sul comportamento del caricamento, vedere [voci del registro di sistema per i componenti aggiuntivi VSTO](registry-entries-for-vsto-add-ins.md).

15. Selezionare la chiave del **manifesto** nell'editor del registro di sistema. Nella **finestra Proprietà**modificare la proprietà **value** in **file:///[TARGETDIR] ExcelAddIn. VSTO | vstolocal**

    ![Screenshot dell'editor del registro di sistema](media/setup-project-figure-6.png)

    **Figura 6: impostazione delle chiavi del registro di sistema**

      Il runtime di VSTO usa questa chiave del registro di sistema per individuare il manifesto di distribuzione. La macro [TARGETDIR] verrà sostituita con la cartella in cui è installato il componente aggiuntivo. La macro includerà il carattere finale, quindi il nome file del manifesto di distribuzione deve essere ExcelAddIn. VSTO senza il carattere \.
      Il suffisso **vstolocal** indica al runtime di VSTO che il componente aggiuntivo deve essere caricato da questo percorso anziché dalla cache ClickOnce. La rimozione di questo suffisso causerà la copia della personalizzazione nella cache ClickOnce da parte del runtime.

   >[!WARNING]
   >È necessario prestare molta attenzione all'editor del registro di sistema in Visual Studio. Se, ad esempio, si imposta accidentalmente DeleteAtUninstall per la chiave errata, è possibile eliminare una parte attiva del registro di sistema, lasciando il computer utente in uno stato incoerente, o addirittura peggiore, danneggiato.

le versioni di Office a 64 bit useranno l'hive del registro di sistema a 64 bit per cercare i componenti aggiuntivi. Per registrare i componenti aggiuntivi nell'hive del registro di sistema a 64 bit, la piattaforma di destinazione del progetto di installazione deve essere impostata solo su 64 bit.

1. Selezionare il progetto **OfficeAddInSetup** in Esplora soluzioni.
2. Passare alla finestra **Proprietà** e impostare la proprietà **TargetPlatform** su **x64**.

Se si installa un componente aggiuntivo per le versioni di Office a 32 bit e a 64 bit, sarà necessario creare due pacchetti MSI distinti. Uno per 32 bit e uno per 64 bit.

  ![Screenshot della finestra proprietà che mostra la piattaforma di destinazione per la registrazione dei componenti aggiuntivi con Office a 64 bit](media/setup-project-figure-7.jpg)

  **Figura 7: piattaforma di destinazione per la registrazione di componenti aggiuntivi con Office a 64 bit**

Se il pacchetto MSI viene usato per installare il componente aggiuntivo o la soluzione, è possibile che venga installato senza che siano installati i prerequisiti necessari. È possibile utilizzare le condizioni di avvio nel file MSI per impedire l'installazione del componente aggiuntivo se i prerequisiti non sono installati.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>Configurare una condizione di avvio per rilevare il runtime di VSTO

1. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse su **OfficeAddInSetup**.
2. Espandi **visualizzazione**.
3. Fare clic su **condizioni di avvio**.
4. Nell'editor **condizioni di avvio (OfficeAddInSetup)** fare clic con il pulsante destro del mouse **su requisiti nel computer di destinazione**e quindi fare clic su **Aggiungi condizione di avvio del registro di sistema**. Questa condizione di ricerca può eseguire ricerche nel registro di sistema per una chiave installata dal runtime di VSTO. Il valore della chiave è quindi disponibile per le varie parti del programma di installazione tramite una proprietà denominata. La condizione di avvio utilizza la proprietà definita dalla condizione di ricerca per verificare la presenza di un determinato valore.
5. Nell'editor **condizioni di avvio (OfficeAddInSetup)** selezionare la condizione **di ricerca Cerca RegistryEntry1** , fare clic con il pulsante destro del mouse sulla condizione e selezionare **finestra Proprietà**.

6. Nella finestra **Proprietà** impostare queste proprietà:
   1. Impostare il valore di **(Name)** per la **ricerca del runtime VSTO 2010**.
   2. Modificare il valore della **Proprietà** in **VSTORUNTIMEREDIST**.
   3. Impostare il valore di **chiave** su **software \\ Microsoft \\ VSTO Runtime Setup \\ v4R**
   4. Lasciare la proprietà **radice** impostata su **vsdrrHKLM**.
   5. Modificare la proprietà **value** in **Version**.

7. Nell'editor **condizioni di avvio (OfficeAddInSetup)** selezionare la condizione di avvio **condition1** , fare clic con il pulsante destro del mouse sulla condizione e selezionare **finestra Proprietà**.
8. Nella finestra Proprietà impostare queste proprietà:
   1. Impostare **(Name)** per **verificare la disponibilità del Runtime di VSTO 2010**.
   2. Modificare il valore della **condizione** in **VSTORUNTIMEREDIST \> = "10.0.30319"**
   3. Lasciare vuota la proprietà **InstallUrl** .
   4. Impostare il **messaggio** su **Visual Studio 2010 Tools per Office Runtime non installato. Eseguire Setup.exe per installare il componente aggiuntivo**.

        ![Screenshot della finestra proprietà per verificare la condizione di avvio della disponibilità di runtime](media/setup-project-figure-8.jpg)

        **Figura 8: finestra delle proprietà per la verifica della condizione di avvio della disponibilità di runtime**

 La condizione di avvio precedente verifica in modo esplicito la presenza del runtime di VSTO quando viene installato dal pacchetto del programma di avvio automatico.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Configurare una condizione di avvio per rilevare il runtime di VSTO installato da Office

1. Nell'editor **condizioni di avvio (OfficeAddInSetup)** fare clic con il pulsante destro del mouse su **Cerca computer di destinazione**e quindi scegliere **Aggiungi ricerca Registro di sistema**.
2. Selezionare la condizione **di ricerca RegistryEntry1** , fare clic con il pulsante destro del mouse sulla condizione e selezionare **finestra Proprietà**.
3. Nella finestra **Proprietà** impostare queste proprietà:
    1. Impostare il valore di **(Name)** per la **ricerca di Office VSTO Runtime**.
    2. Modificare il valore della **Proprietà** in **OfficeRuntime**.
    3. Impostare il valore di **chiave** su **software \\ Microsoft \\ VSTO Runtime Setup \\ V4**.
    4. Lasciare la proprietà **radice** impostata su **vsdrrHKLM**.
    5. Modificare la proprietà **value** in **Version**.

4. Nell'editor **condizioni di avvio (OfficeAddInSetup)** selezionare la condizione di avvio della **disponibilità di Runtime di VSTO 2010** definita in precedenza, fare clic con il pulsante destro del mouse sulla condizione e selezionare **finestra Proprietà**.

5. Modificare il valore della proprietà **Condition** in **VSTORUNTIMEREDIST \> = "10.0.30319" o OFFICERUNTIME \> = "10.0.21022"**. I numeri di versione potrebbero essere diversi a seconda delle versioni del runtime richieste dal componente aggiuntivo.

    ![Screenshot delle finestre delle proprietà per la condizione di avvio](media/setup-project-figure-9.jpg)
  
    **Figura 9: finestre delle proprietà per verificare la disponibilità di runtime tramite Redist o la condizione di avvio di Office**

Se un componente aggiuntivo è destinato .NET Framework 4 o versione successiva, i tipi all'interno degli assembly di interoperabilità primari (PIA), a cui viene fatto riferimento, possono essere incorporati nell'assembly VSTO.

Per verificare se i tipi di interoperabilità verranno incorporati nel componente aggiuntivo attenendosi alla procedura seguente:

1. Espandere il nodo riferimenti in Esplora soluzioni
2. Selezionare uno dei riferimenti di PIA, ad esempio **Office**.
3. Per visualizzare le finestre delle proprietà, premere F4 o selezionare proprietà nel menu di scelta rapida assembly.
4. Verificare il valore della proprietà **Incorpora tipi di interoperabilità**.

Se il valore è impostato su **true**, i tipi vengono incorporati ed è possibile passare alla sezione [**per compilare il progetto di installazione**](#to-build-the-setup-project) .

Per altre informazioni, vedere [equivalenza del tipo e tipi di interoperabilità incorporati](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Per configurare le condizioni di avvio per rilevare che per i Pia di Office

1. Nell'editor **condizioni di avvio (OfficeAddInSetup)** fare clic con il pulsante destro del mouse **su requisiti nel computer di destinazione**e quindi **scegliere Aggiungi Windows Installer condizione di avvio**. Questa condizione di avvio cerca un assembly di interoperabilità primario di Office cercando l'ID componente specifico.
2. Fare clic con il pulsante destro del mouse su **Cerca Component1** e scegliere **finestra Proprietà** per visualizzare le proprietà della condizione di avvio.
3. Nella **finestra Proprietà**impostare le proprietà seguenti:

    1. Modificare il valore della proprietà **(Name)** per cercare l'assembly di interoperabilità **primario condiviso di Office**
    2. Modificare il valore di **ComponentID** in ID componente per il componente di Office che si sta usando. È possibile trovare l'elenco di ID componente nella tabella seguente, ad esempio **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}**.
    3. Modificare il valore della proprietà **Property** in **HASSHAREDPIA**.

4. Nell'editor **condizioni di avvio (OfficeAddInSetup)** fare clic con il pulsante destro del mouse su **condition1** e quindi scegliere **finestra Proprietà** per visualizzare le proprietà della condizione di avvio.

5. Modificare le proprietà di **condition1**:

    1. Modificare **(Name)** per **verificare la disponibilità di Pia condiviso di Office**.
    2. Modificare la **condizione** in **HASSHAREDPIA**.
    3. Lasciare vuoto **InstallUrl** .
    4. Modificare il **messaggio** in **un componente necessario per l'interazione con Excel non è disponibile. Eseguire setup.exe**.

    ![Screenshot della finestra proprietà per la verifica della condizione di avvio dell'assembly di interoperabilità primario condivisa di Office](media/setup-project-figure-10.jpg)
  
    **Figura 10: finestra delle proprietà per la verifica della condizione di avvio del PIA condiviso di Office**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>ID dei componenti degli assembly di interoperabilità primari per Microsoft Office

|Assembly di interoperabilità primario|Office 2010|Office 2013|Office 2013 (64 bit)|Office 2016|Office 2016 (64 bit)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26E4FC2223FF}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153F732-D670-4E44-8AB7-500F2B576BDA}|{0F825A16-25B2-4771-A497-FC8AF3B355D8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1D844339-3DAE-413E-BC13-62D6A52816B2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824A03F-28CC-4371-BC54-93D15EFC1E7F}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|
|PowerPoint|{EECBA6B8-3A62-44AD-99EB-8666265466F9}|{813139AD-6DAB-4DDD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3EA123B5-6316-452E-9D51-A489E06E2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2CC0B221-22D2-4C15-A9FB-DE818E51AF75}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|
|Word|{8B74A499-37F8-4DEA-B5A0-D72FC501CEFA}|{9FE736B7-B1EE-410C-8D07-082891C3DAC8}|{13C07AF5-B206-4A48-BB5B-B8022333E3CA}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|
|Microsoft Forms 2,0|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52DA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510}|-|-|
|smart tag|{7102C98C-EF47-4F04-A227-FE33650BF954}|{487A7921-EB3A-4262-BB5B-A5736B732486}|{74EFC1F9-747D-4867-B951-EFCF29F51AF7}|-|-|
|Office condiviso|{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E}|{76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|
|Project|{957A4EC0-E67B-4E86-A383-6AF7270B216A}|{1C50E422-24FA-44A9-A120-E88280C8C341}|{706D7F44-8231-489D-9B25-3025ADE9F114}|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![Screenshot delle condizioni di avvio finali](media/setup-project-figure-11.jpg)

  **Figura 11: Condizioni di avvio finale**

È possibile affinare ulteriormente le condizioni di avvio per l'installazione di ExcelAddIn. Ad esempio, potrebbe essere utile verificare se è installata l'applicazione di Office di destinazione effettiva.

### <a name="to-build-the-setup-project"></a>Per compilare il progetto di installazione

1. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto **OfficeAddInSetup** , quindi scegliere **Compila**.
2. Utilizzando **Esplora risorse**, passare alla directory di output del progetto **OfficeAddInSetup** e passare alla cartella Release o debug, a seconda della configurazione di compilazione selezionata. Copiare tutti i file dalla cartella in un percorso a cui gli utenti possono accedere.

Per testare l'installazione di ExcelAddIn

1. Passare al percorso in cui è stato copiato **OfficeAddInSetup** .
2. Fare doppio clic sul file setup.exe per installare il componente aggiuntivo **OfficeAddInSetup** . Accettare le condizioni di licenza software visualizzate e completare l'installazione guidata per installare il componente aggiuntivo nel computer dell'utente.

La soluzione Excel Office deve essere installata ed eseguita dal percorso specificato durante l'installazione.

## <a name="additional-requirements-for-document-level-solutions"></a>Requisiti aggiuntivi per le soluzioni a livello di documento

Per la distribuzione di soluzioni a livello di documento sono necessari alcuni passaggi di configurazione diversi nel progetto di installazione di Windows Installer.

Ecco un elenco dei passaggi di base necessari per distribuire una soluzione a livello di documento:

- Creare il progetto di installazione di Visual Studio.
- Aggiungere l'output primario della soluzione a livello di documento. L'output primario include anche il documento Microsoft Office.
- Aggiungere i manifesti dell'applicazione e di distribuzione come file separati.
- Escludere i componenti dipendenti dal pacchetto del programma di installazione (eccetto gli assembly di utilità).
- Configurare i pacchetti prerequisiti.
- Configurare le condizioni di avvio.
- Compilare il progetto di installazione e copiare i risultati nel percorso di distribuzione.
- Distribuire la soluzione a livello di documento nel computer utente eseguendo l'installazione.
- Se necessario, aggiornare le proprietà personalizzate del documento.

### <a name="changing-the-location-of-the-deployed-document"></a>Modifica della posizione del documento distribuito

Le proprietà all'interno di un documento di Office vengono usate per individuare le soluzioni a livello di documento. Se il documento viene installato nella stessa cartella dell'assembly VSTO, non sono necessarie modifiche. Tuttavia, se è installato in una cartella diversa, sarà necessario aggiornare queste proprietà durante l'installazione.

Per altre informazioni su queste proprietà del documento, vedere [Cenni preliminari sulle proprietà personalizzate dei documenti](custom-document-properties-overview.md).

Per modificare queste proprietà, è necessario utilizzare un'azione personalizzata durante l'installazione.

L'esempio seguente usa una soluzione a livello di documento denominata ExcelWorkbookProject e un progetto di installazione denominato ExcelWorkbookSetup. Il progetto ExcelWorkbookSetup viene configurato utilizzando gli stessi passaggi descritti in precedenza, ad eccezione dell'impostazione delle chiavi del registro di sistema.

Per aggiungere il progetto di azione personalizzato alla soluzione di Visual Studio

1. Per aggiungere un nuovo progetto console .NET alla soluzione, fare clic con il pulsante destro del mouse sul **progetto di distribuzione di documenti di Office** nel **Esplora soluzioni**
2. Espandere **Aggiungi** , quindi fare clic su **nuovo progetto**.
3. Selezionare il modello applicazione console e denominare il progetto **AddCustomizationCustomAction**.

    ![Screenshot del Esplora soluzioni-AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **Figura 12: Esplora soluzioni-AddCustomizationCustomAction**

4. Aggiungere un riferimento a questi assembly:
    1. System.ComponentModel
    2. System.Configuration.Install
    3. Microsoft. VisualStudio. Tools. Applications
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. Copiare questo codice in Program.cs o Program. vb

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

Per aggiungere la personalizzazione al documento, è necessario avere l'ID della soluzione a livello di documento VSTO. Questo valore viene recuperato dal file di progetto di Visual Studio.

Per recuperare l'ID soluzione

1. Scegliere **Compila soluzione** dal menu **Compila** per compilare la soluzione a livello di documento e aggiungere la proprietà ID soluzione al file di progetto.
2. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto a livello di documento **ExcelWorkbookProject**
3. Fare clic su **UnloadProject** per accedere al file di progetto dall'interno di Visual Studio.

    ![Screenshot della soluzione Esplora soluzioni lo scaricamento del documento di Excel](media/setup-project-figure-16.jpg)

    **Figura 13: scaricamento della soluzione documento di Excel**

4. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse su **ExcelWorkbookProject** e scegliere **EditExcelWorkbookProject. vbproj** o **modifica ExcelWorkbookProject. csproj**.
5. Nell'editor **ExcelWorkbookProject** individuare l'elemento **SolutionID** all'interno dell'elemento **PropertyGroup** .
6. Copiare il valore GUID di questo elemento.

    ![Recupero di SolutionID](media/setup-project-figure-17.jpg)

    **Figura 14: recupero del SolutionID**

7. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse su **ExcelWorkbookProject** e scegliere **Ricarica progetto**.
8. Fare clic su **Sì** nella finestra di dialogo visualizzata per chiudere l'editor **ExcelWorkbookProject** .
9. L' **ID soluzione** verrà usato nell'azione installazione personalizzata.

L'ultimo passaggio consiste nel configurare l'azione personalizzata per i passaggi di **installazione** e **disinstallazione** .

### <a name="to-configure-the-setup-project"></a>Per configurare il progetto di installazione

1. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse su **ExcelWorkbookSetup**, espandere **Aggiungi** , quindi fare clic su **output progetto**.
2. Nella finestra di dialogo **Aggiungi gruppo di output del progetto** fare clic su **AddCustomizationCustomAction**nell'elenco **progetto** .
3. Selezionare **output primario** e fare clic su **OK** per chiudere la finestra di dialogo e aggiungere l'assembly contenente l'azione personalizzata al progetto di installazione.

    ![Screenshot dell'azione personalizzata manifesto del documento-finestra Aggiungi gruppo di output del progetto](media/setup-project-figure-18.jpg)

    **Figura 15: azione personalizzata del manifesto del documento-Aggiungi gruppo di output del progetto**

4. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse su **ExcelWorkbookSetup**.
5. Espandere **Visualizza** e fare clic su **azioni personalizzate**.
6. Nell'editor delle **azioni personalizzate (ExcelWorkbookSetup)** fare clic con il pulsante destro del mouse su **azioni personalizzate** e scegliere **Aggiungi azione personalizzata**.
7. Nella finestra di dialogo **Seleziona elemento nel progetto** , scegliere **cartella applicazione**nell'elenco **Cerca in** . Selezionare **output primario da AddCustomizationCustomAction (attivo)** e fare clic su **OK** per aggiungere l'azione personalizzata al passaggio di installazione.
8. Nel **nodo Installa**, fare clic con il pulsante destro del mouse su **output primario da AddCustomizationCustomAction (attivo)** e scegliere **Rinomina**. Assegnare un nome al **documento di copia dell'azione personalizzata in documenti e alleghi la personalizzazione**.
9. Nel **nodo Disinstalla**, fare clic con il pulsante destro del mouse su **output primario da AddCustomizationCustomAction (attivo)** e scegliere **Rinomina**. Denominare l'azione personalizzata **Rimuovi documento dalla cartella documenti**.

    ![Screenshot della finestra azioni personalizzate del manifesto del documento](media/setup-project-figure-19.jpg)

    **Figura 16: azioni personalizzate del manifesto del documento**

10. Nell'editor **azioni personalizzate (ExcelWorkbookSetup)** , fare clic con il pulsante destro del mouse su **copia documento in documenti e alleghi personalizzazione** , quindi scegliere **finestra Proprietà**.
11. Nella finestra delle **Proprietà** di **CustomActionData** immettere il percorso della DLL di personalizzazione, il manifesto di distribuzione e il percorso del documento Microsoft Office. Il SolutionID è necessario anche.
12. Se si desidera registrare eventuali errori di installazione in un file, includere un parametro LogFile.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Screenshot dell'azione personalizzata per copiare il documento in documenti Finestra Proprietà](media/setup-project-figure-20.jpg)

    **Figura 17: azione personalizzata per copiare il documento in documenti**

13. Per l'azione personalizzata per Uninstall è necessario il nome del documento. è possibile specificarlo utilizzando lo stesso parametro documentLocation in **CustomActionData**

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. Compilare e distribuire il progetto **ExcelWorkbookSetup** .
15. Cercare nella cartella **documenti** e aprire il file di ExcelWorkbookProject.xlsx.

## <a name="additional-resources"></a>Risorse aggiuntive

[Procedura: installare il Strumenti di Visual Studio per Office Runtime](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Office Primary Interop Assemblies](office-primary-interop-assemblies.md)

[Voci del registro di sistema per i componenti aggiuntivi VSTO](registry-entries-for-vsto-add-ins.md)

[Custom Document Properties Overview](custom-document-properties-overview.md)

[Specifica delle aree del modulo nel registro di sistema di Windows](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Granting Trust to Documents](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>Informazioni sugli autori

Vugt è un Microsoft MVP con tecnologie Office Open XML e un consulente indipendente che si concentra sulla creazione di Office Business Applications (OBA) con SharePoint, Microsoft Office e le tecnologie .NET correlate.
Si tratta di un collaboratore frequente per i siti della community degli sviluppatori, ad esempio [MSDN](/previous-versions/office/developer/office-2007/bb879915(v=office.12)). Ha pubblicato diversi white paper e articoli, oltre a un libro disponibile sulla riga denominata Open XML: e-Book illustrato.
Il fondatore del code-Counsel, una società olandese, si concentra sulla distribuzione di contenuti tecnici all'avanguardia tramite diversi canali. Per ulteriori informazioni su l'utente, leggere il suo blog.

Ted Pattison è un MVP, un autore, un trainer e il fondatore del gruppo Ted Pattison. Nel 2005, Ted è stato assunto da Microsoft Developer Platform Evangelist Group per creare il curriculum di formazione per sviluppatori Ascend per Windows SharePoint Services 3,0 e Microsoft Office SharePoint Server 2007. Da quel momento, Ted si è concentrato interamente sull'istruzione degli sviluppatori professionisti nelle tecnologie SharePoint 2007. Ted ha terminato di scrivere un libro per Microsoft Press, intitolato all'interno di Windows SharePoint Services 3,0, che è incentrato sull'utilizzo di SharePoint come piattaforma di sviluppo per la creazione di soluzioni aziendali. Ted scrive anche una colonna incentrata sugli sviluppatori per MSDN Magazine intitolato Office Space.
