---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 449c6c1ecdb0644b9b52b6ec12ce867dc34d66c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156094"
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando presente, definisce se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>Value  
 Un simbolo del preprocessore che mediante il relativo presenza o assenza determina se un file di log di grafica viene salvato nella directory dei file temporanei dell'utente. Se questo simbolo è definito, quindi il nome di file definito da `VSG_DEFAULT_RUN_FILENAME` è relativo alla directory corrente dell'applicazione acquisita o è un percorso assoluto; in caso contrario, il nome di file definito da `VSG_DEFAULT_RUN_FILENAME` è relativo alla directory dei file temporanei dell'utente e non può essere un percorso assoluto.  
  
## <a name="remarks"></a>Note  
 A seconda dei privilegi dell'utente, il file di log di grafica potrà non essere in grado di essere salvata in un percorso arbitrario. È consigliabile che si vuole salvare i log di grafica in directory dei file temporanei dell'utente o un altro percorso noto, se non si è certi se è possibile scrivere un posizione che verrà scelta dall'utente.  
  
 Per evitare che il file di log di grafica viene salvato nella directory dei file temporanei, è necessario definito `DONT_SAVE_VSGLOG_TO_TEMP` prima di includere `vsgcapture.h`.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come salvare il file di log di grafica in un percorso assoluto nel computer host.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
