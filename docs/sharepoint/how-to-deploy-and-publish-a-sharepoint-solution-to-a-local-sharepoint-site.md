---
title: Distribuire & la soluzione di pubblicazione SharePoint nel sito di SharePoint locale
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 59d4fe41565d0aaf0c52cae9434d4a576dc26baa
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016820"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Procedura: distribuire e pubblicare una soluzione SharePoint in un sito di SharePoint locale
  È possibile distribuire o pubblicare soluzioni SharePoint in un server SharePoint locale nel computer di sviluppo. Il processo di distribuzione copia il file con *estensione wsp* nel server SharePoint, installa la soluzione e quindi attiva le funzionalità. Il processo di pubblicazione copia il file con estensione *WSP* nel server SharePoint e lo installa. È necessario attivarla manualmente per abilitarla in SharePoint.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Per distribuire una soluzione SharePoint nel server SharePoint locale

1. In **Esplora soluzioni**scegliere il progetto che si desidera distribuire.

2. Sulla barra dei menu scegliere **Compila**, **Distribuisci soluzione**.

     Il file con *estensione wsp* viene creato e installato nel server SharePoint locale. Inoltre, le funzionalità sono attivate.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Per pubblicare una soluzione SharePoint in un server SharePoint locale

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto SharePoint che si desidera pubblicare, quindi scegliere **pubblica**.

2. Nella finestra di dialogo **pubblica** scegliere il pulsante **di opzione pubblica sul file System** .

3. Nella casella di testo percorso di **destinazione** immettere un percorso locale, quindi scegliere il pulsante **pubblica** .

     Lo stato di avanzamento della pubblicazione viene visualizzato nella finestra di **output** di Visual Studio. Al termine del processo, il file di soluzione (con*estensione wsp*) viene installato nel server SharePoint locale. Tuttavia, deve essere comunque attivato per essere utilizzato in SharePoint. Se il file della soluzione esiste già, si verifica un errore e viene chiesto se si desidera sovrascrivere il file esistente. Per informazioni sull'aggiornamento del pacchetto, vedere la sezione sull'aggiornamento di pacchetti remoti in [procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [Creare pacchetti della soluzione SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
