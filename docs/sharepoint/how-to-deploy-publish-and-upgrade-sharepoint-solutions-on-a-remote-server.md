---
title: Distribuire, pubblicare & aggiornare le soluzioni SharePoint in modalità remota
titleSuffix: ''
description: Distribuire, pubblicare e aggiornare soluzioni SharePoint in modalità sandbox in un sito remoto o in un sito di SharePoint locale.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ab301f11ffdae03564f05388dfbba55a90d12391
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913685"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto
  Oltre a distribuire le soluzioni SharePoint al sistema locale, è possibile pubblicare soluzioni di SharePoint in modalità sandbox in siti remoti o in siti di SharePoint locali. Il processo di pubblicazione remota copia il file con *estensione wsp* nel server SharePoint, installa la soluzione e quindi consente di attivare la soluzione. È inoltre possibile aggiornare un'installazione remota di una soluzione SharePoint dopo che sono state apportate modifiche.

## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Per pubblicare una soluzione SharePoint in modalità sandbox in un server SharePoint remoto

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto SharePoint creato mediante sandbox che si desidera pubblicare, quindi scegliere **pubblica**.

2. Nella finestra di dialogo **pubblica** scegliere il pulsante **di opzione pubblica nel sito di SharePoint** , quindi immettere un URL per un sito di pubblicazione online, ad esempio: `https://mytestsite.sharepoint.microsoftonline.com` .

3. Scegliere il pulsante di opzione **Apri la raccolta soluzioni nel browser dopo la pubblicazione** per visualizzare l'elenco delle soluzioni nella pagina **raccolta** soluzioni dopo la pubblicazione.

4. Fare clic sul pulsante **Pubblica**.

5. Accedere al server remoto se è necessaria l'autenticazione dell'utente.

     Lo stato di avanzamento della pubblicazione viene visualizzato nella finestra di **output** di Visual Studio. Al termine del processo, il file di soluzione (con *estensione wsp*) viene installato nel server SharePoint remoto. Tuttavia, deve essere comunque attivato prima di poter essere utilizzato in SharePoint.

6. Nella pagina **raccolta soluzioni** selezionare l'applicazione SharePoint, quindi sulla barra multifunzione scegliere il pulsante **attiva** .

7. Nella finestra di dialogo **attiva soluzione** , sulla barra multifunzione, scegliere di nuovo il pulsante **attiva** .

     La colonna **stato** nella pagina **raccolta soluzioni** indica che l'applicazione è attiva.

## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Per aggiornare una soluzione di SharePoint in modalità sandbox in un server SharePoint remoto
 Se una soluzione di SharePoint creata mediante sandbox è già pubblicata su un server remoto, il processo seguente consente di aggiornarlo dopo aver apportato modifiche all'applicazione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

1. Rinominare il pacchetto di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . A tale scopo, in **Esplora soluzioni** aprire il pacchetto. Viene visualizzato in **Package Explorer**.

2. In **Package Explorer**, nella casella **nome** , modificare il nome del pacchetto in un nome univoco.

3. Salvare il progetto.

4. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto, quindi scegliere **pubblica**.

5. Nella finestra di dialogo **pubblica** scegliere il pulsante **di opzione pubblica nel sito di SharePoint** e quindi, se l'URL del server remoto in cui è salvata la soluzione non è presente, immetterlo.

6. Scegliere il pulsante di opzione **Apri la raccolta soluzioni nel browser dopo la pubblicazione** per visualizzare l'elenco delle soluzioni nella pagina **raccolta** soluzioni dopo la pubblicazione.

7. Fare clic sul pulsante **Pubblica**.

8. Accedere al server remoto se è necessaria l'autenticazione dell'utente.

     Se è stato eseguito di recente l'accesso al server remoto, è possibile che l'autenticazione non sia obbligatoria.

     Se nel server SharePoint esiste ancora la versione precedente dell'applicazione con lo stesso nome, verrà ricevuto un errore per il fatto che nel server SharePoint esiste già un pacchetto con lo stesso nome. Prima della pubblicazione è necessario rinominare il pacchetto con un nome univoco.

9. Scegliere la nuova applicazione in SharePoint, quindi sulla barra multifunzione scegliere il pulsante **Aggiorna** .

10. Nella finestra di dialogo **Aggiorna soluzione** , sulla barra multifunzione, scegliere di nuovo il pulsante **Aggiorna** . La colonna **stato** nella pagina **raccolta soluzioni** indicherà ora che l'applicazione è attiva.

     La versione precedente della soluzione è disattivata, la nuova versione della soluzione viene aggiornata con i dati conservati dalla soluzione precedente e la nuova soluzione viene attivata in SharePoint.

## <a name="see-also"></a>Vedi anche
- [Procedura: distribuire e pubblicare una soluzione SharePoint in un sito di SharePoint locale](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)
- [Creare pacchetti della soluzione SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
