---
title: IDebugSettingsCallback2::EnumEEs | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: afc9337ac2312c356fe5ea6fcbe9cfb492ea5221
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517686"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugSettingsCallback2::EnumEEs](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugsettingscallback2-enumees).  
  
Enumera gli analizzatori di espressioni disponibili assegnati gli identificatori di lingua e il fornitore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT EnumEEs(  
   DWORD  celtBuffer,  
   GUID*  rgguidLang,  
   GUID*  rgguidVendor,  
   DWORD* pceltEEs  
);  
```  
  
```csharp  
public int EnumEEs(  
   uint       celtBuffer,  
   ref Guid   rgguidLang,  
   ref Guid   rgguidVendor,  
   ref uint[] pceltEEs  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celtBuffer`  
 [in] Numero di elementi nel `pceltEEs` buffer.  
  
 `rgguidLang`  
 [in, out] Identificatore univoco per il linguaggio di programmazione.  
  
 `rgguidVendor`  
 [in, out] Identificatore univoco del fornitore.  
  
 `pceltEEs`  
 [in, out] Matrice di analizzatori di espressioni.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

