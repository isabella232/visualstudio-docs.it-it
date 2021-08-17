---
description: Quando presente, definisce se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente.
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e2413e38408405bc3b3677a2e8f691abca063676bec41e6a4bfa31cc93fdbce6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121436082"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Quando presente, definisce se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente.

## <a name="syntax"></a>Sintassi

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>Valore
 Simbolo del preprocessore che in base alla presenza o all'assenza determina se il file di log grafico viene salvato nella directory dei file temporanei dell'utente. Se questo simbolo è definito, il nome file definito da è relativo alla directory corrente dell'app acquisita o è un percorso assoluto. In caso contrario, il nome file definito da è relativo alla directory dei file temporanei dell'utente e non può essere un percorso `VSG_DEFAULT_RUN_FILENAME` `VSG_DEFAULT_RUN_FILENAME` assoluto.

## <a name="remarks"></a>Commenti
 A seconda dei privilegi dell'utente, il file di log della grafica potrebbe non essere salvato in un percorso arbitrario. È consigliabile salvare i log grafici nella directory dei file temporanei dell'utente o in un'altra posizione nota, se non si è certi che il percorso scelto possa essere scritto dall'utente.

 Per impedire il salvataggio del file di log grafico nella directory dei file temporanei, è necessario definire `DONT_SAVE_VSGLOG_TO_TEMP` prima di includere `vsgcapture.h` .

## <a name="example"></a>Esempio
 Questo esempio illustra come salvare il file di log grafico in un percorso assoluto nel computer host.

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h
#define DONT_SAVE_VSGLOG_TO_TEMP
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Vedi anche
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
