---
title: Disabilitare l'attivazione dell'URL ClickOnce app usando Progettazione
description: Informazioni su come disabilitare l'avvio automatico all'installazione per un'applicazione ClickOnce usando Visual Studio, in modo che gli utenti devono avviare l'applicazione dal menu Start.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: b86b9ecd4ada8396f603af2555de11efd7d3c51e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160660"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Procedura: Disabilitare gli URL di applicazioni ClickOnce tramite la finestra di progettazione
In genere, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione viene avviata automaticamente immediatamente dopo l'installazione da un server Web. Per motivi di sicurezza, è possibile decidere di disabilitare questo comportamento e indicare agli utenti di avviare l'applicazione dal menu **Start.** La procedura seguente descrive come disabilitare l’attivazione dell’URL.

 Questa tecnica può essere usata solo per le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installate nel computer dell'utente da un server Web. Non può essere usato per le applicazioni solo online, che possono essere avviate solo usando il relativo URL. Per altre informazioni sulla differenza tra applicazioni solo online e installate, vedere Scelta di una strategia [ClickOnce distribuzione.](../deployment/choosing-a-clickonce-deployment-strategy.md)

 In questa procedura viene utilizzato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . È anche possibile eseguire questa attività usando [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Per altre informazioni, vedere [Procedura: Disabilitare l'attivazione url ClickOnce applicazioni](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## <a name="procedure"></a>Procedura

#### <a name="to-disable-url-activation-for-your-application"></a>Per disabilitare l'attivazione dell'URL per l'applicazione

1. Fare clic con il pulsante destro del mouse **sul nome del progetto Esplora soluzioni** e scegliere **Proprietà.**

2. Nella pagina **Proprietà** fare clic sulla **scheda** Pubblica.

3. Fare clic su **Opzioni**.

4. Fare **clic su Manifesti**.

5. Selezionare la casella di controllo Blocca **l'attivazione dell'applicazione tramite un URL**.

6. Distribuire l'applicazione.

## <a name="see-also"></a>Vedi anche
- [Pubblicazione ClickOnce applicazioni](../deployment/publishing-clickonce-applications.md)