---
title: "Procedura: Disabilitare l'attivazione dell'URL di applicazioni ClickOnce | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6841b8a91cec24f467f6e3f684cbb27e25c9fa63
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899349"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Procedura: Disabilitare l'attivazione dell'URL delle applicazioni ClickOnce

In genere, un’applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] viene avviata automaticamente subito dopo l'installazione da un server Web. Per motivi legati alla sicurezza, è possibile disabilitare questo comportamento e invece indicare agli utenti di avviare l'applicazione dal menu **Start**. La procedura seguente descrive come disabilitare l’attivazione dell’URL.

Questa tecnica può essere usata solo per le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installate nel computer dell'utente da un server Web. Non può essere usata per le applicazioni solo online, che possono essere avviate solo mediante l'URL. Per altre informazioni sulla differenza tra le applicazioni solo online e installate, vedere [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

Questa procedura Usa lo strumento Windows Software Development Kit (SDK) MageUI.exe. Per altre informazioni su questo strumento, vedere [MageUI.exe (Strumento per la generazione e la modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). È anche possibile eseguire questa procedura usando Visual Studio.

## <a name="procedure"></a>Routine

### <a name="to-disable-url-activation-for-your-application"></a>Per disabilitare l'attivazione dell'URL per l'applicazione

1. Aprire il manifesto della distribuzione in MageUI.exe. Se non ancora stato creato uno, seguire i passaggi in [procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2. Selezionare la scheda **Opzioni di distribuzione**.

3. Deselezionare la casella di controllo **Esegui automaticamente l'applicazione dopo l'installazione**.

4. Salvare e firmare il manifesto.

## <a name="see-also"></a>Vedere anche

- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)