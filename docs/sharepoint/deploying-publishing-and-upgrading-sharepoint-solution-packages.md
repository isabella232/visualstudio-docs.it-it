---
title: Distribuire, pubblicare & aggiornare i pacchetti della soluzione SharePointDeploy, publish, & upgrade SharePoint solution packages
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d8e55b01173e749395f60d189366a08907bdaccd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444970"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Distribuire, pubblicare e aggiornare pacchetti di soluzioni SharePointDeploy, publish, and upgrade SharePoint solution packages
  Dopo aver sviluppato una soluzione SharePoint in Visual Studio, è possibile distribuire il relativo file di pacchetto (con estensione wsp) in un server SharePoint locale o pubblicarlo in un server SharePoint remoto o locale. Se si distribuiscono i file, è possibile personalizzare la modalità di distribuzione dei file del pacchetto (con estensione wsp).

> [!NOTE]
> Attualmente, solo le soluzioni in modalità sandbox possono essere pubblicate in server SharePoint remoti. Per ulteriori informazioni, consultate [Considerazioni sulle soluzioni in modalità sandbox](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Distribuire, pubblicare e aggiornare
 *Per distribuzione* si intende la copia di un file di soluzione SharePoint compilato da un progetto SharePoint in Visual Studio in un host locale. In una soluzione distribuita è possibile configurare i passaggi di distribuzione, ad esempio il riciclo del pool di Internet Information Services (IIS), l'attivazione della soluzione dopo la distribuzione e così via. Per eseguire la distribuzione, utilizzare il comando **Distribuisci** del menu **Compila** . Per ulteriori informazioni, vedere [Procedura: modificare una configurazione](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) di distribuzione di SharePoint e [Procedura: distribuire e pubblicare una soluzione di SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)in un sito di SharePoint locale .

 *Per pubblicazione* si intende il caricamento di un file di soluzione SharePoint in modalità sandbox in un sito di SharePoint remoto. vale a dire, un sito situato su un altro sistema. È anche possibile pubblicare un file di soluzione in modalità sandbox di SharePoint in un sito di SharePoint locale, ma indipendentemente dal fatto che il sito pubblicato in sia locale o remoto, non è possibile configurare i passaggi di distribuzione.

 *L'aggiornamento* si riferisce all'aggiornamento di una soluzione SharePoint pubblicata in remoto o in locale. Dopo aver apportato le modifiche alla soluzione SharePoint in Visual Studio, modificare il nome del file del pacchetto della soluzione, ripubblicare la soluzione e quindi aggiornare la soluzione dopo la ripubblicazione. Se si ripubblica una soluzione pubblicata localmente, è possibile sovrascrivere il file di soluzione esistente.

## <a name="deploy-packages"></a>Distribuire i pacchetti
 È possibile distribuire i file di pacchetto nel server SharePoint nel computer di sviluppo per il test e il debug. È inoltre possibile creare un file di pacchetto che è possibile installare in un altro computer scegliendo il pulsante di opzione **Pubblica nel file system** nella finestra di dialogo **Pubblica.** Il pacchetto viene creato e copiato nel percorso del file locale specificato. Per distribuire una soluzione SharePoint nel server locale, utilizzare il comando **Distribuisci** del menu **Compila** . Per ulteriori informazioni, vedere [Procedura: distribuire e pubblicare una soluzione SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)in un sito di SharePoint locale.

 Per informazioni su come distribuire una definizione di elenco, aggiungere un ricevitore di eventi e usare Progettazione funzionalità e Progettazione pacchetti, vedere [Procedura dettagliata: distribuzione](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)di una definizione di elenco attività del progetto .

## <a name="customize-the-deployment-process"></a>Personalizzare il processo di distribuzione
 Nella tabella seguente vengono illustrate le due configurazioni di distribuzione che è possibile utilizzare quando si esegue il debug e si distribuisce una soluzione SharePoint.The following table shows the two deployment configurations that you can use when you debug and deploy a SharePoint solution.

|Configurazione di distribuzione|Descrizione|
|------------------------------|-----------------|
|Predefinito|Configurazione di distribuzione predefinita. Vengono eseguiti i passaggi di distribuzione seguenti:The following deployment steps are performed:<br /><br /> 1. Eseguire il comando pre-distribuzione.<br />2. Riciclare il pool di applicazioni IIS.<br />3. Ritirare la soluzione.<br />4. Aggiungere la soluzione.<br />5. Attivare le funzioni.<br />6. Eseguire il comando post-distribuzione.<br /><br /> Quando un pacchetto viene disinstallato, vengono eseguite le seguenti operazioni di ritiro.<br /><br /> 1. Riciclare il pool di applicazioni IIS.<br />2. Ritirare la soluzione.|
|Nessuna attivazione|Questa configurazione di distribuzione esegue gli stessi passaggi della configurazione predefinita, ma ignora il passaggio di attivazione.|

 È possibile creare configurazioni di distribuzione personalizzate per completare un singolo passaggio o modificare l'ordine dei passaggi nel processo di distribuzione. Per ulteriori informazioni, vedere [Procedura: modificare una configurazione](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)di distribuzione di SharePoint .

 È inoltre possibile aggiungere comandi da eseguire prima e dopo la distribuzione. Per ulteriori informazioni, vedere [Procedura: Impostare i comandi](../sharepoint/how-to-set-sharepoint-deployment-commands.md)di distribuzione di SharePoint .

## <a name="publish-packages-to-a-remote-or-local-server"></a>Pubblicare pacchetti in un server remoto o localePublish packages to a remote or local server
 Per pubblicare una soluzione SharePoint in modalità sandbox in un server remoto, sulla barra dei menu scegliere **Compila**, **Pubblica**e quindi nella finestra di dialogo **Pubblica** scegliere il pulsante di opzione Pubblica nel sito di **SharePoint,** specificando l'URL del server remoto, ad `https://someremoteserver.sharepoint.microsoftonline.com`esempio .

 Per pubblicare una soluzione SharePoint in un server locale, nella finestra di dialogo **Pubblica** scegliere il pulsante di opzione **Pubblica nel file system,** specificando un percorso di sistema locale.

 Dopo che una soluzione viene pubblicata correttamente in SharePoint, la soluzione viene visualizzata nella **raccolta** soluzioni in cui è possibile attivarla. Per ulteriori informazioni, vedere [Procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Aggiornare i pacchetti pubblicati
 Se si apportano modifiche a un progetto SharePoint in Visual Studio dopo la pubblicazione, il pacchetto pubblicato deve essere aggiornato per includere le modifiche. Per eseguire correttamente l'aggiornamento, un pacchetto deve avere un nome univoco. Se nel sito di SharePoint viene trovato un pacchetto con lo stesso nome, che può verificarsi quando si aggiorna un'applicazione esistente, viene visualizzato un errore che segnala il conflitto di nomi di file e consente di rinominare il pacchetto. Dopo la ripubblicazione, il nuovo pacchetto viene visualizzato nel sito di SharePoint e può essere aggiornato. Un pacchetto aggiornato aggiorna la soluzione utilizzando i dati del pacchetto precedente e quindi attiva la soluzione in SharePoint. Per ulteriori informazioni, vedere [Procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Vedere anche
- [Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
