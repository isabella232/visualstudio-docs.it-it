---
title: Disabilitare l'attivazione dell'URL delle app ClickOnce usando progettazione
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 818ab634d48fb666ecab5d89464ea017040bd250
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382484"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Procedura: Disabilitare gli URL di applicazioni ClickOnce tramite la finestra di progettazione
In genere, un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione verrà avviata automaticamente immediatamente dopo l'installazione da un server Web. Per motivi di sicurezza, è possibile decidere di disabilitare questo comportamento e indicare agli utenti di avviare l'applicazione dal menu **Start** . La procedura seguente descrive come disabilitare l’attivazione dell’URL.

 Questa tecnica può essere usata solo per le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installate nel computer dell'utente da un server Web. Non può essere usato per le applicazioni solo online, che possono essere avviate solo tramite l'URL. Per ulteriori informazioni sulla differenza tra le applicazioni solo online e installate, vedere [scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

 Questa procedura utilizza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . È anche possibile eseguire questa attività usando [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Per altre informazioni, vedere [procedura: disabilitare l'attivazione dell'URL delle applicazioni ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## <a name="procedure"></a>Procedura

#### <a name="to-disable-url-activation-for-your-application"></a>Per disabilitare l'attivazione dell'URL per l'applicazione

1. Fare clic con il pulsante destro del mouse sul nome del progetto in **Esplora soluzioni**, quindi scegliere **Proprietà**.

2. Nella pagina **Proprietà** fare clic sulla scheda **pubblica** .

3. Fare clic su **Opzioni**.

4. Fare clic su **manifesti**.

5. Selezionare la casella **di controllo Blocca applicazione dall'attivazione tramite un URL**.

6. Distribuire l'applicazione.

## <a name="see-also"></a>Vedere anche
- [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)