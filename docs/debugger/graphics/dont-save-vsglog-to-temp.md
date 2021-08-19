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
ms.openlocfilehash: 44ffbba52a09c5d2874e51014cec9e1b755c5f32
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154252"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Quando presente, definisce se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente.

## <a name="syntax"></a>Sintassi

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>Valore
 Simbolo del preprocessore che in base alla sua presenza o assenza determina se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente. Se questo simbolo è definito, il nome file definito da è relativo alla directory corrente dell'app acquisita o è un percorso assoluto. In caso contrario, il nome file definito da è relativo alla directory dei file temporanei dell'utente e non può essere un percorso `VSG_DEFAULT_RUN_FILENAME` `VSG_DEFAULT_RUN_FILENAME` assoluto.

## <a name="remarks"></a>Commenti
 A seconda dei privilegi dell'utente, il file di log di grafica potrebbe non essere salvato in un percorso arbitrario. È consigliabile salvare i log di grafica nella directory dei file temporanei dell'utente o in un'altra posizione nota, se non si è certi che il percorso scelto possa essere scritto dall'utente.

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
