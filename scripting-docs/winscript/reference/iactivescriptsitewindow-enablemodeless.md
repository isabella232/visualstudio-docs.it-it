---
title: IActiveScriptSiteWindow::EnableModeless | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f15135273b98a65903a5d03de87c541fc032cce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992926"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Fa sì che l'host abilitare o disabilitare la finestra principale, nonché eventuali finestre di dialogo non modale.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `fEnable`  
 [in] Flag che, se `TRUE`, abilita la finestra principale e le finestre di dialogo non modale oppure, se `FALSE`, li disabilita.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` caso di esito positivo o `E_FAIL` se si è verificato un errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo è identico al `IOleInPlaceFrame::EnableModeless` (metodo).  
  
 Chiamate a questo metodo possono essere annidate.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)