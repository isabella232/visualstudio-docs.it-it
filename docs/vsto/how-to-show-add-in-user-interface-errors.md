---
title: "Procedura: visualizzare gli errori dell'interfaccia utente del componente aggiuntivo"
description: Informazioni su come usare Visual Studio per visualizzare a livello di codice gli errori dell'interfaccia utente del componente aggiuntivo VTSO nelle applicazioni Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29e07e49d901b44b534d9d274e5535be663e97ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927678"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Procedura: visualizzare gli errori dell'interfaccia utente del componente aggiuntivo
  Per impostazione predefinita, se un componente aggiuntivo VSTO tenta di modificare l'interfaccia utente di Microsoft Office e non riesce, non viene visualizzato alcun messaggio di errore. È però possibile configurare le applicazioni di Microsoft Office in modo da visualizzare messaggi per gli errori correlati all'interfaccia utente. È possibile utilizzare questi messaggi per determinare il motivo per cui non viene visualizzata una barra multifunzione personalizzata o perché viene visualizzata una barra multifunzione, ma non viene visualizzato alcun controllo.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>Per visualizzare gli errori dell'interfaccia utente dei componenti aggiuntivi VSTO

1. Avviare l’applicazione.

2. Scegliere la scheda **File** .

3. Fare clic su **Opzioni**.

4. Nel riquadro delle categorie fare clic su **Avanzate**.

5. Nel riquadro dei dettagli selezionare **Mostra errori dell'interfaccia utente dei componenti aggiuntivi**, quindi fare clic su **OK**.

    > [!NOTE]
    > Per Outlook, la casella di controllo **Mostra errori dell'interfaccia utente dei componenti aggiuntivi** si trova nella sezione **Sviluppo** del riquadro dei dettagli. Per altre applicazioni, la casella di controllo si trova nella sezione **Generale** del riquadro dei dettagli.

## <a name="see-also"></a>Vedi anche
- [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)
- [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)
