---
description: Quando presente, definisce se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente.
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 06152c79859a34e604ffc4e5227e2dd11ebbeaca
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146197"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Quando presente, definisce se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente.

## <a name="syntax"></a>Sintassi

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>Valore
 Simbolo del preprocessore che, per sua presenza o assenza, determina se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente. Se questo simbolo è definito, il nome file definito da `VSG_DEFAULT_RUN_FILENAME` è relativo alla directory corrente dell'app acquisita oppure è un percorso assoluto. in caso contrario, il nome file definito da `VSG_DEFAULT_RUN_FILENAME` è relativo alla directory dei file temporanei dell'utente e non può essere un percorso assoluto.

## <a name="remarks"></a>Commenti
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

## <a name="see-also"></a>Vedi anche
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
