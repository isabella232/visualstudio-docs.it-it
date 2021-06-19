---
title: Distribuzione MSI e VSIX di un linguaggio DSL
description: Informazioni su come installare un linguaggio specifico di dominio (DSL) nel proprio computer o in altri computer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 879028746eac10160492f03651ef8b51714e9c6a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391010"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Distribuzione MSI e VSIX di un linguaggio DSL
È possibile installare un linguaggio specifico di dominio nel proprio computer o in altri computer. Visual Studio deve essere già installato nel computer di destinazione.

## <a name="choosing-between-vsix-and-msi-deployment"></a><a name="which"></a> Scelta tra la distribuzione VSIX e MSI
 Esistono due metodi per distribuire un linguaggio specifico di dominio:

|Metodo|Vantaggi|
|-|-|
|VSX (estensione Visual Studio)|Distribuzione molto semplice: copiare ed eseguire il file **con estensione vsix** dal progetto DslPackage.<br /><br /> Per altre informazioni, [vedere Installazione e disinstallazione di un DSL tramite VSX.](#Installing)|
|MSI (file del programma di installazione)|- Consente all'utente di aprire Visual Studio facendo doppio clic su un file DSL.<br />- Associa un'icona al tipo di file DSL nel computer di destinazione.<br />: associa un XSD (XML Schema) al tipo di file DSL. In questo modo si evitano avvisi quando il file viene caricato in Visual Studio.<br /><br /> È necessario aggiungere un progetto di installazione alla soluzione per creare un file MSI.<br /><br /> Per altre informazioni, vedere [Distribuzione di un DSL tramite un file MSI.](#msi)|

## <a name="install-and-uninstall-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> Installare e disinstallare un DSL usando VSX

Quando il DSL viene installato con questo metodo, l'utente può aprire un file DSL dall'interno di Visual Studio, ma il file non può essere aperto da Esplora risorse.

### <a name="to-install-a-dsl-by-using-the-vsx"></a>Per installare un DSL tramite VSX

1. Individuare il file **con estensione vsix** compilato dal progetto di pacchetto DSL:

   1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **DslPackage** e quindi scegliere **Apri cartella in Esplora file**.

   2. Individuare il file **bin \\ \* \\**_YourProject_**. DslPackage.vsix**

2. Copiare il file **con estensione vsix** nel computer di destinazione in cui si vuole installare il DSL. Può trattarsi del computer in uso o di un altro computer.

   - Il computer di destinazione deve avere una delle edizioni di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] che supportano DSL in fase di esecuzione. Per altre informazioni, vedere [Supported Visual Studio Editions for Visualization & Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

   - Il computer di destinazione deve avere una delle edizioni di Visual Studio specificata in **DslPackage\source.extensions.manifest.**

3. Nel computer di destinazione fare doppio clic sul file **con estensione vsix.**

    **Visual Studio Extension Installer** si apre e installa l'estensione.

4. Avviare o riavviare [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

5. Per testare il DSL, usare Visual Studio per creare un nuovo file con l'estensione definita per il DSL.

### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Per disinstallare un DSL installato tramite VSX

1. Nel menu **Strumenti** scegliere **Estensioni e aggiornamenti**.

2. Espandere **Estensioni installate**.

3. Selezionare l'estensione in cui è definito il DSL e quindi fare clic su **Disinstalla.**

   Raramente, un'estensione errata non viene caricata e crea un report nella finestra degli errori, ma non viene visualizzata in Gestione estensioni. In tal caso, è possibile rimuovere l'estensione eliminando il file da:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="deploying-a-dsl-in-an-msi"></a><a name="msi"></a> Distribuzione di un DSL in un file MSI
 Definendo un file MSI (Windows Installer) per il DSL, è possibile consentire agli utenti di aprire file DSL da Esplora risorse. È anche possibile associare un'icona e una breve descrizione all'estensione del nome file. Inoltre, l'msi può installare un file XSD che può essere usato per convalidare i file DSL. Se si vuole, è possibile aggiungere altri componenti all'msi che verranno installati contemporaneamente.

 Per altre informazioni sui file MSI e altre opzioni di distribuzione, vedere [Distribuzione di applicazioni, servizi e componenti.](../deployment/deploying-applications-services-and-components.md)

 Per compilare un file MSI, aggiungere un progetto di installazione alla Visual Studio soluzione. Il metodo più semplice per creare un progetto di installazione è usare il modello CreateMsiSetupProject.tt, che è possibile scaricare dal sito [VMSDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).

### <a name="to-deploy-a-dsl-in-an-msi"></a>Per distribuire un DSL in un file MSI

1. Impostare `InstalledByMsi` nel manifesto dell'estensione. In questo modo si impedisce l'installazione e la disinstallazione di VSX, ad eccezione di MSI. Questo è importante se si includeranno altri componenti nell'msi.

   1. Aprire DslPackage\source.extension.tt

   2. Inserire la riga seguente prima di `<SupportedProducts>` :

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Creare o modificare un'icona che rappresenterà il DSL in Esplora risorse. Ad esempio, modificare **DslPackage\Resources\File.ico**

3. Assicurarsi che gli attributi seguenti del DSL siano corretti:

   - In Esplora DSL fare clic sul nodo radice e in Finestra Proprietà esaminare:

       - Descrizione

       - Versione

   - Fare clic **sul nodo Editor** e nella Finestra Proprietà fare clic su **Icona**. Impostare il valore per fare riferimento a un file di icona in **DslPackage\Resources,** ad **esempio File.ico**

   - Nel menu **Compila** **aprire Gestione configurazione** e selezionare la configurazione che si vuole compilare, ad esempio **Versione** o **Debug.**

4. Passare a [Visualization and Modeling SDK home page](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)e dalla scheda **Download** scaricare **CreateMsiSetupProject.tt**.

5. Aggiungere **CreateMsiSetupProject.tt** al progetto Dsl.

    Visual Studio creerà un file denominato **CreateMsiSetupProject.vdproj.**

6. In Esplora risorse copiare Dsl \\ *.vdproj in una nuova cartella denominata Setup.

    Se si vuole, è ora possibile escludere CreateMsiSetupProject.tt dal progetto Dsl.

7. In **Esplora soluzioni** aggiungere **Setup \\ \* .vdproj** come progetto esistente.

8. Scegliere **Dipendenze** progetto dal menu **Progetto**.

    Nella finestra **di dialogo Dipendenze** progetto selezionare il progetto di installazione.

    Selezionare la casella accanto a **DslPackage**.

9. Ricompilare la soluzione.

10. In Esplora risorse individuare il file MSI compilato nel progetto di installazione.

     Copiare il file MSI in un computer in cui si vuole installare il DSL. Fare doppio clic sul file MSI. Il programma di installazione verrà eseguito.

11. Nel computer di destinazione creare un nuovo file con estensione DSL. l'elenco di controllo seguente.

    - Nella Esplora risorse elenco il file viene visualizzato con l'icona e la descrizione definite.

    - Quando si fa doppio clic sul file, Visual Studio e apre il file DSL nell'editor DSL.

    Se si preferisce, è possibile creare il progetto di installazione manualmente, anziché usare il modello di testo. Per una procedura dettagliata che include questa procedura, vedere il capitolo 5 del lab [dell'SDK di visualizzazione e modellazione.](https://code.msdn.microsoft.com/DSLToolsLab/Release/ProjectReleases.aspx?ReleaseId=4207)

### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Per disinstallare un DSL installato da un file MSI

1. In Windows aprire il **Pannello di controllo Programmi** e funzionalità.

2. Disinstallare il DSL.

3. Riavviare Visual Studio.
