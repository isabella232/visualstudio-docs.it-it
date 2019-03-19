---
title: IDebugHelper::CreatePropertyBrowserEx | Microsoft Docs
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
ms.openlocfilehash: 01e63d1588fd1e25f3415f22450ed5145752d711
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144576"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Restituisce un visualizzatore di proprietà che esegue il wrapping di una variante e consente la conversione personalizzata di valori VARIANT o tipi VARTYPE in stringhe.  
  
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
 [in] Variante di radice da esplorare.  
  
 `bstrName`  
 [in] Nome da assegnare la radice.  
  
 `pdat`  
 [in] Il thread su cui si desidera richiedere proprietà. Se questo parametro è NULL, non viene eseguito alcun tipo di marshalling.  
  
 `pdf`  
 [in] Oggetto che fornisce formattazione personalizzata per le varianti.  
  
 `ppdob`  
 [out] Il Visualizzatore proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce un visualizzatore di proprietà che esegue il wrapping di una variante e consente la conversione personalizzata di valori VARIANT o tipi VARTYPE in stringhe.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [Interfaccia IDebugHelper](../../winscript/reference/idebughelper-interface.md)   
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)