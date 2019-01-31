---
title: EndCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8f72e3bcd3755fe59af5207586cf9cf03d432f4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967625"
---
# <a name="endcapture"></a>EndCapture
Termina un intervallo di acquisizione avviato con `BeginCapture`.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
void EndCapture();  
```  
  
## <a name="remarks"></a>Note  
 Un intervallo di acquisizione in genere estende un subset di un singolo frame, come ad esempio quando si desidera acquisire informazioni grafiche solo su un determinato tipo di chiamata di disegno. Se l'intervallo di acquisizione estende una chiamata da presentare, vengono acquisiti due frame di informazioni grafiche. Il primo frame estende l'intervallo tra la chiamata a `BeginCapture` e la chiamata da presentare; il secondo frame estende l'intervallo tra il primo evento Direct3D dopo la chiamata da presentare e la chiamata a `EndCapture`.  
  
 Per acquisire un intervallo, è necessario preparare l'applicazione per acquisire e registrare le informazioni grafiche, vale a dire, è necessario avere chiamato [Init](init.md) tramite un'istanza di `VsgDbg` classe prima di chiamare `BeginCapture` o `EndCapture`.  
  
## <a name="see-also"></a>Vedere anche  
 [BeginCapture](begincapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)