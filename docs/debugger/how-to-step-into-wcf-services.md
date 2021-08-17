---
title: Eseguire un'istruzione in Wcf Services | Microsoft Docs
description: Eseguire un'istruzione in Windows communication foundation (WCF). Se si trova nella stessa soluzione Visual Studio client, premere punti di interruzione all'interno del servizio WCF.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a73d6438547138c016533562a0b7ae71f894967b3d5da08c9d2408fdc0029bb6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453449"
---
# <a name="how-to-step-into-wcf-services"></a>Procedura: eseguire istruzioni nei servizi WCF
In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], è possibile eseguire istruzioni in un servizio WCF. Se il servizio WCF si trova nella stessa soluzione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] del client, è possibile raggiungere punti di interruzione nel servizio WCF.

 Per consentire il funzionamento, è necessario avere attivato il debug nel file app.config o web.config. Per informazioni su come abilitare il debug e sulle limitazioni relative all'esecuzione di istruzioni nei servizi WCF, vedere [Limitazioni del debug WCF.](../debugger/limitations-on-wcf-debugging.md)

### <a name="to-step-into-a-wcf-service"></a>Per eseguire istruzioni in un servizio WCF

1. Creare una soluzione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] contenente entrambi i progetti client WCF e servizio WCF.

2. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto Client WCF e scegliere **Imposta come progetto di avvio**.

3. Attivare il debug nel file app.config o web.config. Per altre informazioni, vedere [Limitazioni del debug WCF.](../debugger/limitations-on-wcf-debugging.md)

4. Impostare un punto di interruzione nel percorso all'interno del progetto client in cui si desidera iniziare a eseguire le istruzioni. In genere, si troverà poco prima della chiamata del servizio WCF.

5. Eseguire il debug nel punto d'interruzione, quindi iniziare a eseguire le istruzioni. Il debugger eseguirà automaticamente le istruzioni nel servizio.

## <a name="see-also"></a>Vedi anche
- [Debug dei servizi WCF](../debugger/debugging-wcf-services.md)
- [Limitazioni del debug WCF](../debugger/limitations-on-wcf-debugging.md)
- [Procedura: Eseguire il debug di un Self-Hosted WCF](../debugger/how-to-debug-a-self-hosted-wcf-service.md)