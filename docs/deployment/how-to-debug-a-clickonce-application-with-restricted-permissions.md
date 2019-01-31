---
title: "Procedura: Eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ClickOnce applications
- ClickOnce deployment, debugging
- ClickOnce applications, debugging
ms.assetid: 6991ea91-5253-451b-923d-22273a3d38b1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 373fa21a0ec588768017bcbcd8b0fdc4587bf091
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976524"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Procedura: Eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate
Le applicazioni sul computer di sviluppo vengono in genere eseguite con autorizzazioni di attendibilità totale. È quindi molto probabile che le eccezioni di sicurezza generate durante il debug di un'applicazione ClickOnce siano diverse da quelle restituite all'utente finale quando esegue l'applicazione con autorizzazioni limitate.  
  
 Per rilevare queste eccezioni, è necessario eseguire il debug dell'applicazione con le stesse autorizzazioni dell'utente finale. Il debug con autorizzazioni limitate può essere abilitato nella pagina **Sicurezza** di **Creazione progetti**.  
  
 Inoltre, quando si sviluppano applicazioni che chiamano servizi Web, in genere questi ultimi si trovano sul computer di sviluppo. Dopo la distribuzione, l'utente finale accederà a questi servizi Web da un URL differente. Per simulare l'esperienza dell'utente finale durante il debug, è possibile specificare un URL in modo che il debugger consideri i servizi Web come se venissero chiamati da tale URL.  
  
### <a name="to-enable-debugging-with-restricted-permissions"></a>Per abilitare il debug con autorizzazioni limitate  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  In **Creazione progetti**fare clic sulla scheda **Sicurezza** .  
  
3.  Selezionare la casella di controllo **Abilita impostazioni di sicurezza ClickOnce** e quindi selezionare il pulsante di opzione **È un'applicazione con attendibilità parziale** .  
  
4.  Fare clic su **Avanzate** .  
  
5.  Selezionare la casella di controllo **Esegui debug dell'applicazione con il set di autorizzazioni selezionato** e quindi fare clic su **OK**.  
  
     Quando si esegue il debug dell'applicazione, un eventuale tentativo di accedere a un'autorizzazione che non fa parte del set di autorizzazioni genererà un'eccezione di sicurezza.  
  
### <a name="to-specify-a-url-for-debugging"></a>Per specificare un URL per il debug  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  In **Creazione progetti**fare clic sulla scheda **Sicurezza** .  
  
3.  Selezionare la casella di controllo **Abilita impostazioni di sicurezza ClickOnce** e quindi selezionare il pulsante di opzione **È un'applicazione con attendibilità parziale** .  
  
4.  Fare clic su **Avanzate** .  
  
5.  Selezionare la casella di controllo **Esegui debug dell'applicazione con il set di autorizzazioni selezionato** e quindi fare clic su **OK**.  
  
6.  Nella casella di testo **Esegui debug dell'applicazione come se fosse stata scaricata dal seguente URL** immettere un URL o un percorso di rete.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Impostare le autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)