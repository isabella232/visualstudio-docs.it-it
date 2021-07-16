---
description: Elimina un'istanza della classe VsgDbg.
title: VsgDbg::~VsgDbg (distruttore) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ddc942d2ef3a33f1f8d843ff5657f76bb58104c4
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232388"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (distruttore)
Elimina un'istanza della `VsgDbg` classe . Se le informazioni grafiche vengono registrate attivamente, il file di log della grafica viene finalizzato e chiuso e vengono rilasciate le risorse usate durante l'acquisizione attiva delle informazioni grafiche.

## <a name="syntax"></a>Sintassi

```C++
~VsgDbg();
```

## <a name="see-also"></a>Vedere anche
- [VsgDbg::VsgDbg (costruttore)](vsgdbg-vsgdbg-constructor.md)
