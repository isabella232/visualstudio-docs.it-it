---
title: IDebugComPlusSymbolProvider::AreSymbolsLoaded | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- AreSymbolsLoaded
- IDebugComPlusSymbolProvider::AreSymbolsLoaded
ms.assetid: bbf8707d-f89c-4177-b019-d519f1ec6f4a
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a0e8930dfa38554f2f09e59753abc7845477171
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967261"
---
# <a name="idebugcomplussymbolprovideraresymbolsloaded"></a>IDebugComPlusSymbolProvider::AreSymbolsLoaded
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina se vengono caricati i simboli di debug per il modulo specificato dato l'identificatore del dominio applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT AreSymbolsLoaded (  
   ULONG32 ulAppDomainID,  
   GUID    guidModule  
);  
```  
  
```csharp  
int AreSymbolsLoaded (  
   uint ulAppDomainID,  
   Guid guidModule  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ulAppDomainID`  
 [in] Identificatore per il dominio dell'applicazione.  
  
 `guidModule`  
 [in] Identificatore univoco per il modulo.  
  
## <a name="return-value"></a>Valore restituito  
 Se vengono caricati i simboli di debug, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone le [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaccia.  
  
```cpp#  
HRESULT CDebugSymbolProvider::AreSymbolsLoaded(  
    ULONG32 ulAppDomainID,  
    GUID guidModule  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::AreSymbolsLoaded );  
  
    IfFalseGo( GetModule( idModule, &pModule ) == S_OK, S_FALSE );  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::AreSymbolsLoaded, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
