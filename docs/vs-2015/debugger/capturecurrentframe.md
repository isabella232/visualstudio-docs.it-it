---
title: CaptureCurrentFrame | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b2fcb05d63370f8f40ab09f0978e0f49dbe7d6a3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529049"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CaptureCurrentFrame](https://docs.microsoft.com/visualstudio/debugger/graphics/capturecurrentframe).  
  
Acquisisce il resto del frame corrente nel file di log di grafica.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Note  
 Se è attualmente in corso un'altra acquisizione, ad esempio un'acquisizione avviata dalla funzione `BeginCapture`, tale acquisizione viene completata e registrata nel log di grafica come frame distinto. Immediatamente dopo, la diagnostica della grafica inizia ad acquisire la parte restante del frame corrente, che viene a sua volta registrata come frame distinto. La fine del frame corrente viene contrassegnata da una chiamata da presentare.  
  
 Per acquisire un frame, è necessario preparare l'applicazione per acquisire e registrare le informazioni grafiche, vale a dire, è necessario avere chiamato [Init](../debugger/init.md) tramite un'istanza di `VsgDbg` classe prima di chiamare `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Vedere anche  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)



