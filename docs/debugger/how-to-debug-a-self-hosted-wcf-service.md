---
title: Eseguire il debug Self-Hosted servizio WCF | Microsoft Docs
description: Informazioni su come eseguire il debug di un servizio WCF self-hosted. Il modo più semplice (ma non sempre possibile) è configurare Visual Studio per l'avvio sia del client che del server.
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
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 73933801ca158a4e348eba26f379383ecd793a22
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074124"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Procedura: eseguire il debug di un servizio WCF indipendente
Un *servizio indipendente* è un servizio WCF che non viene eseguito in IIS, nell'host dei servizi WCF o nel server di sviluppo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Il modo più semplice per eseguire il debug di un'istanza di WCF self-hosted è configurare per avviare sia il client che il server quando si sceglie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Avvia** debug dal menu **Debug.**

 Se il servizio WCF esegue il self-hosting all'interno di o un processo che non può essere avviato in questo modo, ad esempio il servizio NT, non è possibile utilizzare questo metodo. È invece possibile eseguire una delle operazioni seguenti:

- Collegare manualmente il debugger al processo di hosting. Per altre informazioni, vedere [Connettersi a processi in esecuzione.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

     - o -

- Avviare il debug del client e quindi eseguire una chiamata al servizio. A tale scopo è necessario abilitare il debug nel file app.config. Per altre informazioni, [vedere Limitazioni relative al debug di WCF.](../debugger/limitations-on-wcf-debugging.md)

### <a name="to-start-both-client-and-host-from-visual-studio"></a>Per avviare sia il client che l'host da Visual Studio

1. Creare una [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione contenente i progetti client e server.

2. Configurare la soluzione per avviare i processi client e server quando si sceglie **Avvia** dal menu **Debug.**

   1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nome della soluzione.

   2. Fare clic **su Imposta progetti di avvio**.

   3. Nella finestra **di \<name> dialogo Proprietà** soluzione selezionare Progetti di avvio **multipli.**

   4. Nella griglia **Progetti di avvio** multipli , nella riga corrispondente al progetto server, fare clic su **Azione** e scegliere **Avvia**.

   5. Nella riga che corrisponde al progetto client fare clic su **Azione e** scegliere **Avvia.**

   6. Fare clic su **OK**.

## <a name="see-also"></a>Vedi anche
- [Debug dei servizi WCF](../debugger/debugging-wcf-services.md)
- [Limitazioni relative al debug di WCF](../debugger/limitations-on-wcf-debugging.md)
- [Procedura: Eseguire un'istruzione nei servizi WCF](../debugger/how-to-step-into-wcf-services.md)
