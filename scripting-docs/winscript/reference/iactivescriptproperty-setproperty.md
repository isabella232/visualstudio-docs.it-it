---
title: 'IActiveScriptProperty:: SetProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8307a82f181be20205c7bfcc47e881b0fa1e90
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571315"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Imposta la proprietà specificata dal parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:   
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwProperty`  
 Valore della proprietà da impostare.  
  
 `pvarIndex`  
 Non usato.  
  
 `pvarValue`  
 Valore della proprietà.  
  
 Nella tabella seguente sono descritti i valori consentiti per `dwProperty`.  
  
|Costante|Value|Significato|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Impone al motore di script di dividere in modalità Integer anziché in modalità a virgola mobile. Il valore predefinito è `False`.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Consente la sostituzione della funzione di confronto tra stringhe del motore di script.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Informa il motore di script che non esistono altri motori di script per contribuire all'oggetto globale.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Impone al motore di scripting [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] di selezionare un set di funzionalità del linguaggio da supportare. Il set predefinito di funzionalità del linguaggio supportate dal motore di script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è equivalente al set di funzionalità del linguaggio presente nella versione 5,7 del motore di script di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_UNEXPECTED`|La chiamata non era prevista (ad esempio, il motore di scripting non è ancora stato caricato o inizializzato).|  
  
## <a name="remarks"></a>Note  
 Per abilitare o disabilitare la divisione di interi, richiamare `SetProperty` e convertire una `Boolean` in un `Object`. Per impostazione predefinita, il valore della proprietà è `False`. Se lo si imposta su `True`, le operazioni di divisione restituiranno solo numeri interi.  
  
 Per abilitare o disabilitare il confronto di stringhe personalizzato, richiamare `SetProperty` e passare un valore `Object`. L'oggetto passato deve implementare l'interfaccia [IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md)dell'interfaccia. Il metodo [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) dell'interfaccia dell' [interfaccia IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md) viene chiamato ogni volta che viene eseguita una funzione di confronto di stringhe.  
  
 Per selezionare il set di funzionalità del linguaggio da supportare durante l'inizializzazione del motore di script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], richiamare `SetProperty` e passare un valore corrispondente al set di funzionalità del linguaggio da abilitare per SCRIPTPROP_INVOKEVERSIONING. Se questa proprietà è impostata su 1 (SCRIPTLANGUAGEVERSION_5_7), le funzionalità del linguaggio disponibili sono le stesse di quelle visualizzate nella versione 5,7 del motore di scripting di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Se è impostato su 2 (SCRIPTLANGUAGEVERSION_5_8), le funzionalità del linguaggio disponibili sono quelle visualizzate nella versione 5,7 oltre alle nuove funzionalità aggiunte alla versione 5,8. Per impostazione predefinita, questa proprietà è impostata su 0 (SCRIPTLANGUAGEVERSION_DEFAULT), equivalente al set di funzionalità del linguaggio visualizzato nella versione 5,7, a meno che l'host non supporti un comportamento predefinito diverso. Internet Explorer 8, ad esempio, consente di optare per le funzionalità del linguaggio [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] supportate dalla versione 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di scripting per impostazione predefinita quando la modalità documento predefinita per Internet Explorer 8 è la modalità "standard di Internet Explorer 8". Il cambio della modalità documento di Internet Explorer 8 con gli standard di Internet Explorer 7 o la modalità non standard Reimposta il motore di script di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] per supportare solo il set di funzionalità del linguaggio presente nella versione 5,7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di scripting.  
  
> [!NOTE]
> SCRIPTPROP_INVOKEVERSIONING deve essere impostato solo quando è in corso l'inizializzazione del motore di script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come forzare il motore di scripting a utilizzare la divisione Integer e come consentire l'overload della funzione di confronto.  
  
```c#  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Definizione della compatibilità del documento](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))    
 @No__t_1 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)  
 [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md)