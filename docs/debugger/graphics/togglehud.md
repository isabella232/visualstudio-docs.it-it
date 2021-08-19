---
title: ToggleHUD | Microsoft Docs
description: Usare il metodo ToggleHUD() di VsgDbg per attivare o disattivare la visualizzazione della visualizzazione head-up (HUD) della diagnostica grafica quando viene eseguita l'app.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 15c232c89bf7f0a502bd98127498bc8047d01fda
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044028"
---
# <a name="togglehud"></a>ToggleHUD
Attiva o disattiva la sovrapposizione *HUD* (Head-Up Display) di diagnostica grafica.

## <a name="syntax"></a>Sintassi

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Osservazioni
 La diagnostica della grafica HUD viene visualizzata nell'angolo superiore sinistro dell'applicazione in esecuzione nella diagnostica della grafica. Visualizza informazioni di run-time sull'app e sull'acquisizione di informazioni grafiche e i messaggi aggiunti chiamando la funzione membro [AddMessage.](addmessage.md)

 Per attivare o disattivare l'HUD, non è necessario acquisire attivamente le informazioni grafiche, ovvero è possibile attivarla tramite un'istanza della classe, ma non è necessario chiamare prima la funzione membro `VsgDbg` [Init.](init.md)