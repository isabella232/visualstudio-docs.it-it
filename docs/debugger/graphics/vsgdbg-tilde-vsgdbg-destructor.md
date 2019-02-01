---
title: 'VsgDbg:: ~ VsgDbg (distruttore) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 800a270ddb8e320bc7f7f712850cfd84200f00a9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983612"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (distruttore)
Elimina un'istanza di `VsgDbg` classe. Se viene registrate in modo attivo le informazioni grafiche, il file di log di grafica viene finalizzato e chiusa e vengono rilasciate le risorse che sono state usate durante l'acquisizione attivamente informazioni grafiche.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VsgDbg::VsgDbg (Costruttore)](vsgdbg-vsgdbg-constructor.md)