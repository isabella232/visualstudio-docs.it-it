---
title: ToggleHUD | Microsoft Docs
description: Usare il metodo ToggleHUD () di VsgDbg per impostare il modo in cui viene visualizzata la schermata iniziale di diagnostica della grafica (HUD) quando viene eseguita l'app.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60bee5a89be0fc1503595a36cfc48a692711d40a
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996071"
---
# <a name="togglehud"></a>ToggleHUD
Attiva o disattiva la sovrimpressione di diagnostica della grafica *HUD* (Head-up display).

## <a name="syntax"></a>Sintassi

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Osservazioni
 La diagnostica della grafica HUD viene visualizzata nell'angolo superiore sinistro dell'applicazione in esecuzione nella diagnostica della grafica. Vengono visualizzate informazioni di run-time sull'app e sull'acquisizione di informazioni grafiche e messaggi aggiunti chiamando la funzione membro [AddMessage](addmessage.md) .

 Per impostare l'HUD, non è necessario acquisire attivamente le informazioni grafiche, ovvero può essere attivata o disattivata tramite un'istanza della `VsgDbg` classe, ma non è necessario chiamare prima la funzione membro [init](init.md) .