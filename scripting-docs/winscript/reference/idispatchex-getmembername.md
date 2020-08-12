---
title: 'IDispatchEx:: GetMemberName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberName
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberName method
ms.assetid: 5e59b63c-b781-4b90-88fd-40603a379a2d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8dbfb82e986ed6d1738bcc0cffeec35e5ba4515c
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144610"
---
# <a name="idispatchexgetmembername"></a>IDispatchEx::GetMemberName
Recupera il nome di un membro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetMemberName(  
   DISPID id,  
   BSTR *pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `id`  
 Identifica il membro. USA `GetDispID` o `GetNextDispID` per ottenere l'identificatore di invio.  
  
 `pbstrName`  
 Indirizzo di un oggetto `BSTR` che riceve il nome del membro. L'applicazione chiamante è responsabile della liberazione di questo valore.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|valore|Significato|
|-|-|  
|`S_OK`|Operazione completata.|  
|`DISP_E_UNKNOWNNAME`|Il nome non è noto.|  
  
## <a name="example"></a>Esempio  
  
```cpp
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
   SysFreeString(bstrName);  
   hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx:: GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)