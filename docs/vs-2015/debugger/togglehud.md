---
title: ToggleHUD | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b224fdbd4dfadc6af29a0491bba5a18089c260b4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520146"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [ToggleHUD](https://docs.microsoft.com/visualstudio/debugger/graphics/togglehud).  
  
Attiva/Disattiva diagnostica della grafica *HUD* (Head-Up Display) sovrapporre attiva o disattiva.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Note  
 La diagnostica della grafica HUD viene visualizzata nell'angolo superiore sinistro dell'applicazione in esecuzione nella diagnostica della grafica. Visualizza le informazioni di runtime relativi all'app e sull'acquisizione delle informazioni grafiche e i messaggi aggiunti chiamando il [AddMessage](../debugger/addmessage.md) funzione membro.  
  
 Per attivare o disattivare l'HUD, non è necessario acquisire attivamente informazioni grafiche, vale a dire, può essere modificato tramite un'istanza del `VsgDbg` (classe), ma la [Init](../debugger/init.md) funzione membro non deve essere chiamato per primo.



