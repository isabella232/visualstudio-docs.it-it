---
title: 'Iactivescriptsite:: GetItemInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4dc6515d64406870ca10f003d7cea515c49b7d8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095888"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Consente al motore di scripting ottenere informazioni su un elemento aggiunto con il [IActiveScript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) (metodo).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrName`  
 [in] Il nome associato all'elemento, come specificato nella [IActiveScript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) (metodo).  
  
 `dwReturnMask`  
 [in] Maschera di bit che specifica le informazioni sull'elemento devono essere restituite. Il motore di scripting deve richiedere la quantità minima di informazioni possibili perché alcuni dei parametri restituiti (ad esempio, `ITypeInfo`) può richiedere molto tempo per caricare o generare. Può essere una combinazione dei valori seguenti:  
  
|Valore|Significato|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Restituisce il `IUnknown` interfaccia per questo elemento.|  
|SCRIPTINFO_ITYPEINFO|Restituisce il `ITypeInfo` interfaccia per questo elemento.|  
  
 `ppunkItem`  
 [out] Indirizzo di una variabile che riceve un puntatore per il `IUnknown` interfaccia associata all'elemento specificato. Il motore di script è possibile usare la `IUnknown::QueryInterface` metodo per ottenere il `IDispatch` interfaccia per l'elemento. Questo parametro riceve NULL se `dwReturnMask` non include il valore SCRIPTINFO_IUNKNOWN. Inoltre, riceve NULL se nessun oggetto associato al nome di elemento; Questo meccanismo viene usato per creare una semplice classe quando è stato aggiunto l'elemento denominato con il flag SCRIPTITEM_CODEONLY impostato [IActiveScript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) (metodo).  
  
 `ppTypeInfo`  
 [out] Indirizzo di una variabile che riceve un puntatore per il `ITypeInfo` interfaccia associato all'elemento. Questo parametro riceve NULL se `dwReturnMask` non include il valore SCRIPTINFO_ITYPEINFO, o se le informazioni sul tipo non è disponibile per questo elemento. Se le informazioni sul tipo non è disponibile, l'oggetto non è l'origine degli eventi e l'associazione di nomi deve essere realizzato con i `IDispatch::GetIDsOfNames` (metodo). Si noti che il `ITypeInfo` interfaccia recuperata descrive (coclasse) dell'elemento (TKIND_COCLASS) perché l'oggetto può supportare più interfacce e le interfacce di eventi. Se l'elemento supporta il `IProvideMultipleTypeInfo` interfaccia, il `ITypeInfo` interfaccia recuperato è quello utilizzato per l'indice da zero `ITypeInfo` che sarebbe possibile ottenere usando il `IProvideMultipleTypeInfo::GetInfoOfIndex` (metodo).  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`TYPE_E_ELEMENTNOTFOUND`|Non è stato trovato un elemento il nome specificato.|  
  
## <a name="remarks"></a>Note  
 Questo metodo recupera solo le informazioni indicate dal `dwReturnMask` parametro; Ciò migliora le prestazioni. Ad esempio, se un' `ITypeInfo` interfaccia non è necessaria per un elemento, semplicemente non è specificato `dwReturnMask`.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)