---
title: La distribuzione, pubblicazione e aggiornamento dei pacchetti delle soluzioni SharePoint | Microsoft Docs
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
ms.openlocfilehash: 093016b3924d7882901a2b2c1bda060571d5bff4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618406"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Distribuire, pubblicare e aggiornare i pacchetti di soluzioni SharePoint
  Dopo aver sviluppato una soluzione di SharePoint in Visual Studio, è possibile distribuire il file del pacchetto (con estensione wsp) in un server SharePoint locale o pubblicata in un server SharePoint locale o remoto. Se si distribuiscono i file, è possibile personalizzare la distribuzione di file del pacchetto (con estensione wsp).

> [!NOTE]
>  Attualmente, solo soluzioni create mediante sandbox possono essere pubblicate in server remoti di SharePoint. Per altre informazioni, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Distribuire, pubblicare e aggiornare
 *Distribuzione* fa riferimento alla copia un file di soluzione SharePoint compilato da un progetto SharePoint in Visual Studio in un host locale. In una soluzione distribuita, è possibile configurare la procedura di distribuzione, ad esempio riciclo del pool di Internet Information Services (IIS), l'attivazione della soluzione dopo la distribuzione e così via. Per distribuire, usare il **Deploy** comando le **compilare** menu. Per altre informazioni, vedere [Procedura: Modificare una configurazione di distribuzione di SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) e [come: Distribuire e pubblicare una soluzione di SharePoint in un sito di SharePoint locale](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 *Pubblicazione* si riferisce al caricamento di un file di soluzione SharePoint in modalità sandbox in SharePoint remoto sito, vale a dire un sito che si trova in un altro sistema. È anche possibile pubblicare un file di soluzione creata mediante sandbox di SharePoint in un sito di SharePoint locale, ma indipendentemente dal fatto che il sito pubblicato sia locale o remoto, non è possibile configurare la procedura di distribuzione.

 *L'aggiornamento* si riferisce all'aggiornamento di una soluzione di SharePoint pubblicata in locale o esistente in modalità remota. Dopo aver apportato eventuali modifiche alla soluzione di SharePoint in Visual Studio, modificare il nome di file del pacchetto della soluzione, ripubblicare la soluzione e quindi aggiornare la soluzione dopo lo Ripubblica correttamente. Se si pubblica nuovamente una soluzione pubblicata in locale, è possibile sovrascrivere il file della soluzione esistente.

## <a name="deploy-packages"></a>Distribuire i pacchetti
 È possibile distribuire i file di pacchetto per il server SharePoint nel computer di sviluppo per il test e debug. È anche possibile creare un file di pacchetto che è possibile installare in un altro computer, scegliere il **pubblicare nel File System** pulsante di opzione il **Publish** nella finestra di dialogo. Il pacchetto viene creato e copiato nel percorso file locale specificato. Per distribuire una soluzione di SharePoint al server locale, usare il **Deploy** comando le **compilazione** menu. Per altre informazioni, vedere [Procedura: Distribuire e pubblicare una soluzione di SharePoint in un sito di SharePoint locale](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Per informazioni su come distribuire una definizione di elenco, aggiungere un ricevitore di eventi e usare la progettazione di funzionalità e pacchetto, vedere [procedura dettagliata: Distribuire una definizione di elenco attività di progetto](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Personalizzare il processo di distribuzione
 La tabella seguente illustra le due configurazioni di distribuzione che è possibile usare quando si eseguire il debug e distribuisce una soluzione di SharePoint.

|Configurazione della distribuzione|Descrizione|
|------------------------------|-----------------|
|Impostazione predefinita|La configurazione della distribuzione predefinita. Vengono eseguiti i passaggi di distribuzione seguenti:<br /><br /> 1.  Esegui comando pre-distribuzione.<br />2.  Ricicla pool di applicazioni IIS.<br />3.  Ritirare la soluzione.<br />4.  Aggiungere soluzioni.<br />5.  Attivare le funzionalità.<br />6.  Esegui comando post-distribuzione.<br /><br /> Quando si disinstalla un pacchetto, vengono eseguite le seguenti fasi di ritrazione.<br /><br /> 1.  Ricicla pool di applicazioni IIS.<br />2.  Ritirare la soluzione.|
|Nessuna attivazione|Questa configurazione di distribuzione esegue le stesse operazioni come la configurazione predefinita, ma ignora il passaggio di attivazione.|

 È possibile creare le proprie configurazioni di distribuzione per completare un unico passaggio oppure modificare l'ordine dei passaggi del processo di distribuzione. Per altre informazioni, vedere [Procedura: Modificare una configurazione di distribuzione di SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 È anche possibile aggiungere comandi da eseguire prima e dopo la distribuzione. Per altre informazioni, vedere [Procedura: Impostare i comandi di distribuzione di SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Pubblicare pacchetti in un server locale o remoto
 Per pubblicare una soluzione creata mediante sandbox di SharePoint in un server remoto, nella barra dei menu, scegliere **compilare**, **pubblica**, quindi il **pubblica** finestra di dialogo, seleziona il **Pubblica sul sito di SharePoint** pulsante di opzione, fornendo l'URL del server remoto, ad esempio **https://someremoteserver.sharepoint.microsoftonline.com**.

 Per pubblicare una soluzione di SharePoint a un server locale, nelle **Publish** finestra di dialogo scegliere la **pubblicare nel File System** pulsante di opzione, specificare un percorso di sistema locale.

 Dopo che una soluzione correttamente pubblica in SharePoint, la soluzione è inclusa nel **raccolta soluzioni** in cui è possibile attivarlo. Per altre informazioni, vedere [Procedura: Distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Aggiornare i pacchetti pubblicati
 Se si apportano modifiche a un progetto SharePoint in Visual Studio dopo la pubblicazione, è necessario aggiornare il pacchetto pubblicato per includere le modifiche. Per aggiornare correttamente, un pacchetto deve avere un nome univoco. Se un pacchetto con lo stesso nome viene trovato nel sito di SharePoint, che può verificarsi quando si aggiorna un'applicazione esistente - gli avvisi di un errore per il nome del file in conflitto e consente di rinominare il pacchetto. Dopo venga pubblicato nuovamente, il nuovo pacchetto viene visualizzata nel sito di SharePoint e può essere aggiornato. Un pacchetto aggiornato Aggiorna la soluzione utilizzando i dati dal pacchetto precedente e quindi attiva la soluzione in SharePoint. Per altre informazioni, vedere [Procedura: Distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Vedere anche
- [Il pacchetto e distribuire soluzioni di SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
