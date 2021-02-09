---
title: Eseguire un'istruzione nei servizi WCF | Microsoft Docs
description: Eseguire un'istruzione in un servizio Windows Communication Foundation (WCF). Se si trova nella stessa soluzione di Visual Studio del client, fare clic su punti di interruzione all'interno del servizio WCF.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5f3a884698586cdd9a89ff62a090f02af3953a91
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896643"
---
# <a name="how-to-step-into-wcf-services"></a>Procedura: eseguire istruzioni nei servizi WCF
In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], è possibile eseguire istruzioni in un servizio WCF. Se il servizio WCF si trova nella stessa soluzione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] del client, è possibile raggiungere punti di interruzione nel servizio WCF.

 Per consentire il funzionamento, è necessario avere attivato il debug nel file app.config o web.config. Per informazioni sull'abilitazione del debug e sulle limitazioni relative all'esecuzione di un'istruzione nei servizi WCF, vedere [limitazioni del debug di WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-step-into-a-wcf-service"></a>Per eseguire istruzioni in un servizio WCF

1. Creare una soluzione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] contenente entrambi i progetti client WCF e servizio WCF.

2. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto Client WCF e scegliere **Imposta come progetto di avvio**.

3. Attivare il debug nel file app.config o web.config. Per ulteriori informazioni, vedere [limitazioni del debug di WCF](../debugger/limitations-on-wcf-debugging.md).

4. Impostare un punto di interruzione nel percorso all'interno del progetto client in cui si desidera iniziare a eseguire le istruzioni. In genere, si troverà poco prima della chiamata del servizio WCF.

5. Eseguire il debug nel punto d'interruzione, quindi iniziare a eseguire le istruzioni. Il debugger eseguirà automaticamente le istruzioni nel servizio.

## <a name="see-also"></a>Vedi anche
- [Debug dei servizi WCF](../debugger/debugging-wcf-services.md)
- [Limitazioni del debug WCF](../debugger/limitations-on-wcf-debugging.md)
- [Procedura: eseguire il debug di un servizio WCF Self-Hosted](../debugger/how-to-debug-a-self-hosted-wcf-service.md)