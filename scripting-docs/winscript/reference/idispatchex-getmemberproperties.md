---
title: 'IDispatchEx:: GetMemberProperties | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8016eef7b6e0da9b9fc88695db845cba7f608ff3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574093"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Recupera le proprietà di un membro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `id`  
 Identifica il membro. USA `GetDispID` o `GetNextDispID` per ottenere l'identificatore di invio.  
  
 `grfdexFetch`  
 Determina le proprietà da recuperare. Può trattarsi di una combinazione dei valori elencati in `pgrfdex` e/o una combinazione dei valori seguenti:  
  
|Value|Significato|  
|-----------|-------------|  
|grfdexPropCanAll|Combina fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct e fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Combina fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct e fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|Combina fdexPropNoSideEffects e fdexPropDynamicType.|  
|grfdexPropAll|Combina grfdexPropCanAll, grfdexPropCannotAll e grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Indirizzo di un `DWORD` che riceve le proprietà richieste. Può trattarsi di una combinazione dei valori seguenti:  
  
|Value|Significato|  
|-----------|-------------|  
|fdexPropCanGet|Il membro può essere ottenuto utilizzando DISPATCH_PROPERTYGET.|  
|fdexPropCannotGet|Impossibile ottenere il membro utilizzando DISPATCH_PROPERTYGET.|  
|fdexPropCanPut|Il membro può essere impostato tramite DISPATCH_PROPERTYPUT.|  
|fdexPropCannotPut|Il membro non può essere impostato con DISPATCH_PROPERTYPUT.|  
|fdexPropCanPutRef|Il membro può essere impostato tramite DISPATCH_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|Il membro non può essere impostato con DISPATCH_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|Il membro non ha effetti collaterali. Un debugger, ad esempio, può ottenere, impostare o chiamare in modo sicuro questo membro senza modificare lo stato dello script di cui è in corso il debug.|  
|fdexPropDynamicType|Il membro è dinamico e può essere modificato nel corso della durata dell'oggetto.|  
|fdexPropCanCall|Il membro può essere chiamato come metodo usando DISPATCH_METHOD.|  
|fdexPropCannotCall|Il membro non può essere chiamato come metodo usando DISPATCH_METHOD.|  
|fdexPropCanConstruct|Il membro può essere chiamato come Costruttore usando DISPATCH_CONSTRUCT.|  
|fdexPropCannotConstruct|Il membro non può essere chiamato come costruttore utilizzando DISPATCH_CONSTRUCT.|  
|fdexPropCanSourceEvents|Il membro può generare eventi.|  
|fdexPropCannotSourceEvents|Il membro non può generare eventi.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|||  
|-|-|  
|`S_OK`|Operazione completata.|  
|`DISP_E_UNKNOWNNAME`|Il nome non è noto.|  
  
## <a name="example"></a>Esempio  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)    
 @No__t_1 [IDispatchEx:: GetDispID](../../winscript/reference/idispatchex-getdispid.md)  
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)