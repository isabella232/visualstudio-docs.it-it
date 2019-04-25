---
title: "Procedura: creare ed eseguire un'installazione automatica | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: deabd34896b327f7cbbb35c7af75f5810dcfbf17
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040546"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>Procedura: creare ed eseguire un'installazione automatica di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile eseguire l'applicazione di installazione per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] come un'installazione automatica, cioè invisibile all'utente, su una rete intranet invece che su un supporto tipo DVD. In questo argomento viene descritto come preparare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per questo tipo di installazione da una condivisione di rete.

## <a name="creating-a-network-image"></a>Creazione di un'immagine di rete
 Innanzitutto, creare un'immagine di rete del supporto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

#### <a name="to-create-a-network-image"></a>Per creare un'immagine di rete

1. Creare una cartella nel server (ad esempio, *Unità*:\IDEinstall\\).

2. Scaricare il programma di installazione da [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015), quindi eseguire *Product*.exe /Layout *Drive*:\IDEinstall\

3. Condividere la cartella IDEinstall sulla rete e quindi impostare le impostazioni di sicurezza appropriate.

     Il percorso di rete dell'applicazione di installazione per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] è simile a \\\\*ServerName*\IDEinstall\\*Product*.exe.

    > [!NOTE]
    >  L'installazione potrebbe non riuscire se una combinazione di percorso e nome file supera i 260 caratteri. La lunghezza massima di un percorso in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] è 221 caratteri.  Il nome del percorso locale non deve superare i 70 caratteri e il nome del percorso di rete non deve superare i 39 caratteri.

     L'installazione potrebbe non riuscire anche se i nomi delle cartelle nel percorso includono spazi (ad esempio, "\\\\*ServerName*\IDE install" oppure \\\\*ServerName*\Visual Studio\\).

## <a name="deploying-visual-studio-in-unattended-mode"></a>Distribuzione di Visual Studio in modalità automatica
 Per distribuire [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in modalità automatica, è necessario modificare il file AdminDeployment.xml. A tale scopo, è necessario innanzitutto creare il file AdminDeployment.xml usando il parametro della riga di comando `/CreateAdminFile` *\<file location>*. È quindi possibile usare tale file per effettuare il push di una distribuzione di Visual Studio sulla rete o per inserirla in un'installazione se si inserisce tale file nella directory *Drive*:\IDEinstall\packages. Il file AdminDeployment.xml non è univoco per un sistema operativo, architettura, edizione di Visual Studio o lingua del sistema operativo.

> [!CAUTION]
>  In alcuni casi, gli elementi elencati come selezionati nel file AdminDeployment.xml non vengono installati. Per risolvere questo problema, inserire gli elementi contrassegnati "Selected="yes"" alla **fine** del file AdminDeployment.xml.
>
>  Se non si vogliono installare le dipendenze facoltative di un elemento, sarà necessario selezionare prima l'elemento padre e quindi deselezionare le dipendenze facoltative dopo l'elemento padre, come illustrato nella schermata seguente:
>
>  ![Voci relative all'installazione alla fine del file AdminDeployment.xml](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")
>
>  Un altro modo per eseguire questa operazione consiste nell'omettere gli elementi figlio facoltativi di un elemento padre, vale a dire di non includere gli elementi "Selected="no"", ma è necessario comunque inserire tutti gli elementi "Selected="yes"" alla fine del file AdminDeployment.xml.

> [!IMPORTANT]
>  Durante l'installazione, il computer potrebbe riavviarsi automaticamente una o più volte. Dopo il riavvio, è necessario accedere nuovamente con lo stesso account utente con cui è stato effettuato l'accesso per eseguire l'installazione prima di riavviare il computer. È possibile evitare i riavvii automatici installando i componenti prerequisiti prima di eseguire un'installazione automatica. Per altre informazioni, vedere la sezione intitolata "Evitare il riavvio durante l'installazione" nella [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md).

 Lo schema del file AdminDeployment contiene i seguenti elementi:

|Elemento|Attributo|Valori|Description|
|-------------|---------------|------------|-----------------|
|BundleCustomizations|TargetDir|*Path*|Si comporta come la sostituzione del percorso nell'interfaccia utente dell'applicazione di installazione. Questo elemento viene ignorato se Visual Studio è già installato.|
|BundleCustomizations|NoWeb|yes&#124;default|Se il valore di questo elemento è Sì, l'applicazione di installazione non tenta mai di accedere al Web durante l'azione di installazione.|
|SelectableItemCustomization|Hidden|Yes&#124;No|Se il valore di questo elemento è Sì, nasconde un elemento selezionabile nell'albero della personalizzazione.|
|SelectableItemCustomization|Selezionato|Yes&#124;No|Seleziona o deseleziona un elemento selezionabile nell'albero della personalizzazione.|
|BundleCustomizations|Feed|Path|Percorso del feed che l'utente vuole usare.  Questo feed viene usato per le successive operazioni di modifica nel computer ("Default" per impostazione predefinita).|
|BundleCustomizations|SuppressRefreshPrompt|yes&#124;default|Impedisce che all'utente venga richiesto di aggiornare l'installazione se è disponibile una versione più recente.|
|BundleCustomizations|NoRefresh|yes&#124;default|Non aggiorna l'installazione se è disponibile una versione più recente.|
|BundleCustomizations|NoCacheOnlyMode|yes&#124;default|Impedisce il prepopolamento della cache del pacchetto.|

> [!WARNING]
>  L'applicazione di installazione rispetterà lo stato selezionato di un elemento selezionabile anche se è nascosto. Ad esempio, se si desidera installare sempre un elemento selezionabile, è possibile contrassegnarlo come nascosto e selezionato.

#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Per creare un'installazione automatica di Visual Studio

1. Nel file *Drive*:\IDEinstall\AdminDeployment.xml, modificare il valore dell'attributo NoWeb dell'elemento BundleCustomizations da "default" a "yes", come illustrato nell'esempio riportato di seguito:

     Modificare `<BundleCustomizations TargetDir="default" NoWeb="default"/>` in `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`

2. Modificare l'attributo SelectableItemCustomization in base alle esigenze per i componenti facoltativi, quindi salvare il file.

## <a name="running-unattended-setup"></a>Esecuzione dell'installazione automatica
 È possibile eseguire l'installazione automatica eseguendo automaticamente l'applicazione di installazione per Visual Studio nei computer client o consentendo agli utenti di eseguire autonomamente l'applicazione usando le impostazioni definite.

#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>Per eseguire un'installazione automatica in un computer client

- Aprire il menu **Start**, scegliere **Esegui** e quindi immettere \\\\*ServerName*\IDEinstall\vs_*Product*.exe /adminfile *PathOfTheAdmindeployment.xmlFile*<em>AdditionalParametersAsNeeded</em>

   Ad esempio, è possibile specificare la seguente riga di comando: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`

#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>Per abilitare i client in modo da installare manualmente Visual Studio con le impostazioni predefinite

1. Copiare il file AdminDeployment.xml personalizzato in una condivisione di rete in sola lettura (ad esempio, \\\\*NomeServer*\IDEinstall\packages\AdminDeployment.xml).

2. Consentire agli utenti di effettuare l'installazione da tale condivisione.

## <a name="maintaining-an-installation"></a>Gestione di un'installazione
 Se si apre il **Pannello di controllo** e si esegue nuovamente l'applicazione di installazione, è possibile modificare le funzionalità di Visual Studio, disinstallare linguaggi di programmazione e ripristinare o disinstallare Visual Studio.

> [!NOTE]
>  Per usare la modalità di manutenzione è necessario disporre delle credenziali amministrative sul computer locale.

#### <a name="to-maintain-an-installation-on-a-client-computer"></a>Per mantenere un'installazione su un computer client

- Aprire il **Pannello di controllo**, quindi scegliere **Programmi e funzionalità**.

- Scegliere [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], quindi scegliere **Modifica**.

#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>Per modificare le impostazioni di AdminDeployment in un computer client dopo l'installazione di Visual Studio

1. Aggiornare AdminDeployment.xml in base alle esigenze.

2. Aprire il menu **Start** , quindi scegliere **Esegui**.

3. Immettere il testo seguente: \\\\*ServerName*\IDEinstall\vs_*Product*.exe /AdminFile PathToAdmindeployment.xml File

    AdditionalParametersAsNeeded

    Ad esempio, è possibile specificare la seguente riga di comando: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`

   Repair è il parametro predefinito dopo l'installazione di Visual Studio. Se si ripristina Visual Studio con un /AdminFile aggiornato, si eseguirà l'override delle impostazioni di distribuzione Admin correnti con quelle richiamate dal file AdminDeployment.xml aggiornato.

## <a name="updating-an-installation"></a>Aggiornamento di un'installazione
 Microsoft ha rilasciato diversi aggiornamenti per Visual Studio 2015. In questa sezione viene illustrato come aggiornare l'immagine dell'installazione automatica di Visual Studio 2015 in modo da includere gli aggiornamenti.

#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>Per aggiornare un'installazione automatica di Visual Studio

1. Individuare il file Product.exe nell'immagine di rete esistente, fare clic con il pulsante destro del mouse su di esso e quindi scegliere **Proprietà**.

2. Fare clic sulla scheda **Informazioni dettagliate** e quindi prendere nota della proprietà **Versione prodotto**.

    ![Esempio di finestra di dialogo delle proprietà in un'installazione automatica di Visual Studio](../install/media/unattended-install-properties-dialog-box.PNG "Installazione automatica - Finestra di dialogo delle proprietà")

3. ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>Se la versione del prodotto è 14.0.24720.0 o 14.0.24720.1, seguire questa procedura:
   1. Eseguire *Product.exe* /Layout *Drive:* \IDEinstall in un computer con accesso a Internet. Ad esempio, eseguire: `vs_enterprise.exe /Layout d:\IDEinstall`.

   2. Al termine dell'esecuzione del comando /Layout, copiare la nuova immagine in una nuova posizione.

   3. Creare e modificare il file AdminDeployment.xml. A tale scopo, usare il parametro della riga di comando `/CreateAdminFile`*\<file location>*. Per altre informazioni, vedere la sezione "Distribuzione di Visual Studio in modalità automatica" in questo articolo.

   4. Nel computer client, eseguire il comando seguente per aggiornare la copia di Visual Studio installata in precedenza: "\\\\*server1*\IDEinstall_Updated_1\\*Product.exe* /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart".

        Ad esempio, eseguire: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`
5. ###### <a name="for-other-product-version-values-follow-these-steps"></a>Per altri valori di versione del prodotto, seguire questa procedura:
   1. Eseguire *Product.exe* /Layout *Drive:* \IDEinstall in un computer con accesso a Internet. Ad esempio, eseguire: `vs-enterprise.exe /Layout d:\IDEinstall`.

   2. Al termine dell'esecuzione del comando /Layout, copiare la nuova immagine in una nuova posizione. In alternativa, è possibile sostituire l'immagine di rete esistente.

   3. Creare e quindi modificare il file AdminDeployment.xml. A tale scopo, usare il parametro della riga di comando `/CreateAdminFile`*\<file location>*. Per altre informazioni, vedere la sezione "Distribuzione di Visual Studio in modalità automatica" in questo articolo.

   4. Se si copia l'immagine in una nuova posizione, è necessario eseguire il comando seguente nel computer client per aggiornare la copia di Visual Studio installata in precedenza: "\\\\*server1*\IDEinstall_Updated_1\\*Product.exe* /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart".

        Ad esempio, eseguire: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`

   5. Se si sostituisce l'immagine di rete esistente, è possibile eseguire il comando come indicato nel passaggio precedente oppure è possibile procedere come segue:
       1. Aprire il **Pannello di controllo**, quindi scegliere **Programmi e funzionalità**.

       2. Scegliere **Visual Studio** e quindi scegliere **Cambia**.

       3. Dopo l'avvio di Visual Studio in modalità di manutenzione, fare clic su **Modifica**.

       4. L'aggiornamento più recente verrà visualizzato nella pagina delle funzionalità. Selezionare le altre funzionalità da installare, fare clic su **Avanti**, quindi fare clic su **Aggiorna** per installare l'aggiornamento e le nuove funzionalità.

## <a name="registering-the-product"></a>Registrazione del prodotto
 Al termine dell'installazione, è possibile registrare la copia di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dall'interno di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

#### <a name="to-register"></a>Per effettuare la registrazione

1. Aprire il menu **Guida** , quindi scegliere **Registra prodotto**.

2. Immettere il codice Product Key.

     Per altre informazioni, vedere gli argomenti [Procedura: individuare il codice Product Key di Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) e [Procedura: applicare automaticamente i codici Product Key durante la distribuzione di Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md).

## <a name="see-also"></a>Vedere anche
 [Installare Visual Studio](../install/install-visual-studio-2015.md)