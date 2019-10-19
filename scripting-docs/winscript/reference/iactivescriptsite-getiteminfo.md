---
title: 'IActiveScriptSite:: GetItemInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 3c0458f42466a264c30a440b1b14a028a2457f12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570918"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Consente al motore di scripting di ottenere informazioni su un elemento aggiunto con il metodo [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
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
 in Nome associato all'elemento, come specificato nel metodo [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `dwReturnMask`  
 in Maschera di bit che specifica le informazioni sull'elemento da restituire. Il motore di scripting deve richiedere la quantità minima di informazioni possibili perché alcuni dei parametri restituiti, ad esempio `ITypeInfo`, possono richiedere molto tempo per il caricamento o la generazione. Può essere una combinazione dei valori seguenti:  
  
|Value|Significato|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Restituisce l'interfaccia `IUnknown` per questo elemento.|  
|SCRIPTINFO_ITYPEINFO|Restituisce l'interfaccia `ITypeInfo` per questo elemento.|  
  
 `ppunkItem`  
 out Indirizzo di una variabile che riceve un puntatore all'interfaccia `IUnknown` associata all'elemento specificato. Il motore di scripting può utilizzare il metodo `IUnknown::QueryInterface` per ottenere l'interfaccia `IDispatch` per l'elemento. Questo parametro riceve NULL se `dwReturnMask` non include il valore SCRIPTINFO_IUNKNOWN. Inoltre, riceve NULL se non è presente alcun oggetto associato al nome dell'elemento; Questo meccanismo viene usato per creare una classe semplice quando l'elemento denominato è stato aggiunto con il flag SCRIPTITEM_CODEONLY impostato nel metodo [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `ppTypeInfo`  
 out Indirizzo di una variabile che riceve un puntatore all'interfaccia `ITypeInfo` associata all'elemento. Questo parametro riceve NULL se `dwReturnMask` non include il valore SCRIPTINFO_ITYPEINFO o se le informazioni sul tipo non sono disponibili per questo elemento. Se le informazioni sul tipo non sono disponibili, l'oggetto non può eseguire l'origine di eventi e l'associazione di nomi deve essere realizzata con il metodo `IDispatch::GetIDsOfNames`. Si noti che l'interfaccia `ITypeInfo` recuperata descrive la coclasse dell'elemento (TKIND_COCLASS) perché l'oggetto può supportare più interfacce e interfacce evento. Se l'elemento supporta l'interfaccia di `IProvideMultipleTypeInfo`, l'interfaccia `ITypeInfo` recuperata è uguale a quella dell'indice zero `ITypeInfo` ottenuta utilizzando il metodo `IProvideMultipleTypeInfo::GetInfoOfIndex`.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`TYPE_E_ELEMENTNOTFOUND`|Impossibile trovare un elemento con il nome specificato.|  
  
## <a name="remarks"></a>Note  
 Questo metodo recupera solo le informazioni indicate dal parametro `dwReturnMask`; Ciò migliora le prestazioni. Se, ad esempio, un'interfaccia `ITypeInfo` non è necessaria per un elemento, non viene specificata in `dwReturnMask`.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)