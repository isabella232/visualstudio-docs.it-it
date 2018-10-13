---
title: 'Procedura: abilitare le impostazioni di sicurezza ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 73f4e16dc0d088ca617b49ee1250f51c4ae769e2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226027"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Procedura: abilitare le impostazioni di sicurezza ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sicurezza dall'accesso di codice per applicazioni ClickOnce deve essere abilitata per poter pubblicare l'applicazione. Ciò avviene automaticamente quando si pubblica un'applicazione usando la pubblicazione guidata.  
  
 In alcuni casi, l'abilitazione di sicurezza dall'accesso di codice può influire sulle prestazioni quando si compila o il debug dell'applicazione. In questi casi, si desidera disabilitare temporaneamente le impostazioni di sicurezza.  
  
 Impostazioni di sicurezza ClickOnce possono essere abilitate o disabilitate sul **sicurezza** pagina della **creazione progetti**.  
  
### <a name="to-enable-clickonce-security-settings"></a>Per abilitare le impostazioni di sicurezza ClickOnce  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Sicurezza** .  
  
3.  Selezionare la casella di controllo **Abilita impostazioni di sicurezza ClickOnce** .  
  
     È ora possibile personalizzare le impostazioni di sicurezza per l'applicazione nella pagina sicurezza.  
  
    > [!NOTE]
    >  Questa casella di controllo è selezionata automaticamente ogni volta che l'applicazione viene pubblicata con il **pubblica** procedura guidata.  
  
### <a name="to-disable-clickonce-security-settings"></a>Per disabilitare le impostazioni di sicurezza ClickOnce  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Sicurezza** .  
  
3.  Cancella il **Enable ClickOnce Security Settings** casella di controllo.  
  
     L'applicazione verrà eseguita con le impostazioni di sicurezza con attendibilità totale; tutte le impostazioni sul **sicurezza** pagina verrà ignorata.  
  
    > [!NOTE]
    >  Ogni volta che l'applicazione viene pubblicata con la pubblicazione guidata, verrà selezionata questa casella di controllo; è necessario cancellarlo nuovo termine di ogni pubblicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sicurezza di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)



