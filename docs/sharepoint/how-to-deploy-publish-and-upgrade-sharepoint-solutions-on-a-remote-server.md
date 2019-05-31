---
title: Distribuire, pubblicare e aggiornare soluzioni SharePoint in modalità remota
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c8e9c46a9acaf8c70fa434514785276f9ba343d4
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401424"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Procedura: Distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto
  Oltre a distribuire soluzioni di SharePoint al sistema locale, è possibile pubblicare soluzioni create mediante sandbox di SharePoint a siti remoti o i siti SharePoint locali. Le copie di processo di pubblicazione remoto il *wsp* file nel server SharePoint, installa la soluzione e quindi consente di attivare la soluzione. È inoltre possibile aggiornare un'installazione di soluzioni di SharePoint remota dopo aver apportato modifiche a esso.

## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Per pubblicare una soluzione creata mediante sandbox di SharePoint in un server SharePoint remoto

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto in modalità sandbox di SharePoint che si desidera pubblicare e quindi scegliere **Publish**.

2. Nel **Publish** finestra di dialogo scegliere la **pubblica sul sito di SharePoint** pulsante di opzione e quindi immettere un URL per un sito di pubblicazione online, ad esempio: `https://mytestsite.sharepoint.microsoftonline.com`.

3. Scegliere il **aprire la pagina Raccolta soluzioni nel browser dopo la pubblicazione** pulsante di opzione per visualizzare l'elenco delle soluzioni nel **raccolta soluzioni** pagina dopo la pubblicazione.

4. Scegliere il **pubblica** pulsante.

5. Accedere al server remoto se è necessaria l'autenticazione utente.

     Viene visualizzato lo stato della pubblicazione in Visual Studio **Output** finestra. Quando il processo viene completato, la soluzione (*wsp*) file viene installato nel server SharePoint remoto. Tuttavia, deve ancora essere attivato prima di poter essere utilizzato in SharePoint.

6. Nel **raccolta soluzioni** pagina, selezionare l'applicazione di SharePoint e quindi sulla barra multifunzione scegliere la **Activate** pulsante.

7. Nel **soluzione attiva** finestra di dialogo, nella barra multifunzione, scegliere il **Activate** nuovamente clic sul pulsante.

     Il **lo stato** colonna il **raccolta soluzioni** pagina indica che l'applicazione è attiva.

## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Per eseguire l'aggiornamento di una soluzione creata mediante sandbox di SharePoint in un server SharePoint remoto
 Se una soluzione creata mediante sandbox di SharePoint è già pubblicata in un server remoto, il processo seguente consente di eseguire l'aggiornamento dopo aver apportato modifiche all'applicazione nel [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

1. Rinominare il pacchetto di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. A questo scopo, nella **Esplora soluzioni** aprire il pacchetto. Viene visualizzato nei **Esplora pacchetti**.

2. Nelle **Package Explorer**, nella **nome** , modificare il nome del pacchetto con un nome univoco.

3. Salvare il progetto.

4. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto e quindi scegliere **Publish**.

5. Nel **Publish** finestra di dialogo scegliere la **pubblica sul sito di SharePoint** pulsante di opzione e quindi, se l'URL per il server remoto in cui la soluzione viene salvata non è presente, l'immissione.

6. Scegliere il **aprire la pagina Raccolta soluzioni nel browser dopo la pubblicazione** pulsante di opzione per visualizzare l'elenco delle soluzioni nel **raccolta soluzioni** pagina dopo la pubblicazione.

7. Scegliere il **pubblica** pulsante.

8. Accedere al server remoto se è necessaria l'autenticazione utente.

     Se connesso al server remoto di recente, potrebbe non essere necessaria l'autenticazione.

     Se la versione precedente dell'applicazione che ha lo stesso nome esiste ancora nel server SharePoint, si otterrà un errore che un pacchetto con lo stesso nome esiste già nel server SharePoint. È necessario rinominare il pacchetto con un nome univoco prima della pubblicazione.

9. Scegliere la nuova applicazione in SharePoint e quindi sulla barra multifunzione scegliere la **aggiornare** pulsante.

10. Nel **aggiornare la soluzione** finestra di dialogo, nella barra multifunzione, scegliere il **aggiornare** nuovamente clic sul pulsante. Il **lo stato** colonna il **raccolta soluzioni** pagina dovrebbe ora indicare che l'applicazione è attiva.

     La versione precedente della soluzione è disattivata, la nuova versione della soluzione viene aggiornata con dati gestiti dalla soluzione precedente e la nuova soluzione viene attivata in SharePoint.

## <a name="see-also"></a>Vedere anche
- [Procedura: Distribuire e pubblicare una soluzione di SharePoint in un sito di SharePoint locale](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)
- [Creare pacchetti delle soluzioni SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Procedura: Personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Procedura: Aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
