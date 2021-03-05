---
description: Elimina un'istanza della classe VsgDbg.
title: 'VsgDbg:: ~ VsgDbg (distruttore) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d90664723695756ebd8acdc7c56bec1fcbd08a31
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155226"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (distruttore)
Elimina un'istanza della `VsgDbg` classe. Se le informazioni grafiche vengono registrate attivamente, il file di log di grafica viene finalizzato e chiuso e le risorse utilizzate durante l'acquisizione attiva delle informazioni grafiche vengono rilasciate.

## <a name="syntax"></a>Sintassi

```C++
~VsgDbg();
```

## <a name="see-also"></a>Vedere anche
- [VsgDbg::VsgDbg (costruttore)](vsgdbg-vsgdbg-constructor.md)
