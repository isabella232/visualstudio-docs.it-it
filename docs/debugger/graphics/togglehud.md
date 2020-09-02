---
title: ToggleHUD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb05bb6a424b5639e0ee98e96c80315c51081ace
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62848472"
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