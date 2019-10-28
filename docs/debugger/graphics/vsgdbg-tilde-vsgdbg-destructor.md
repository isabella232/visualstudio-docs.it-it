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
ms.openlocfilehash: dcc518e649732f6774259efed0965a9898e0fb2d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734788"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (distruttore)
Elimina un'istanza della classe `VsgDbg`. Se le informazioni grafiche vengono registrate attivamente, il file di log di grafica viene finalizzato e chiuso e le risorse utilizzate durante l'acquisizione attiva delle informazioni grafiche vengono rilasciate.

## <a name="syntax"></a>Sintassi

```C++
~VsgDbg();
```

## <a name="see-also"></a>Vedere anche
- [VsgDbg::VsgDbg (Costruttore)](vsgdbg-vsgdbg-constructor.md)