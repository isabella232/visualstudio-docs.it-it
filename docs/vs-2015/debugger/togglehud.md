---
title: ToggleHUD | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02b461ac8d80146bc86bf3636a367900fcdb8f39
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786938"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Attiva/Disattiva diagnostica della grafica *HUD* (Head-Up Display) sovrapporre attiva o disattiva.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Note  
 La diagnostica della grafica HUD viene visualizzata nell'angolo superiore sinistro dell'applicazione in esecuzione nella diagnostica della grafica. Visualizza le informazioni di runtime relativi all'app e sull'acquisizione delle informazioni grafiche e i messaggi aggiunti chiamando il [AddMessage](../debugger/addmessage.md) funzione membro.  
  
 Per attivare o disattivare l'HUD, non è necessario acquisire attivamente informazioni grafiche, vale a dire, può essere modificato tramite un'istanza del `VsgDbg` (classe), ma la [Init](../debugger/init.md) funzione membro non deve essere chiamato per primo.



