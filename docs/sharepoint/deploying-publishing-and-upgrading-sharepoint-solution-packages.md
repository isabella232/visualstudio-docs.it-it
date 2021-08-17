---
title: Distribuire, pubblicare e aggiornare & pacchetti SharePoint soluzione
description: Distribuire, pubblicare e aggiornare i pacchetti SharePoint soluzione. Personalizzare il processo di distribuzione. Pubblicare pacchetti in un server remoto o locale.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: d0dd6332a6ce1f7b0a1940e392918004f246cc525ab48030c15085b82ba54d42
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425531"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Distribuire, pubblicare e aggiornare i pacchetti SharePoint soluzione
  Dopo aver sviluppato una soluzione SharePoint in Visual Studio, è possibile distribuirne il file di pacchetto (con estensione wsp) in un server SharePoint locale o pubblicarlo in un server SharePoint remoto. Se si distribuiscono i file, è possibile personalizzare la modalità di distribuzione dei file del pacchetto (con estensione wsp).

> [!NOTE]
> Attualmente, solo le soluzioni sandbox possono essere pubblicate in server SharePoint remoti. Per altre informazioni, vedere [Considerazioni sulle soluzioni in modalità sandbox.](../sharepoint/sandboxed-solution-considerations.md)

## <a name="deploy-publish-and-upgrade"></a>Distribuire, pubblicare e aggiornare
 *La distribuzione* si riferisce alla copia SharePoint file di soluzione compilato da un progetto SharePoint in Visual Studio in un host locale. In una soluzione distribuita è possibile configurare i passaggi di distribuzione, ad esempio riciclare il pool di Internet Information Services (IIS), attivare la soluzione dopo la distribuzione e così via. Per eseguire la distribuzione, usare **il comando** Distribuisci nel menu **Compila.** Per altre informazioni, vedere [Procedura:](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) Modificare una configurazione di distribuzione SharePoint e [Procedura:](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)Distribuire e pubblicare una soluzione SharePoint in un sito SharePoint locale .

 *La* pubblicazione si riferisce al caricamento di un file di soluzione SharePoint sandbox in un sito SharePoint remoto. in altre informazioni, un sito che si trova in un altro sistema. È anche possibile pubblicare un file di soluzione SharePoint sandbox in un sito SharePoint locale, ma indipendentemente dal fatto che il sito pubblicato in sia locale o remoto, non è possibile configurarne i passaggi di distribuzione.

 *L'aggiornamento* si riferisce all'aggiornamento di una soluzione pubblicata in remoto o SharePoint locale esistente. Dopo aver apportato modifiche alla soluzione SharePoint in Visual Studio, modificare il nome del file del pacchetto della soluzione, ripubblicare la soluzione e quindi aggiornare la soluzione dopo la ripubblicazione. Se si ripubblica una soluzione pubblicata localmente, è possibile sovrascrivere il file di soluzione esistente.

## <a name="deploy-packages"></a>Distribuire i pacchetti
 È possibile distribuire i file di pacchetto nel server SharePoint nel computer di sviluppo per il test e il debug. È anche possibile creare un file di pacchetto che è possibile installare in un altro computer scegliendo il pulsante di opzione Pubblica nel **file system** nella finestra **di dialogo** Pubblica . Il pacchetto viene creato e copiato nel percorso del file locale specificato. Per distribuire una SharePoint nel server locale, usare il **comando** Distribuisci del menu **Compila.** Per altre informazioni, vedere Procedura: Distribuire e pubblicare una soluzione [SharePoint in un sito SharePoint locale.](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)

 Per informazioni su come distribuire una definizione di elenco, aggiungere un ricevitore di eventi e usare Progettazione funzionalità e Progettazione pacchetti, vedere [Procedura dettagliata: Distribuire una](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)definizione di elenco di attività di progetto .

## <a name="customize-the-deployment-process"></a>Personalizzare il processo di distribuzione
 La tabella seguente illustra le due configurazioni di distribuzione che è possibile usare quando si esegue il debug e si distribuisce una SharePoint soluzione.

|Configurazione della distribuzione|Descrizione|
|------------------------------|-----------------|
|Predefinito|Configurazione della distribuzione predefinita. Vengono eseguiti i passaggi di distribuzione seguenti:<br /><br /> 1. Eseguire il comando di pre-distribuzione.<br />2. Riciclare il pool di applicazioni IIS.<br />3. Ritirare la soluzione.<br />4. Aggiungere la soluzione.<br />5. Attivare le funzionalità.<br />6. Eseguire il comando post-distribuzione.<br /><br /> Quando un pacchetto viene disinstallato, vengono eseguiti i passaggi di ritiro seguenti.<br /><br /> 1. Riciclare il pool di applicazioni IIS.<br />2. Ritirare la soluzione.|
|Nessuna attivazione|Questa configurazione di distribuzione esegue gli stessi passaggi della configurazione predefinita, ma ignora il passaggio di attivazione.|

 È possibile creare configurazioni di distribuzione personalizzate per completare un singolo passaggio o modificare l'ordine dei passaggi nel processo di distribuzione. Per altre informazioni, vedere [Procedura: Modificare una configurazione di SharePoint distribuzione .](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)

 È anche possibile aggiungere comandi da eseguire prima e dopo la distribuzione. Per altre informazioni, vedere [Procedura: Impostare i SharePoint di distribuzione.](../sharepoint/how-to-set-sharepoint-deployment-commands.md)

## <a name="publish-packages-to-a-remote-or-local-server"></a>Pubblicare pacchetti in un server remoto o locale
 Per pubblicare una soluzione SharePoint SharePoint in un server remoto, sulla barra dei menu  scegliere Compila **,** Pubblica e quindi nella finestra di dialogo Pubblica scegliere il pulsante di opzione Pubblica nel sito **SharePoint** , specificando l'URL del server remoto, ad esempio `https://someremoteserver.sharepoint.microsoftonline.com` .

 Per pubblicare una SharePoint in un server  locale, nella finestra di dialogo Pubblica scegliere il pulsante di opzione Pubblica nel **file system,** specificando un percorso di sistema locale.

 Dopo che una soluzione è stata pubblicata SharePoint, la soluzione viene visualizzata nella **Raccolta soluzioni** in cui è possibile attivarla. Per altre informazioni, vedere [Procedura: Distribuire, pubblicare](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)e aggiornare soluzioni SharePoint in un server remoto.

### <a name="upgrade-published-packages"></a>Aggiornare i pacchetti pubblicati
 Se si apportano modifiche a un progetto SharePoint in Visual Studio dopo la pubblicazione, il pacchetto pubblicato deve essere aggiornato per includere le modifiche. Per eseguire correttamente l'aggiornamento, un pacchetto deve avere un nome univoco. Se nel sito di SharePoint viene trovato un pacchetto con lo stesso nome, che può verificarsi durante l'aggiornamento di un'applicazione esistente, un errore segnala il conflitto di nome file e consente di rinominare il pacchetto. Dopo la ripubblicazione, il nuovo pacchetto viene visualizzato nel SharePoint e può essere aggiornato. Un pacchetto aggiornato aggiorna la soluzione usando i dati del pacchetto precedente e quindi attiva la soluzione in SharePoint. Per altre informazioni, vedere [Procedura: Distribuire, pubblicare](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)e aggiornare soluzioni SharePoint in un server remoto.

## <a name="see-also"></a>Vedi anche
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
