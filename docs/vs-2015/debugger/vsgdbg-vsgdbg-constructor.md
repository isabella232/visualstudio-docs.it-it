---
title: 'Vsgdbg:: Vsgdbg (costruttore) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a35443dbf4fc413908c61e989d2138122c0991
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527872"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (costruttore)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [vsgdbg:: Vsgdbg (costruttore)](https://docs.microsoft.com/visualstudio/debugger/graphics/vsgdbg-vsgdbg-constructor).  
  
Costruisce un'istanza della classe `VsgDbg` con o senza la preparazione del componente della diagnostica della grafica integrato nell'applicazione per acquisire e registrare attivamente le informazioni grafiche per impostazione predefinita, in base al parametro booleano specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `bDefaultInit`  
 `true` per specificare che il componente di diagnostica della grafica integrato nell'applicazione deve essere preparato per acquisire e registrare attivamente le informazioni grafiche; `false` per specificare che in questo momento l'applicazione non deve essere preparata per acquisire e registrare attivamente le informazioni grafiche.  
  
## <a name="remarks"></a>Note  
 Quando il costruttore viene chiamato con `bDefaultInit` impostata su `true`, il nome file del file di log di grafica viene determinato dal modo in cui `DONT_SAVE_VSGLOG_TO_TEMP` e `VSG_DEFAULT_RUN_FILENAME` vengono definiti i simboli del preprocessore prima `vsgcapture.h` è incluso nell'app.  
  
 Quando il costruttore viene chiamato con `bDefaultInit` impostato su `false`, il componente di diagnostica della grafica integrato nell'applicazione può essere preparato per acquisire e registrare attivamente le informazioni grafiche in un secondo momento chiamando la funzione `Init`.  
  
## <a name="see-also"></a>Vedere anche  
 [VsgDbg:: ~ VsgDbg (distruttore)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)



