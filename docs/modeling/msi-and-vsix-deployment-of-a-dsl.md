---
title: Distribuzione MSI e VSIX di un linguaggio DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9e42b5156ced1c01995882e3250c7243c18d24d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658369"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Distribuzione MSI e VSIX di un linguaggio DSL
È possibile installare un linguaggio specifico di dominio nel computer in uso o in altri computer. Visual Studio deve essere già installato nel computer di destinazione.

## <a name="which"></a>Scelta tra la distribuzione VSIX e MSI
 Esistono due metodi per distribuire un linguaggio specifico di dominio:

|Metodo|Vantaggi|
|-|-|
|VSX (estensione di Visual Studio)|Facile da distribuire: copiare ed eseguire il file con **estensione VSIX** dal progetto DslPackage.<br /><br /> Per ulteriori informazioni, vedere [installazione e disinstallazione di un linguaggio DSL utilizzando VSX](#Installing).|
|MSI (file del programma di installazione)|-Consente all'utente di aprire Visual Studio facendo doppio clic su un file DSL.<br />-Associa un'icona al tipo di file DSL nel computer di destinazione.<br />-Associa un XSD (XML Schema) al tipo di file DSL. In questo modo si evitano gli avvisi quando il file viene caricato in Visual Studio.<br /><br /> Per creare un'identità del servizio gestito, è necessario aggiungere un progetto di installazione alla soluzione.<br /><br /> Per ulteriori informazioni, vedere [distribuzione di un linguaggio DSL utilizzando un file MSI](#msi).|

## <a name="Installing"></a>Installare e disinstallare un linguaggio DSL usando il VSX

Quando il linguaggio DSL viene installato da questo metodo, l'utente può aprire un file DSL da Visual Studio, ma il file non può essere aperto da Esplora risorse.

### <a name="to-install-a-dsl-by-using-the-vsx"></a>Per installare un linguaggio DSL utilizzando il VSX

1. Individuare il file con **estensione VSIX** compilato dal progetto di pacchetto DSL:

   1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto **DslPackage** , quindi scegliere **Apri cartella in Esplora file**.

   2. Individuare il file **bin \\ \* \\** _progettoutente_ **. DslPackage. vsix**

2. Copiare il file **VSIX** nel computer di destinazione in cui si vuole installare il linguaggio DSL. Può trattarsi del computer in uso o di un altro computer.

   - Il computer di destinazione deve avere una delle edizioni di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] che supporta DSLs in fase di esecuzione. Per altre informazioni, vedere le [edizioni di Visual Studio supportate per la visualizzazione & Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

   - Il computer di destinazione deve avere una delle edizioni di Visual Studio specificate in **DslPackage\source.Extensions.manifest**.

3. Nel computer di destinazione fare doppio clic sul file **VSIX** .

    **Visual Studio Extension Installer** si apre e installa l'estensione.

4. Avviare o riavviare [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

5. Per testare il linguaggio DSL, usare Visual Studio per creare un nuovo file con l'estensione definita per il linguaggio DSL.

### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Per disinstallare un linguaggio DSL installato tramite VSX

1. Nel menu **Strumenti** scegliere **Estensioni e aggiornamenti**.

2. Espandere **Estensioni installate**.

3. Selezionare l'estensione in cui è definito il linguaggio DSL, quindi fare clic su **Disinstalla**.

   Raramente, un'estensione errata non viene caricata e crea un report nella finestra degli errori, ma non viene visualizzata in Gestione estensioni. In tal caso, è possibile rimuovere l'estensione eliminando il file da:

   **\Microsoft\VisualStudio\10.0\Extensions** LocalAppData

## <a name="msi"></a>Distribuzione di un linguaggio DSL in un file MSI
 Definendo un file MSI (Windows Installer) per il linguaggio DSL, è possibile consentire agli utenti di aprire i file DSL da Esplora risorse. È anche possibile associare un'icona e una breve descrizione all'estensione del nome file. Inoltre, l'identità del servizio gestito può installare un XSD che può essere utilizzato per convalidare i file DSL. Se lo si desidera, è possibile aggiungere altri componenti nell'identità del servizio gestito che verranno installati nello stesso momento.

 Per ulteriori informazioni sui file MSI e altre opzioni di distribuzione, vedere [distribuzione di applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md).

 Per compilare un'identità del servizio gestito, è necessario aggiungere un progetto di installazione alla soluzione di Visual Studio. Il metodo più semplice per creare un progetto di installazione consiste nell'usare il modello CreateMsiSetupProject.tt, che è possibile scaricare dal [sito VMSDK](http://go.microsoft.com/fwlink/?LinkID=186128).

### <a name="to-deploy-a-dsl-in-an-msi"></a>Per distribuire un linguaggio DSL in un file MSI

1. Impostare `InstalledByMsi` nel manifesto dell'estensione. In questo modo si impedisce l'installazione e la disinstallazione di VSX, ad eccezione di MSI. Questo è importante se si includeranno altri componenti nell'identità del servizio gestito.

   1. Apri DslPackage source.Extension.TT

   2. Inserire la riga seguente prima di `<SupportedProducts>`:

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Creare o modificare un'icona che rappresenterà il linguaggio DSL in Esplora risorse. Ad esempio, Edit **DslPackage\Resources\File.ico**

3. Assicurarsi che gli attributi seguenti del linguaggio DSL siano corretti:

   - In DSL Explorer fare clic sul nodo radice e in Finestra Proprietà rivedere:

       - Descrizione

       - Versione

   - Fare clic sul nodo **Editor** e nella finestra Proprietà fare clic **sull'icona**. Impostare il valore in modo che faccia riferimento a un file di icona in **DslPackage\Resources**, ad esempio **file. ico**

   - Nel menu **Compila** aprire **Configuration Manager**e selezionare la configurazione che si desidera compilare, ad esempio **versione** o **debug**.

4. Passare a [visualizzazione e modellazione SDK Home page](http://go.microsoft.com/fwlink/?LinkID=186128)e dalla scheda **download** scaricare **CreateMsiSetupProject.TT**.

5. Aggiungere **CreateMsiSetupProject.TT** al progetto DSL.

    Visual Studio creerà un file denominato **CreateMsiSetupProject. vdproj**.

6. In Esplora risorse copiare DSL \\ *. vdproj in una nuova cartella denominata setup.

    Se lo si desidera, è ora possibile escludere CreateMsiSetupProject.tt dal progetto DSL.

7. In **Esplora soluzioni**aggiungere il **programma di installazione \\ \*. vdproj** come progetto esistente.

8. Scegliere **Dipendenze progetto**dal menu **progetto** .

    Nella finestra di dialogo **Dipendenze progetto** selezionare il progetto di installazione.

    Selezionare la casella accanto a **DslPackage**.

9. Ricompilare la soluzione.

10. In Esplora risorse individuare il file MSI compilato nel progetto di installazione.

     Copiare il file MSI in un computer in cui si vuole installare il linguaggio DSL. Fare doppio clic sul file MSI. Viene eseguito il programma di installazione.

11. Nel computer di destinazione, creare un nuovo file con l'estensione di file del linguaggio DSL. Verificare che:

    - In visualizzazione elenco di Esplora risorse il file viene visualizzato con l'icona e la descrizione definiti.

    - Quando si fa doppio clic sul file, viene avviato Visual Studio e viene aperto il file DSL nell'editor DSL.

    Se si preferisce, è possibile creare manualmente il progetto di installazione, anziché usare il modello di testo. Per una procedura dettagliata che include questa procedura, vedere il capitolo 5 del [Lab SDK di visualizzazione e modellazione](http://go.microsoft.com/fwlink/?LinkId=208878).

### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Per disinstallare un linguaggio DSL installato da un file MSI

1. In Windows aprire il pannello di controllo **programmi e funzionalità** .

2. Disinstallare il linguaggio DSL.

3. Riavviare Visual Studio.