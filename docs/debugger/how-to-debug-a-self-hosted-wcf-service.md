---
title: 'Procedura: eseguire il debug di un servizio WCF self-hosted | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12654a6aa1abb34c9813e8d29c7608814021a3f0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733973"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Procedura: eseguire il debug di un servizio WCF indipendente
Un *servizio indipendente* è un servizio WCF che non viene eseguito in IIS, nell'host dei servizi WCF o nel server di sviluppo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Il modo più semplice per eseguire il debug di una WCF self-hosted consiste nel configurare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per avviare sia client che server quando si sceglie **Avvia debug** dal menu **debug** .

 Se il servizio WCF è self-hosting all'interno o un processo che non può essere avviato in questo modo, ad esempio NT Service, non è possibile usare questo metodo. In alternativa, è possibile eseguire una delle operazioni seguenti:

- Connetti manualmente il debugger al processo di hosting. Per ulteriori informazioni, vedere [Connetti a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

     oppure

- Avviare il debug del client e quindi eseguire un'istruzione in una chiamata al servizio. A tale scopo, è necessario abilitare il debug nel file app. config. Per ulteriori informazioni, [limitazioni sul debug WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-start-both-client-and-host-from-visual-studio"></a>Per avviare sia il client che l'host da Visual Studio

1. Creare una soluzione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] contenente i progetti client e server.

2. Configurare la soluzione per avviare i processi client e server quando si sceglie **Avvia** dal menu **debug** .

   1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nome della soluzione.

   2. Fare clic su **Imposta progetti di avvio**.

   3. Nella finestra di dialogo **Proprietà \<nome> soluzione** selezionare **Progetti di avvio multipli**.

   4. Nella griglia **progetti di avvio multipli** , nella riga che corrisponde al progetto server, fare clic su **azione** e scegliere **Avvia**.

   5. Nella riga che corrisponde al progetto client fare clic su **azione** e scegliere **Avvia**.

   6. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
- [Debug dei servizi WCF](../debugger/debugging-wcf-services.md)
- [Limitazioni del debug di WCF](../debugger/limitations-on-wcf-debugging.md)
- [Procedura: Eseguire istruzioni nei servizi WCF](../debugger/how-to-step-into-wcf-services.md)