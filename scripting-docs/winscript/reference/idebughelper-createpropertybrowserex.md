---
title: 'IDebugHelper:: CreatePropertyBrowserEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowserEx
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowserEx
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d64d9dad54e029dc4c76e8b7e6c7a3f0299b0cb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576493"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Restituisce un visualizzatore proprietà che esegue il wrapping di una variante e consente la conversione personalizzata di valori VARIANT o tipi VARTYPE in stringhe.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pvar`  
 in Variante radice da esplorare.  
  
 `bstrName`  
 in Nome da assegnare alla radice.  
  
 `pdat`  
 in Thread su cui richiedere le proprietà. Se questo parametro è NULL, non viene eseguito alcun marshalling.  
  
 `pdf`  
 in Oggetto che fornisce la formattazione personalizzata per le varianti.  
  
 `ppdob`  
 out Browser delle proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce un visualizzatore proprietà che esegue il wrapping di una variante e consente la conversione personalizzata di valori VARIANT o tipi VARTYPE in stringhe.  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [IDebugHelper:: CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)  
 [Interfaccia IDebugHelper](../../winscript/reference/idebughelper-interface.md)    
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)