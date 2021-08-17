---
title: Distribuire & pubblicare SharePoint soluzione nel sito SharePoint locale
titleSuffix: ''
description: Vedere come distribuire o pubblicare soluzioni SharePoint in un server SharePoint locale nel computer di sviluppo.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 0ca33017e48db24a4f1ab055289683737d047c4e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047712"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Procedura: Distribuire e pubblicare una soluzione SharePoint in un sito SharePoint locale
  È possibile distribuire o pubblicare SharePoint in un server SharePoint locale nel computer di sviluppo. Il processo di distribuzione copia il file con estensione *wsp* nel server SharePoint, installa la soluzione e quindi attiva le funzionalità. Il processo di pubblicazione copia solo il file con estensione *wsp* nel server SharePoint e lo installa. È necessario attivarlo manualmente per abilitarlo in SharePoint.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Per distribuire una SharePoint di distribuzione nel server SharePoint locale

1. In **Esplora soluzioni** scegliere il progetto da distribuire.

2. Sulla barra dei menu scegliere **Compila**, **Distribuisci soluzione.**

     Il file *con estensione wsp* viene creato e installato nel server SharePoint locale. Inoltre, le funzionalità vengono attivate.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Per pubblicare una SharePoint in un server SharePoint locale

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto SharePoint da pubblicare e quindi scegliere **Pubblica.**

2. Nella finestra **di** dialogo Pubblica scegliere il pulsante **di opzione Pubblica** nel file system .

3. Nella casella **di testo Percorso** di destinazione immettere un percorso locale e quindi scegliere il **pulsante** Pubblica.

     Lo stato di pubblicazione viene visualizzato nella Visual Studio **Output.** Al termine del processo, il file della soluzione ( con estensione *wsp*) viene installato nel server SharePoint locale. Tuttavia, deve comunque essere attivato per essere usato in SharePoint. Se il file della soluzione esiste già, si verifica un errore e viene chiesto se si vuole sovrascrivere il file esistente. Per informazioni sull'aggiornamento del pacchetto, vedere la sezione sull'aggiornamento dei pacchetti remoti in [Procedura: Distribuire,](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)pubblicare e aggiornare soluzioni SharePoint in un server remoto.

## <a name="see-also"></a>Vedi anche
- [Procedura: Distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [Creare SharePoint pacchetti della soluzione](../sharepoint/creating-sharepoint-solution-packages.md)
- [Procedura: Personalizzare un pacchetto SharePoint soluzione](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Procedura: Aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
