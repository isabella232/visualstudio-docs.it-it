---
title: AddMessage | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b60f8bac24b01e39327357b89e9e96c04765077
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249002"
---
# <a name="addmessage"></a>AddMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aggiunge un messaggio personalizzato alla diagnostica della grafica *HUD* (Head-Up Display).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `szMessage`  
 Messaggio da aggiungere a HUD.  
  
## <a name="remarks"></a>Note  
 La diagnostica della grafica HUD viene visualizzata nell'angolo superiore sinistro dell'applicazione in esecuzione nella diagnostica della grafica. Vengono visualizzate le informazioni di runtime sull'applicazione e sull'acquisizione delle informazioni grafiche e i messaggi aggiunti chiamando questa funzione.  
  
 Per aggiungere un messaggio a HUD, non è necessario acquisire attivamente informazioni grafiche, ovvero, ovvero un messaggio può essere aggiunto tramite un'istanza del `VsgDbg` (classe), ma la [Init](../debugger/init.md) funzione membro non deve essere chiamato per primo. I messaggi vengono visualizzati solo in HUD, non vengono registrati nei file di log di grafica.



