---
title: Distribuire, pubblicare & aggiornare i pacchetti della soluzione SharePoint
description: Distribuire, pubblicare e aggiornare i pacchetti della soluzione SharePoint. Personalizzare il processo di distribuzione. Pubblicare i pacchetti in un server remoto o locale.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd0dfa3a12c675463c46e93aa0d5b25e8b4bd4b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948856"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Distribuire, pubblicare e aggiornare i pacchetti della soluzione SharePoint
  Dopo aver sviluppato una soluzione SharePoint in Visual Studio, è possibile distribuire il file di pacchetto (con estensione wsp) in un server SharePoint locale o pubblicarlo in un server SharePoint locale o remoto. Se si distribuiscono i file, è possibile personalizzare la modalità di distribuzione dei file del pacchetto (con estensione wsp).

> [!NOTE]
> Attualmente, solo le soluzioni create mediante sandbox possono essere pubblicate nei server SharePoint remoti. Per ulteriori informazioni, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Distribuire, pubblicare e aggiornare
 Per *distribuzione* si intende la copia di un file di soluzione SharePoint compilato da un progetto SharePoint in Visual Studio in un host locale. In una soluzione distribuita è possibile configurare i passaggi di distribuzione, ad esempio il riciclo del pool di Internet Information Services (IIS), l'attivazione della soluzione dopo la distribuzione e così via. Per eseguire la distribuzione, usare il comando **Distribuisci** del menu **Compila** . Per ulteriori informazioni, vedere [procedura: modificare una configurazione di distribuzione di SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) e [procedura: distribuire e pubblicare una soluzione SharePoint in un sito di SharePoint locale](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Per *pubblicazione* si intende il caricamento di un file di soluzione SharePoint in modalità sandbox in un sito di SharePoint remoto. ovvero un sito che si trova in un altro sistema. È anche possibile pubblicare un file di soluzione sandbox di SharePoint in un sito di SharePoint locale, ma indipendentemente dal fatto che il sito pubblicato in sia locale o remoto, non è possibile configurare i passaggi di distribuzione.

 L' *aggiornamento* si riferisce all'aggiornamento di una soluzione SharePoint esistente in remoto o pubblicata localmente. Dopo aver apportato modifiche alla soluzione SharePoint in Visual Studio, è possibile modificare il nome del file del pacchetto della soluzione, ripubblicare la soluzione e quindi aggiornare la soluzione dopo che è stata ripubblicata correttamente. Se si pubblica nuovamente una soluzione pubblicata localmente, è possibile sovrascrivere il file della soluzione esistente.

## <a name="deploy-packages"></a>Distribuire i pacchetti
 È possibile distribuire i file di pacchetto nel server SharePoint nel computer di sviluppo per il test e il debug. È inoltre possibile creare un file di pacchetto che è possibile installare in un altro computer scegliendo il pulsante di opzione **pubblica sul file System** nella finestra di dialogo **pubblica** . Il pacchetto viene creato e copiato nel percorso del file locale specificato. Per distribuire una soluzione SharePoint nel server locale, utilizzare il comando **Distribuisci** del menu **Compila** . Per ulteriori informazioni, vedere [procedura: distribuire e pubblicare una soluzione SharePoint in un sito di SharePoint locale](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Per informazioni su come distribuire una definizione di elenco, aggiungere un ricevitore di eventi e utilizzare Progettazione funzionalità e progettazione pacchetti, vedere [procedura dettagliata: distribuire una definizione di elenco attività progetto](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Personalizzare il processo di distribuzione
 Nella tabella seguente vengono illustrate le due configurazioni di distribuzione che è possibile utilizzare quando si esegue il debug e si distribuisce una soluzione SharePoint.

|Configurazione della distribuzione|Descrizione|
|------------------------------|-----------------|
|Predefinito|Configurazione di distribuzione predefinita. Vengono eseguiti i passaggi di distribuzione seguenti:<br /><br /> 1. eseguire il comando pre-distribuzione.<br />2. riciclare il pool di applicazioni IIS.<br />3. ritirare la soluzione.<br />4. aggiungere la soluzione.<br />5. attivare le funzionalità.<br />6. eseguire il comando post-distribuzione.<br /><br /> Quando si disinstalla un pacchetto, vengono eseguiti i seguenti passaggi di ritrazione.<br /><br /> 1. riciclare il pool di applicazioni IIS.<br />2. ritirare la soluzione.|
|Nessuna attivazione|Questa configurazione di distribuzione esegue gli stessi passaggi della configurazione predefinita, ma ignora il passaggio di attivazione.|

 È possibile creare configurazioni di distribuzione personalizzate per completare un singolo passaggio o modificare l'ordine dei passaggi del processo di distribuzione. Per altre informazioni, vedere [procedura: modificare una configurazione di distribuzione di SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 È anche possibile aggiungere comandi da eseguire prima e dopo la distribuzione. Per altre informazioni, vedere [procedura: impostare i comandi di distribuzione di SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Pubblicare i pacchetti in un server remoto o locale
 Per pubblicare una soluzione SharePoint in modalità sandbox in un server remoto, sulla barra dei menu scegliere **Compila**, **pubblica**, quindi nella finestra di dialogo **pubblica** scegliere il pulsante di opzione **pubblica nel sito di SharePoint** , specificando l'URL del server remoto, ad esempio `https://someremoteserver.sharepoint.microsoftonline.com` .

 Per pubblicare una soluzione SharePoint in un server locale, nella finestra di dialogo **pubblica** scegliere il pulsante **di opzione pubblica sul file System** , specificando un percorso di sistema locale.

 Dopo che una soluzione è stata pubblicata in SharePoint, la soluzione viene visualizzata nella **raccolta soluzioni** in cui è possibile attivarla. Per ulteriori informazioni, vedere [procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Aggiornare i pacchetti pubblicati
 Se si apportano modifiche a un progetto SharePoint in Visual Studio dopo la pubblicazione, è necessario aggiornare il pacchetto pubblicato per includere le modifiche. Per eseguire correttamente l'aggiornamento, un pacchetto deve avere un nome univoco. Se nel sito di SharePoint viene trovato un pacchetto con lo stesso nome, che può verificarsi durante l'aggiornamento di un'applicazione esistente, viene visualizzato un errore che segnala il conflitto con il nome del file e consente di rinominare il pacchetto. Dopo la ripubblicazione, il nuovo pacchetto viene visualizzato nel sito di SharePoint e può essere aggiornato. Un pacchetto aggiornato aggiorna la soluzione usando i dati del pacchetto precedente e quindi attiva la soluzione in SharePoint. Per ulteriori informazioni, vedere [procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Vedi anche
- [Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
