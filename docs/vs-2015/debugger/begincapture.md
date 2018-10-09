---
title: BeginCapture | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2f9bc573799ddb5fdd094c7c0e571a88c13b5420
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518505"
---
# <a name="begincapture"></a>BeginCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [BeginCapture](https://docs.microsoft.com/visualstudio/debugger/graphics/begincapture).  
  
Inizia un intervallo di acquisizione che termina con `EndCapture`.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
void BeginCapture();  
```  
  
## <a name="remarks"></a>Note  
 Un intervallo di acquisizione in genere estende un subset di un singolo frame, come ad esempio quando si desidera acquisire informazioni grafiche solo su un determinato tipo di chiamata di disegno. Se l'intervallo di acquisizione estende una chiamata da presentare, vengono acquisiti due frame di informazioni grafiche. Il primo frame estende l'intervallo tra la chiamata a `BeginCapture` e la chiamata da presentare; il secondo frame estende l'intervallo tra il primo evento Direct3D dopo la chiamata da presentare e la chiamata a `EndCapture`.  
  
 Per acquisire un intervallo, è necessario preparare l'applicazione per acquisire e registrare le informazioni grafiche, vale a dire, è necessario avere chiamato [Init](../debugger/init.md) tramite un'istanza di `VsgDbg` classe prima di chiamare `BeginCapture` o `EndCapture`.  
  
## <a name="see-also"></a>Vedere anche  
 [EndCapture](../debugger/endcapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)


