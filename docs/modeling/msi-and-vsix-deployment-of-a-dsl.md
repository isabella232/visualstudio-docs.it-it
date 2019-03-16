---
title: Distribuzione MSI e VSIX di un linguaggio DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 664d323976692d20a3f9f9bb8a7e66c0aa4f9761
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58069606"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Distribuzione MSI e VSIX di un linguaggio DSL
È possibile installare un linguaggio specifico di dominio nel proprio computer o in altri computer. Visual Studio deve essere già installato nel computer di destinazione.

## <a name="which"></a> Scelta tra distribuzione MSI e VSIX
 Esistono due metodi di distribuzione di un linguaggio specifico di dominio:

|Metodo|Vantaggi|
|-|-|
|VSX (estensione di Visual Studio)|Molto semplice da distribuire: Copiare ed eseguire la **VSIX** file dal progetto DslPackage.<br /><br /> Per altre informazioni, vedere [installazione e disinstallazione di un linguaggio DSL utilizzando il VSX](#Installing).|
|Identità del servizio gestito (file di programma di installazione)|-Consente all'utente di aprire Visual Studio facendo doppio clic su un file DSL.<br />-Consente di associare un'icona con il tipo di file DSL nel computer di destinazione.<br />-Associa uno schema XSD (XML schema) con il tipo di file DSL. Ciò consente di evitare gli avvisi quando i file verrà caricato in Visual Studio.<br /><br /> È necessario aggiungere un progetto di installazione alla soluzione per creare un file MSI.<br /><br /> Per altre informazioni, vedere [distribuzione di un linguaggio DSL utilizzando un file MSI](#msi).|

## <a name="Installing"></a> Installare e disinstallare un linguaggio DSL utilizzando il VSX

Quando il linguaggio DSL viene installato da questo metodo, l'utente può aprire un file DSL da Visual Studio, ma non è possibile aprire il file da Esplora risorse di Windows.

### <a name="to-install-a-dsl-by-using-the-vsx"></a>Per installare un linguaggio DSL utilizzando il VSX

1. Individuare il **VSIX** file compilato dal progetto del pacchetto DSL:

   1.  Nelle **Esplora soluzioni**, fare doppio clic il **DslPackage** del progetto e quindi fare clic su **Apri cartella in Esplora File**.

   2.  Individuare il file **bin\\\*\\**_YourProject_**. DslPackage.vsix**

2. Copia il **VSIX** file nel computer di destinazione in cui si desidera installare il linguaggio DSL. Può trattarsi del computer in uso o di un altro computer.

   - Nel computer di destinazione deve essere una delle edizioni di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] che supporta linguaggi specifici di dominio in fase di esecuzione. Per altre informazioni, vedere [supportate le edizioni Visual Studio per Visualization and Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

   - Nel computer di destinazione deve essere una delle edizioni di Visual Studio specificata **DslPackage\source.extensions.manifest**.

3. Nel computer di destinazione, fare doppio clic il **VSIX** file.

    **Visual Studio Extension Installer** si apre e installa l'estensione.

4. Avviare o riavviare [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

5. Per testare il linguaggio DSL, usare Visual Studio per creare un nuovo file con estensione definito per il linguaggio DSL.

### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Per disinstallare un linguaggio specifico di dominio che è stato installato utilizzando VSX

1. Nel menu **Strumenti** scegliere **Estensioni e aggiornamenti**.

2. Espandere **Estensioni installate**.

3. Selezionare l'estensione in cui è definito il linguaggio DSL e quindi fare clic su **Disinstalla**.

   Raramente, un'estensione errata non viene caricata e crea un report nella finestra degli errori, ma non viene visualizzata in Gestione estensioni. In tal caso, è possibile rimuovere l'estensione eliminando il file da:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="msi"></a> Distribuzione di un linguaggio DSL in un file MSI
 Con la definizione di un file MSI (programma di installazione di Windows) per il linguaggio DSL, è possibile consentire agli utenti di aprire i file DSL da Esplora risorse di Windows. È anche possibile associare un'icona e una breve descrizione con l'estensione di file. Inoltre, l'identità del servizio gestito è possibile installare uno schema XSD che può essere usato per convalidare i file DSL. Se si desidera, è possibile aggiungere altri componenti nel file MSI che verrà installato nello stesso momento.

 Per altre informazioni sui file MSI e altre opzioni di distribuzione, vedere [distribuzione di applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md).

 Per compilare un file MSI, si aggiunge un progetto di installazione alla soluzione Visual Studio. Il metodo di creazione di un progetto di installazione più semplice consiste nell'usare il modello CreateMsiSetupProject.tt, che è possibile scaricare dal [sito VMSDK](http://go.microsoft.com/fwlink/?LinkID=186128).

### <a name="to-deploy-a-dsl-in-an-msi"></a>Per distribuire un linguaggio DSL in un file MSI

1. Impostare `InstalledByMsi` nel manifesto dell'estensione. Ciò impedisce di VSX installati e disinstallati tranne per il file MSI. Questo è importante se gli altri componenti verranno incluse nel file MSI.

   1.  Open DslPackage\source.extension.tt

   2.  Inserire la riga seguente prima `<SupportedProducts>`:

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Creare o modificare un'icona che rappresenta il linguaggio DSL in Windows Explorer. Ad esempio, modificare **DslPackage\Resources\File.ico**

3. Assicurarsi che i seguenti attributi del linguaggio DSL siano corretti:

   -   In DSL Explorer fare clic sul nodo radice e nella finestra Proprietà controllare:

       -   Descrizione

       -   Versione

   -   Scegliere il **Editor** nodo e nella finestra Proprietà, fare clic su **icona**. Impostare il valore per fare riferimento a un file di icona nel **DslPackage\Resources**, ad esempio **File.ico**

   -   Nel **compilare** menu, aprire **Configuration Manager**e selezionare la configurazione che si desidera compilare, ad esempio **Release** o **Debug** .

4. Passare a [Visualization and Modeling SDK homepage](http://go.microsoft.com/fwlink/?LinkID=186128)e dal **Scarica** scheda, scaricare **CreateMsiSetupProject.tt**.

5. Aggiungere **CreateMsiSetupProject.tt** al progetto Dsl.

    Visual Studio creerà un file denominato **CreateMsiSetupProject.vdproj**.

6. In Esplora risorse, la copia Dsl\\\*.vdproj in una nuova cartella denominata il programma di installazione.

    (Se si desidera, è ora possibile escludere CreateMsiSetupProject.tt dal progetto Dsl.)

7. Nelle **Esplora soluzioni**, aggiungere **il programma di installazione\\\*vdproj** come un progetto esistente.

8. Nel **progetto** menu, fare clic su **dipendenze progetto**.

    Nel **dipendenze progetto** finestra di dialogo, selezionare il progetto di installazione.

    Selezionare la casella accanto a **DslPackage**.

9. Ricompilare la soluzione.

10. In Windows Explorer individuare il file MSI generato nel progetto di installazione.

     Copiare il file MSI in un computer in cui si desidera installare il linguaggio DSL. Fare doppio clic sul file MSI. Viene eseguito il programma di installazione.

11. Nel computer di destinazione, creare un nuovo file con l'estensione del file del linguaggio DSL. Verificare che:

    -   Nella visualizzazione elenco Windows Explorer, il file viene visualizzato con l'icona e una descrizione che è definito.

    -   Quando si fare doppio clic il file, l'avvio di Visual Studio e si apre il file DSL in un editor di linguaggio specifico di dominio.

    Se si preferisce, è possibile creare il progetto di installazione manualmente, anziché usare il modello di testo. Per una procedura dettagliata che includa questa procedura vedere il capitolo 5 del [visualizzazione e modellazione Lab SDK](http://go.microsoft.com/fwlink/?LinkId=208878).

### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Per disinstallare un linguaggio DSL che viene installato da un file MSI

1.  In Windows, aprire il **programmi e funzionalità** Pannello di controllo.

2.  Disinstallare il linguaggio DSL.

3.  Riavviare Visual Studio.