---
title: 'Avviso: debug degli script disabilitato | Microsoft Docs'
description: Quando si tenta di eseguire il debug dello script senza abilitare il debug degli script in Internet Explorer, viene visualizzato un avviso "Debug script disabilitato". Vedere la procedura per abilitarla.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d23d6eaf21375095c04284981b9178a02decec96
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090148"
---
# <a name="warning-script-debugging-disabled"></a>Avviso: debug degli script disabilitato
Il debug degli script è attualmente disabilitato in Internet Explorer

 Questo avviso viene visualizzato quando si tenta di eseguire il debug dello script senza abilitare il debug degli script in Internet Explorer. Per motivi di sicurezza, il debug degli script è disabilitato in Internet Explorer per impostazione predefinita.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>Per abilitare il debug di script in Internet Explorer

1. Scegliere **Opzioni Internet** dal menu **Strumenti** di Internet Explorer.

2. Nella finestra di dialogo **Opzioni Internet** fare clic sulla scheda **Avanzate** .

3. Nella casella **Impostazioni** della scheda **Avanzate**, cercare la categoria **Esplorazione**.

4. Deselezionare **Disabilita debugging degli script (Internet Explorer)**.

5. Fare clic su **OK**.

6. Chiudere e riavviare Internet Explorer.

     Le nuove impostazioni risulteranno ora attive.

## <a name="see-also"></a>Vedi anche
- [Procedura: Connettersi a uno script](attach-to-running-processes-with-the-visual-studio-debugger.md)