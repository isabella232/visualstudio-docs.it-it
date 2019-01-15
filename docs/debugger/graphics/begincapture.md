---
title: BeginCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2fc3dd2d2851df56d3638333a78f4852ad86bef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823814"
---
# <a name="begincapture"></a>BeginCapture
Inizia un intervallo di acquisizione che termina con `EndCapture`.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
void BeginCapture();  
```  
  
## <a name="remarks"></a>Note  
 Un intervallo di acquisizione in genere estende un subset di un singolo frame, come ad esempio quando si desidera acquisire informazioni grafiche solo su un determinato tipo di chiamata di disegno. Se l'intervallo di acquisizione estende una chiamata da presentare, vengono acquisiti due frame di informazioni grafiche. Il primo frame estende l'intervallo tra la chiamata a `BeginCapture` e la chiamata da presentare; il secondo frame estende l'intervallo tra il primo evento Direct3D dopo la chiamata da presentare e la chiamata a `EndCapture`.  
  
 Per acquisire un intervallo, è necessario preparare l'applicazione per acquisire e registrare le informazioni grafiche, vale a dire, è necessario avere chiamato [Init](init.md) tramite un'istanza di `VsgDbg` classe prima di chiamare `BeginCapture` o `EndCapture`.  
  
## <a name="see-also"></a>Vedere anche  
 [EndCapture](endcapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)