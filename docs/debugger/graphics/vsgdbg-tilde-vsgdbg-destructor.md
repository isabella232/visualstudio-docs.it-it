---
title: 'VsgDbg:: ~ VsgDbg (distruttore) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d68b7dbf64f15b376cd49bdd2d60f507014f5167
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877861"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (distruttore)
Elimina un'istanza di `VsgDbg` classe. Se viene registrate in modo attivo le informazioni grafiche, il file di log di grafica viene finalizzato e chiusa e vengono rilasciate le risorse che sono state usate durante l'acquisizione attivamente informazioni grafiche.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VsgDbg::VsgDbg (Costruttore)](vsgdbg-vsgdbg-constructor.md)