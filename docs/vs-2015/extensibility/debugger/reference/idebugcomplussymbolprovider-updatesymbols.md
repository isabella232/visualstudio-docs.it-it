---
title: IDebugComPlusSymbolProvider::UpdateSymbols | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UpdateSymbols
- IDebugComPlusSymbolProvider::UpdateSymbols
ms.assetid: d530f6f1-4af2-454b-bab0-02478a8fe81e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a7e9f699640db9a8a42b9e0c45148a337cd5553
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890413"
---
# <a name="idebugcomplussymbolproviderupdatesymbols"></a>IDebugComPlusSymbolProvider::UpdateSymbols
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Aggiorna i simboli di debug in memoria con quelli del flusso di dati specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT UpdateSymbols (  
   ULONG32  ulAppDomainID,  
   GUID     guidModule,  
   IStream* pUpdateStream  
);  
```  
  
```csharp  
int UpdateSymbols (  
   uint    ulAppDomainID,  
   Guid    guidModule,  
   IStream pUpdateStream  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ulAppDomainID`  
 [in] Identificatore del dominio dell'applicazione.  
  
 `guidModule`  
 [in] Identificatore univoco del modulo.  
  
 `pUpdateStream`  
 [in] Flusso di dati che contiene i simboli di debug aggiornato.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone le [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaccia.  
  
```cpp#  
HRESULT CDebugSymbolProvider::UpdateSymbols(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IStream* pUpdateStream  
)  
{  
    ASSERT(!"Use UpdateSymbols2 on IDebugENCSymbolProvider2");  
    return E_NOTIMPL;  
}  
  
HRESULT CDebugSymbolProvider::UpdateSymbols2(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IStream* pUpdateStream,  
    LINEDELTA* pDeltaLines,  
    ULONG cDeltaLines  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::UpdateSymbols );  
  
    IfFailGo( GetModule( idModule, &pModule ) );  
    IfFailGo( pModule->UpdateSymbols( pUpdateStream, pDeltaLines, cDeltaLines ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::UpdateSymbols, hr );  
  
    return hr;  
}  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)

