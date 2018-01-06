---
title: 'Procedura: visualizzare gli errori dell''interfaccia utente del componente aggiuntivo | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
ms.assetid: aa82cc04-e616-4501-940c-79d11fb393cc
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 35247fed0577d410db86b6d3bd436586784f240a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo
  Per impostazione predefinita, se un componente aggiuntivo VSTO tenta di modificare l'interfaccia utente di Microsoft Office e non riesce, non viene visualizzato alcun messaggio di errore. È però possibile configurare le applicazioni di Microsoft Office in modo da visualizzare messaggi per gli errori correlati all'interfaccia utente. Questi messaggi possono essere usati per stabilire perché non viene visualizzata una barra multifunzione personalizzata o perché viene visualizzata una barra multifunzione ma senza controlli.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-show-vsto-add-in-user-interface-errors"></a>Per visualizzare gli errori dell'interfaccia utente dei componenti aggiuntivi VSTO  
  
1.  Avviare l'applicazione.  
  
2.  Scegliere la scheda **File** .  
  
3.  Fare clic su **Opzioni**.  
  
4.  Nel riquadro delle categorie fare clic su **Avanzate**.  
  
5.  Nel riquadro dei dettagli selezionare **Mostra errori dell'interfaccia utente dei componenti aggiuntivi**, quindi fare clic su **OK**.  
  
    > [!NOTE]  
    >  Per Outlook, la casella di controllo **Mostra errori dell'interfaccia utente dei componenti aggiuntivi** si trova nella sezione **Sviluppo** del riquadro dei dettagli. Per altre applicazioni, la casella di controllo si trova nella sezione **Generale** del riquadro dei dettagli.  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md)  
  
  