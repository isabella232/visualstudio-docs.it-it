---
title: UnInit | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cd66d7329fa4bfc288f3d60879e45cc86ded94e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520230"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [UnInit](https://docs.microsoft.com/visualstudio/debugger/graphics/uninit).  
  
Finalizza il file di log di grafica, lo chiude e libera le risorse utilizzate durante la registrazione attiva delle informazioni grafiche da parte dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>Note  
 `UnInit` viene automaticamente chiamata quando viene eliminata un'istanza della classe `VsgDbg`. Se l'istanza `VsgDbg` non stava registrando attivamente le informazioni grafiche, questa operazione non ha effetto.  
  
 Una volta chiamata `UnInit` su un'istanza della classe `VsgDbg`, è possibile creare e un nuovo file di log di grafica chiamando `Init` e finalizzarlo chiamando `UnInit`. È possibile ripetere questa procedura tutte le volte che si desidera utilizzare la stessa istanza `VsgDbg` per creare diversi file di log di grafica indipendenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Init](../debugger/init.md)



