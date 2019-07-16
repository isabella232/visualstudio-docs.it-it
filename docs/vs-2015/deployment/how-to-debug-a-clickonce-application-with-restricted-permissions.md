---
title: "Procedura: Eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d60f88c4d1532a03922f12f21bb9b455ef5d84d8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153791"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Procedura: Eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le applicazioni sul computer di sviluppo vengono in genere eseguite con autorizzazioni di attendibilità totale. È quindi molto probabile che le eccezioni di sicurezza generate durante il debug di un'applicazione ClickOnce siano diverse da quelle restituite all'utente finale quando esegue l'applicazione con autorizzazioni limitate.  
  
 Per rilevare queste eccezioni, è necessario eseguire il debug dell'applicazione con le stesse autorizzazioni dell'utente finale. Il debug con autorizzazioni limitate può essere abilitato nella pagina **Sicurezza** di **Creazione progetti**.  
  
 Inoltre, quando si sviluppano applicazioni che chiamano servizi Web, in genere questi ultimi si trovano sul computer di sviluppo. Dopo la distribuzione, l'utente finale accederà a questi servizi Web da un URL differente. Per simulare l'esperienza dell'utente finale durante il debug, è possibile specificare un URL in modo che il debugger consideri i servizi Web come se venissero chiamati da tale URL.  
  
### <a name="to-enable-debugging-with-restricted-permissions"></a>Per abilitare il debug con autorizzazioni limitate  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. In **Creazione progetti**fare clic sulla scheda **Sicurezza** .  
  
3. Selezionare la casella di controllo **Abilita impostazioni di sicurezza ClickOnce** e quindi selezionare il pulsante di opzione **È un'applicazione con attendibilità parziale** .  
  
4. Fare clic su **Avanzate** .  
  
5. Selezionare la casella di controllo **Esegui debug dell'applicazione con il set di autorizzazioni selezionato** e quindi fare clic su **OK**.  
  
     Quando si esegue il debug dell'applicazione, un eventuale tentativo di accedere a un'autorizzazione che non fa parte del set di autorizzazioni genererà un'eccezione di sicurezza.  
  
### <a name="to-specify-a-url-for-debugging"></a>Per specificare un URL per il debug  
  
1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2. In **Creazione progetti**fare clic sulla scheda **Sicurezza** .  
  
3. Selezionare la casella di controllo **Abilita impostazioni di sicurezza ClickOnce** e quindi selezionare il pulsante di opzione **È un'applicazione con attendibilità parziale** .  
  
4. Fare clic su **Avanzate** .  
  
5. Selezionare la casella di controllo **Esegui debug dell'applicazione con il set di autorizzazioni selezionato** e quindi fare clic su **OK**.  
  
6. Nella casella di testo **Esegui debug dell'applicazione come se fosse stata scaricata dal seguente URL** immettere un URL o un percorso di rete.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Impostare autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sicurezza di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
