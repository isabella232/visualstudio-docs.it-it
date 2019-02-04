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
ms.openlocfilehash: 967ff50991efbbd7b598605abd992b298367d01c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006177"
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Quando presente, definisce se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente.  

## <a name="syntax"></a>Sintassi  

```C++  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  

## <a name="value"></a>Value  
 Un simbolo del preprocessore che mediante il relativo presenza o assenza determina se un file di log di grafica viene salvato nella directory dei file temporanei dell'utente. Se questo simbolo è definito, quindi il nome di file definito da `VSG_DEFAULT_RUN_FILENAME` è relativo alla directory corrente dell'applicazione acquisita o è un percorso assoluto; in caso contrario, il nome di file definito da `VSG_DEFAULT_RUN_FILENAME` è relativo alla directory dei file temporanei dell'utente e non può essere un percorso assoluto.  

## <a name="remarks"></a>Note  
 A seconda dei privilegi dell'utente, il file di log di grafica potrà non essere in grado di essere salvata in un percorso arbitrario. È consigliabile che si vuole salvare i log di grafica in directory dei file temporanei dell'utente o un altro percorso noto, se non si è certi se è possibile scrivere un posizione che verrà scelta dall'utente.  

 Per evitare che il file di log di grafica viene salvato nella directory dei file temporanei, è necessario definito `DONT_SAVE_VSGLOG_TO_TEMP` prima di includere `vsgcapture.h`.  

## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come salvare il file di log di grafica in un percorso assoluto nel computer host.  

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  

#include <vsgcapture.h>  
```  

## <a name="see-also"></a>Vedere anche  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
