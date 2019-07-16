---
title: 'VsgDbg:: ~ VsgDbg (distruttore) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0ae3dd206953e728175f4479920861295feae00
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200294"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (distruttore)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Elimina un'istanza di `VsgDbg` classe. Se viene registrate in modo attivo le informazioni grafiche, il file di log di grafica viene finalizzato e chiusa e vengono rilasciate le risorse che sono state usate durante l'acquisizione attivamente informazioni grafiche.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VsgDbg::VsgDbg (Costruttore)](../debugger/vsgdbg-vsgdbg-constructor.md)
