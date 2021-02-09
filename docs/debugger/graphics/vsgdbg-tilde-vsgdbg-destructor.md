---
title: 'VsgDbg:: ~ VsgDbg (distruttore) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 53d969e6be772b446598c9c3644582684be488a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861348"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (distruttore)
Elimina un'istanza della `VsgDbg` classe. Se le informazioni grafiche vengono registrate attivamente, il file di log di grafica viene finalizzato e chiuso e le risorse utilizzate durante l'acquisizione attiva delle informazioni grafiche vengono rilasciate.

## <a name="syntax"></a>Sintassi

```C++
~VsgDbg();
```

## <a name="see-also"></a>Vedere anche
- [VsgDbg::VsgDbg (costruttore)](vsgdbg-vsgdbg-constructor.md)