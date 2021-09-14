---
title: Distribuire, pubblicare e & aggiornare SharePoint in modalità remota
titleSuffix: ''
description: Distribuire, pubblicare e aggiornare soluzioni SharePoint sandbox in un sito remoto o in un sito SharePoint locale.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: fb4838625029a95f2c7b6d55cfba22284c168818
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636859"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Procedura: Distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto
  Oltre a distribuire soluzioni SharePoint nel sistema locale, è possibile pubblicare soluzioni SharePoint sandbox in siti remoti o SharePoint locali. Il processo di pubblicazione remota copia il file con estensione *wsp* nel server SharePoint, installa la soluzione e quindi consente di attivare la soluzione. È anche possibile aggiornare un'installazione SharePoint soluzione remota dopo aver apportato modifiche.

## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Per pubblicare una soluzione SharePoint sandbox in un server SharePoint remoto

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto SharePoint sandbox da pubblicare e quindi scegliere **Pubblica**.

2. Nella finestra **di** dialogo Pubblica scegliere il pulsante di opzione Pubblica SharePoint **sito** e quindi immettere un URL per un sito di pubblicazione online, ad esempio: `https://mytestsite.sharepoint.microsoftonline.com` .

3. Scegliere il **pulsante di opzione Apri** raccolta soluzioni nel browser dopo la pubblicazione per visualizzare l'elenco di soluzioni nella pagina **Raccolta** soluzioni dopo la pubblicazione.

4. Fare clic sul pulsante **Pubblica**.

5. Accedere al server remoto se è necessaria l'autenticazione utente.

     Lo stato di pubblicazione viene visualizzato nella Visual Studio **Output.** Al termine del processo, il file della soluzione ( con estensione *wsp*) viene installato nel server SharePoint remoto. Tuttavia, deve essere ancora attivato prima di poter essere usato in SharePoint.

6. Nella pagina **Raccolta soluzioni** selezionare l'applicazione SharePoint e quindi sulla barra multifunzione scegliere il **pulsante Attiva.**

7. Nella finestra **di dialogo** Attiva soluzione scegliere nuovamente il **pulsante Attiva** sulla barra multifunzione.

     La **colonna** Stato nella **pagina Raccolta soluzioni** indica che l'applicazione è attiva.

## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Per aggiornare una soluzione SharePoint sandbox in un server SharePoint remoto
 Se una soluzione SharePoint sandbox è già pubblicata in un server remoto, il processo seguente consente di aggiornarla dopo aver apportato modifiche all'applicazione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

1. Rinominare il SharePoint pacchetto in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . A tale scopo, in **Esplora soluzioni** aprire il pacchetto. Viene visualizzato in **Esplora pacchetti**.

2. Nella **casella Nome**  di Esplora pacchetti modificare il nome del pacchetto in un nome univoco.

3. Salvare il progetto.

4. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto e quindi scegliere **Pubblica**.

5. Nella finestra **di** dialogo Pubblica scegliere il pulsante di opzione Pubblica nel sito SharePoint e quindi, se l'URL del server remoto **in** cui viene salvata la soluzione non è presente, immetterlo.

6. Scegliere il **pulsante di opzione Apri** raccolta soluzioni nel browser dopo la pubblicazione per visualizzare l'elenco di soluzioni nella pagina **Raccolta** soluzioni dopo la pubblicazione.

7. Fare clic sul pulsante **Pubblica**.

8. Accedere al server remoto se è necessaria l'autenticazione utente.

     Se è stato eseguito l'accesso al server remoto di recente, l'autenticazione potrebbe non essere necessaria.

     Se la versione precedente dell'applicazione con lo stesso nome esiste ancora nel server SharePoint, verrà visualizzato un errore che indica che un pacchetto con lo stesso nome esiste già nel server SharePoint. È necessario rinominare il pacchetto con un nome univoco prima della pubblicazione.

9. Scegliere la nuova applicazione in SharePoint quindi sulla barra multifunzione scegliere il **pulsante** Aggiorna.

10. Nella finestra **di dialogo Aggiorna** soluzione scegliere di nuovo il **pulsante** Aggiorna sulla barra multifunzione. La **colonna Stato** nella pagina **Raccolta** soluzioni dovrebbe ora indicare che l'applicazione è attiva.

     La versione precedente della soluzione viene disattivata, la nuova versione della soluzione viene aggiornata con i dati gestiti dalla soluzione precedente e la nuova soluzione viene attivata in SharePoint.

## <a name="see-also"></a>Vedi anche
- [Procedura: Distribuire e pubblicare una soluzione SharePoint in un sito SharePoint locale](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)
- [Creare SharePoint pacchetti della soluzione](../sharepoint/creating-sharepoint-solution-packages.md)
- [Procedura: Personalizzare un pacchetto SharePoint soluzione](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Procedura: Aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
