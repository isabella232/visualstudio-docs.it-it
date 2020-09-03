---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40f3c3c22de6b4b0ebdbdf2dfc953f4cb1c9b5e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72736084"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Quando presente, definisce se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente.

## <a name="syntax"></a>Sintassi

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>Valore
 Simbolo del preprocessore che, per sua presenza o assenza, determina se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente. Se questo simbolo è definito, il nome file definito da `VSG_DEFAULT_RUN_FILENAME` è relativo alla directory corrente dell'app acquisita oppure è un percorso assoluto. in caso contrario, il nome file definito da `VSG_DEFAULT_RUN_FILENAME` è relativo alla directory dei file temporanei dell'utente e non può essere un percorso assoluto.

## <a name="remarks"></a>Osservazioni
 A seconda dei privilegi dell'utente, il file di log di grafica potrebbe non essere in grado di essere salvato in un percorso arbitrario. Si consiglia di salvare i log di grafica nella directory dei file temporanei dell'utente o in un altro percorso noto, se non si è certi che la posizione scelta possa essere scritta dall'utente.

 Per evitare che il file di log di grafica venga salvato nella directory dei file temporanei, è necessario definire `DONT_SAVE_VSGLOG_TO_TEMP` prima di includere `vsgcapture.h` .

## <a name="example"></a>Esempio
 Questo esempio illustra come salvare il file di log di grafica in un percorso assoluto nel computer host.

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h
#define DONT_SAVE_VSGLOG_TO_TEMP
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Vedere anche
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
