---
description: Elimina un'istanza della classe VsgDbg.
title: VsgDbg::~VsgDbg (distruttore) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3a0331d0919a52ed91cf973a274a01220dc88f2a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627996"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (distruttore)
Elimina un'istanza della `VsgDbg` classe . Se le informazioni grafiche vengono registrate attivamente, il file di log della grafica viene finalizzato e chiuso e vengono rilasciate le risorse usate durante l'acquisizione attiva delle informazioni grafiche.

## <a name="syntax"></a>Sintassi

```C++
~VsgDbg();
```

## <a name="see-also"></a>Vedere anche
- [VsgDbg::VsgDbg (costruttore)](vsgdbg-vsgdbg-constructor.md)
