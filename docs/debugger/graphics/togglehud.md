---
title: ToggleHUD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a4ee371f90636d98d5dd771cc508e58cd1d1a394
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53907975"
---
# <a name="togglehud"></a>ToggleHUD
Attiva/Disattiva diagnostica della grafica *HUD* (Head-Up Display) sovrapporre attiva o disattiva.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Note  
 La diagnostica della grafica HUD viene visualizzata nell'angolo superiore sinistro dell'applicazione in esecuzione nella diagnostica della grafica. Visualizza le informazioni di runtime relativi all'app e sull'acquisizione delle informazioni grafiche e i messaggi aggiunti chiamando il [AddMessage](addmessage.md) funzione membro.  
  
 Per attivare o disattivare l'HUD, non è necessario acquisire attivamente informazioni grafiche, vale a dire, può essere modificato tramite un'istanza del `VsgDbg` (classe), ma la [Init](init.md) funzione membro non deve essere chiamato per primo.