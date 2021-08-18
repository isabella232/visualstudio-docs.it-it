---
title: "Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo"
description: Informazioni su come usare le Visual Studio per visualizzare a livello di codice gli errori dell'interfaccia utente del componente aggiuntivo VTSO Microsoft Office applicazioni.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ef5a8780e56da76476038605cfad957cfcd8ba0e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099620"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo
  Per impostazione predefinita, se un componente VSTO prova a modificare l'interfaccia utente di Microsoft Office e non riesce, non viene visualizzato alcun messaggio di errore. È però possibile configurare le applicazioni di Microsoft Office in modo da visualizzare messaggi per gli errori correlati all'interfaccia utente. È possibile usare questi messaggi per determinare perché una barra multifunzione personalizzata non viene visualizzata o perché viene visualizzata una barra multifunzione ma non viene visualizzato alcun controllo.

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
- [Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)
- [Creare aree Outlook modulo](../vsto/creating-outlook-form-regions.md)
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md)
