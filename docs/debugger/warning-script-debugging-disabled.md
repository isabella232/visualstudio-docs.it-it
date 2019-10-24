---
title: 'Avviso: debug degli script disabilitato | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91875a370f6d072cf2dd69807f516b8f1a808461
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728206"
---
# <a name="warning-script-debugging-disabled"></a>Avviso: debug degli script disabilitato
Il debug degli script è attualmente disabilitato in Internet Explorer

 Questo avviso viene visualizzato quando si tenta di eseguire il debug dello script senza abilitare il debug degli script in Internet Explorer. Per motivi di sicurezza, il debug degli script è disabilitato in Internet Explorer per impostazione predefinita.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>Per abilitare il debug di script in Internet Explorer

1. Scegliere **Opzioni Internet** dal menu **Strumenti** di Internet Explorer.

2. Nella finestra di dialogo **Opzioni Internet** fare clic sulla scheda **Avanzate** .

3. Nella casella **Impostazioni** della scheda **Avanzate**, cercare la categoria **Esplorazione**.

4. Deselezionare **Disabilita debugging degli script (Internet Explorer)** .

5. Fare clic su **OK**.

6. Chiudere e riavviare Internet Explorer.

     Le nuove impostazioni risulteranno ora attive.

## <a name="see-also"></a>Vedere anche
- [Procedura: Connettersi a file script](../debugger/how-to-attach-to-script.md)