---
title: Pubblicazione di un servizio Cloud usando gli strumenti di Azure | Microsoft Docs
description: Informazioni su come pubblicare progetti di servizi cloud di Azure usando Visual Studio.
author: ghogen
manager: douge
assetId: 1a07b6e4-3678-4cbf-b37e-4520b402a3d9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: cf29e1cdde71d2e8ef7caa9bc91bc31c30c7bc41
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002860"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>Pubblicazione di un servizio cloud con Visual Studio

Visual Studio può pubblicare un'applicazione direttamente in Azure, con supporto per gli ambienti di gestione temporanea e produzione di un servizio cloud. Durante la pubblicazione, selezionare l'ambiente di distribuzione e un account di archiviazione da usata temporaneamente per il pacchetto di distribuzione.

Durante lo sviluppo e test di un'applicazione Azure, è possibile usare distribuzione Web per pubblicare le modifiche in modo incrementale per i ruoli web. Dopo aver pubblicato l'applicazione in un ambiente di distribuzione, distribuzione Web consente di distribuire le modifiche apportate direttamente alla macchina virtuale che esegue il ruolo web. Non è necessario creare un pacchetto e pubblicare l'intera applicazione di Azure ogni volta che si desidera aggiornare il ruolo web per testare le modifiche. Con questo approccio, è possibile avere le modifiche di ruolo web disponibili nel cloud per il test senza dover attendere la pubblicazione in un ambiente di distribuzione dell'applicazione.

Usare le procedure seguenti per pubblicare l'applicazione Azure e per aggiornare un ruolo web tramite distribuzione Web:

- Pubblicare o assemblare un'applicazione Azure da Visual Studio
- Aggiornare un ruolo web come parte del ciclo di sviluppo e test

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>Pubblicare o assemblare un'applicazione Azure da Visual Studio

Quando si pubblica l'applicazione Azure, è possibile eseguire una delle seguenti attività:

- Creare un pacchetto del servizio: È possibile usare questo pacchetto e il file di configurazione del servizio per pubblicare l'applicazione in un ambiente di distribuzione dal [portale di Azure](https://portal.azure.com).

- Pubblicare il progetto Azure da Visual Studio: per pubblicare l'applicazione direttamente in Azure, si utilizza la pubblicazione guidata. Per informazioni, vedere [pubblicazione guidata applicazione di Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-create-a-service-package-from-visual-studio"></a>Per creare un pacchetto del servizio da Visual Studio

1. Quando si è pronti a pubblicare l'applicazione, aprire Esplora soluzioni, aprire il menu di scelta rapida per il progetto Azure contenente i ruoli e scegliere pubblica.

1. Per creare un pacchetto del servizio, seguire questa procedura:

   a. Nel menu di scelta rapida per il progetto Azure, scegliere **pacchetto**.

   b. Nel **pacchetto applicazione Azure** nella finestra di dialogo scegliere la configurazione del servizio per il quale si desidera creare un pacchetto e quindi scegliere la configurazione della build.

   c. (Facoltativo) Per abilitare Desktop remoto per il servizio cloud dopo la pubblicazione, selezionare **Abilita Desktop remoto per tutti i ruoli**, quindi selezionare **impostazioni** per configurare le credenziali di Desktop remoto. Per altre informazioni, vedere [abilitare connessione Desktop remoto per un ruolo nei servizi Cloud di Azure con Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

      Se si desidera eseguire il debug del servizio cloud dopo la pubblicazione, attivare il debug remoto selezionando **Abilita Debugger remoto per tutti i ruoli**.

   d. Per creare il pacchetto, scegliere il **pacchetto** collegamento.

      Esplora file Mostra il percorso del file del pacchetto appena creato. È possibile copiare questo percorso, in modo che sia possibile usarlo dal portale di Azure.

   e. Per pubblicare il pacchetto in un ambiente di distribuzione, è necessario usare questo percorso come percorso del pacchetto quando si crea un servizio cloud e si distribuisce il pacchetto in un ambiente con il portale di Azure.

1. (Facoltativo) Per annullare il processo di distribuzione, nel menu di scelta rapida per la voce nel log attività, scegliere **Annulla e Rimuovi**. Questo comando Arresta il processo di distribuzione ed elimina l'ambiente di distribuzione da Azure. Per rimuovere l'ambiente dopo la distribuzione, usare il portale di Azure.

1. (Facoltativo) Una volta avviate le istanze del ruolo, Visual Studio Mostra automaticamente l'ambiente di distribuzione nel **servizi Cloud** nodo in Esplora Server. A questo punto, è possibile visualizzare lo stato di singole istanze del ruolo. Visualizzare [risorse di gestione di Azure con Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md). La figura seguente mostra le istanze del ruolo mentre si trovano ancora nello stato di inizializzazione:

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>Aggiornare un ruolo web come parte del ciclo di sviluppo e test

Se l'infrastruttura di back-end dell'app è stabile, ma i ruoli web richiedono aggiornamenti più frequenti, è possibile utilizzare distribuzione Web per aggiornare solo un ruolo web nel progetto. La funzionalità distribuzione Web è utile quando non si vuole ricompilare e ridistribuire i ruoli di lavoro back-end, o se si dispone di più ruoli web e si desidera aggiornare solo uno dei ruoli web.

### <a name="requirements-for-using-web-deploy"></a>Requisiti per l'uso di distribuzione Web

- **Solo a scopo di sviluppo e test**: le modifiche vengono apportate direttamente alla macchina virtuale in cui è in esecuzione il ruolo web. Se è necessario riciclare questa macchina virtuale, le modifiche andranno perse perché il pacchetto originale pubblicato viene utilizzato per ricreare la macchina virtuale per il ruolo. Ripubblicare l'applicazione per ottenere le modifiche più recenti per il ruolo web.

- **Solo i ruoli web possono essere aggiornati**: non è possibile aggiornare i ruoli di lavoro. Inoltre, non è possibile aggiornare il `RoleEntryPoint` in `web role.cs`.

- **Può supportare solo una singola istanza di un ruolo web**: non è possibile avere più istanze di qualsiasi ruolo web nell'ambiente di distribuzione. Tuttavia, sono supportati più ruoli web con una sola istanza.

- **Abilitare connessioni desktop remoto**: questo requisito consente la distribuzione Web usare l'utente e password per connettersi alla macchina virtuale per distribuire le modifiche al server che esegue Internet Information Services (IIS). Inoltre, potrebbe essere necessario connettersi alla macchina virtuale per aggiungere un certificato attendibile a IIS su questa macchina virtuale. (Questo certificato assicura che la connessione remota per IIS utilizzata da distribuzione Web è protetta).

La procedura seguente presuppone che si sta utilizzando il **pubblica applicazione Azure** procedura guidata.

### <a name="enable-web-deploy-when-you-publish-your-application"></a>Abilita distribuzione Web quando si pubblica l'applicazione

1. Per abilitare la **Abilita distribuzione Web per tutti i ruoli web** opzione, è innanzitutto necessario configurare le connessioni desktop remoto. Selezionare **Abilita Desktop remoto** per tutti i ruoli e quindi specificare le credenziali che viene usato per connettersi in remoto le **configurazione Desktop remoto** finestra visualizzata. Visualizzare [abilitare connessione Desktop remoto per un ruolo nei servizi Cloud di Azure con Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

1. Per abilitare distribuzione Web per tutti i ruoli web nell'applicazione, selezionare **Abilita distribuzione Web per tutti i ruoli web**.

    Viene visualizzato un triangolo giallo. Distribuzione Web utilizza un certificato autofirmato non attendibile per impostazione predefinita, non è consigliata per il caricamento dei dati sensibili. Se occorre proteggere questo processo per i dati sensibili, è possibile aggiungere un certificato SSL da usare per le connessioni di distribuzione Web. Questo certificato deve essere un certificato attendibile. Per altre informazioni, vedere [proteggere distribuzione web](#make-web-deploy-secure).

1. Scegliere **successivo** per visualizzare i **riepilogo** schermata e quindi scegliere **Publish** per distribuire il servizio cloud.

    Il servizio cloud viene pubblicato. La macchina virtuale creata dispone di connessioni remote abilitate per IIS in modo che distribuzione Web possa essere utilizzato per aggiornare i ruoli web senza ripubblicarli.

   > [!NOTE]
   > Se si dispone di più di un'istanza configurata per un ruolo web, viene visualizzato un messaggio di avviso che informa che ogni ruolo web è limitata a una sola istanza nel pacchetto che viene creato per pubblicare l'applicazione. Selezionare **OK** per continuare. Come indicato nella sezione requisiti, è possibile avere più di un ruolo web ma solo un'istanza di ogni ruolo.

### <a name="update-your-web-role-by-using-web-deploy"></a>Aggiornare il ruolo web tramite distribuzione Web

1. Per usare distribuzione Web, apportare modifiche al codice del progetto per uno dei ruoli web in Visual Studio che si desidera pubblicare, quindi fare doppio clic su questo nodo del progetto nella soluzione e scegliere **pubblica**. Il **pubblica sul Web** verrà visualizzata la finestra di dialogo.

1. (Facoltativo) Se è stato aggiunto un certificato SSL attendibile da usare per le connessioni remote per IIS, è possibile cancellare il **Consenti certificato non attendibile** casella di controllo. Per informazioni su come aggiungere un certificato per proteggere distribuzione Web, vedere la sezione **per rendere sicuro distribuzione Web** più avanti in questo articolo.

1. Per usare distribuzione Web, il meccanismo di pubblicazione richiede il nome utente e la password impostata per la connessione Desktop remoto alla prima pubblicazione del pacchetto.

   a. Nelle **nome utente**, immettere il nome utente.

   b. Nelle **Password**, immettere la password.

   c. (Facoltativo) Se si desidera salvare questa password in questo profilo, scegliere **Salva password**.

1. Per pubblicare le modifiche apportate al ruolo web, scegliere **pubblica**.

    Consente di visualizzare la riga dello stato **pubblicazione avviata**. Quando la pubblicazione è stata completata, **pubblicazione completata** viene visualizzata. Le modifiche apportate a questo punto sono state distribuite al ruolo web nella macchina virtuale. A questo punto è possibile avviare l'applicazione Azure nell'ambiente di Azure per testare le modifiche.

### <a name="make-web-deploy-secure"></a>Proteggere distribuzione web

1. Distribuzione Web utilizza un certificato autofirmato non attendibile per impostazione predefinita, non è consigliata per il caricamento dei dati sensibili. Se occorre proteggere questo processo per i dati sensibili, è possibile aggiungere un certificato SSL da usare per le connessioni di distribuzione Web. Questo certificato deve essere un certificato attendibile, pertanto ottengono da un'autorità di certificazione (CA).

    Per proteggere distribuzione Web per ogni macchina virtuale per ognuno dei ruoli web, è necessario caricare il certificato attendibile che si desidera usare per il web distribuire al portale di Azure. Questo certificato assicura che il certificato viene aggiunto alla macchina virtuale che viene creata per il ruolo web quando si pubblica l'applicazione.

1. Per aggiungere un certificato SSL attendibile a IIS da usare per le connessioni remote, seguire questa procedura:

   a. Per connettersi alla macchina virtuale che esegue il ruolo web, selezionare l'istanza del ruolo web in **Cloud Explorer** oppure **Esplora Server**, quindi scegliere il **connettersi tramite Desktop remoto**  comando. Per informazioni dettagliate su come connettersi alla macchina virtuale, vedere [abilitare connessione Desktop remoto per un ruolo nei servizi Cloud di Azure con Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio). Il browser richiede di scaricare un `.rdp` file.

   b. Per aggiungere un certificato SSL, aprire il servizio di gestione in Gestione IIS. In Gestione IIS abilitare SSL aprendo il **associazioni** clic sul collegamento nella **azione** riquadro. Il **Aggiungi Binding sito** verrà visualizzata la finestra di dialogo. Scegli **Add**e quindi scegliere HTTPS nel **tipo** elenco a discesa. Nel **certificato SSL** scegliere il certificato SSL firmato da un'autorità di certificazione e caricato il portale di Azure. Per altre informazioni, vedere [configurare le impostazioni di connessione per il servizio di gestione](http://go.microsoft.com/fwlink/?LinkId=215824).

      > [!NOTE]
      > Se si aggiunge un certificato SSL attendibile, il triangolo giallo di avviso non viene visualizzata la **pubblicazione guidata**.

## <a name="include-files-in-the-service-package"></a>Includere file nel pacchetto del servizio

Potrebbe essere necessario includere file specifici nel pacchetto del servizio in modo che siano disponibili nella macchina virtuale creata per un ruolo. Ad esempio, è possibile aggiungere un `.exe` o un `.msi` file utilizzato da uno script di avvio per il pacchetto del servizio. Oppure potrebbe essere necessario aggiungere un assembly che richiede un progetto di ruolo web worker o ruolo. Per includere file, devono essere aggiunti alla soluzione per l'applicazione Azure.

1. Per aggiungere un assembly a un pacchetto del servizio, procedere come segue:

   a. Nelle **Esplora soluzioni**, aprire il nodo del progetto per il progetto in cui Manca l'assembly di riferimento.
   b. Per aggiungere l'assembly al progetto, aprire il menu di scelta rapida per il **riferimenti** cartella e quindi scegliere **Aggiungi riferimento**. Viene visualizzata la finestra di dialogo Aggiungi riferimento.
   c. Scegliere il riferimento che si desidera aggiungere e quindi scegliere **OK**. Il riferimento viene aggiunto all'elenco sotto il **riferimenti** cartella.
   d. Aprire il menu di scelta rapida per l'assembly che è stato aggiunto e scegliere **proprietà**. Il **proprietà** verrà visualizzata la finestra.

      Per includere questo assembly nel pacchetto del servizio, nelle **elenco Copia localmente** sceglie **True**.
1. Nelle **Esplora soluzioni** aprire il nodo del progetto per il progetto in cui Manca l'assembly di riferimento.

1. Per aggiungere l'assembly al progetto, aprire il menu di scelta rapida per il **riferimenti** cartella e quindi scegliere **Aggiungi riferimento**. Il **Aggiungi riferimento** viene visualizzata la finestra.

1. Scegliere il riferimento che si desidera aggiungere e quindi scegliere il **OK** pulsante.

    Il riferimento viene aggiunto all'elenco sotto il **riferimenti** cartella.

1. Aprire il menu di scelta rapida per l'assembly che è stato aggiunto e scegliere **proprietà**. Viene visualizzata la finestra Proprietà.

1. Per includere questo assembly nel pacchetto del servizio, nelle **Copia localmente** casella di riepilogo **True**.

1. Per includere file nel pacchetto del servizio che sono stati aggiunti al progetto di ruolo web, aprire il menu di scelta rapida per il file e quindi scegliere **proprietà**. Dal **delle proprietà** finestra, scegliere **contenuto** dal **azione di compilazione** casella di riepilogo.

1. Per includere file nel pacchetto del servizio che sono stati aggiunti al progetto di ruolo di lavoro, aprire il menu di scelta rapida per il file e quindi scegliere **proprietà**. Dal **delle proprietà** finestra, scegliere **copia se più recente** dal **copia in directory di output** casella di riepilogo.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sulla pubblicazione in Azure da Visual Studio, vedere [pubblicazione guidata applicazione di Azure](vs-azure-tools-publish-azure-application-wizard.md).
