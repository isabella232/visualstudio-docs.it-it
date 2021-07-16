---
title: ToggleHUD | Microsoft Docs
description: Usare il metodo ToggleHUD() di VsgDbg per attivare o disattivare la visualizzazione head-Up display (HUD) della diagnostica grafica durante l'esecuzione dell'app.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 809b33fe3339da56507d09fcf15ec51481b751e0
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232492"
---
# <a name="togglehud"></a>ToggleHUD
Attiva o disattiva la *sovrimpressione HUD* (Head-Up Display) di diagnostica della grafica.

## <a name="syntax"></a>Sintassi

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Osservazioni
 La diagnostica della grafica HUD viene visualizzata nell'angolo superiore sinistro dell'applicazione in esecuzione nella diagnostica della grafica. Visualizza informazioni di run-time sull'app e sull'acquisizione di informazioni grafiche e i messaggi aggiunti chiamando la funzione membro [AddMessage.](addmessage.md)

 Per attivare o disattivare l'hud, non è necessario acquisire attivamente informazioni grafiche, ovvero è possibile attivarla tramite un'istanza della classe, ma non è necessario chiamare prima la funzione membro `VsgDbg` [Init.](init.md)