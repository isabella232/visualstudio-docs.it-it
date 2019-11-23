---
title: 'IActiveScriptProperty:: GetProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1eeec6472a067d18a8b8962cfac70c25c0ff971
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571410"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Ottiene la proprietà specificata dal parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetProperty(  
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
 Valore della proprietà da ottenere.  
  
 `pvarIndex`  
 Non usato.  
  
 `pvarValue`  
 Valore della proprietà.  
  
 Nella tabella seguente sono descritti i valori consentiti per `dwProperty`.  
  
|Costante|Valore|Significato|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Impone al motore di script di dividere in modalità Integer anziché in modalità a virgola mobile.|  
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
 L'host può utilizzare la proprietà SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION per informare un motore di script che non esistono altri motori di scripting per contribuire all'oggetto globale. Internet Explorer può ad esempio informare il motore di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] che la pagina di cui viene eseguito il rendering contiene solo [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] script. Pertanto, solo il motore di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] può aggiungere nuove proprietà alla finestra oggetto globale e non è presente alcun motore di Visual Basic Scripting Edition (VBScript) per eseguire la stessa operazione. Il motore può ignorare questo flag oppure può usarlo per ottimizzare la gestione dei nuovi membri aggiunti all'oggetto globale.  
  
 L'host può utilizzare la proprietà SCRIPTPROP_INVOKEVERSIONING per selezionare il set di funzionalità del linguaggio da supportare al momento dell'avvio del motore di scripting [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Se questa proprietà è impostata su 1 (SCRIPTLANGUAGEVERSION_5_7), le funzionalità del linguaggio disponibili sono le stesse di quelle visualizzate nella versione 5,7 del motore di script di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Se è impostato su 2 (SCRIPTLANGUAGEVERSION_5_8), le funzionalità del linguaggio disponibili sono quelle visualizzate nella versione 5,7 oltre alle funzionalità aggiunte alla versione 5,8. Per impostazione predefinita, questa proprietà è impostata su 0 (SCRIPTLANGUAGEVERSION_DEFAULT), equivalente al set di funzionalità del linguaggio visualizzato nella versione 5,7, a meno che l'host non supporti un comportamento predefinito diverso. Internet Explorer 8, ad esempio, consente di optare per le funzionalità del linguaggio [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] supportate dalla versione 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di scripting per impostazione predefinita quando la modalità documento per Internet Explorer 8 è la modalità "standard di Internet Explorer 8".  
  
## <a name="see-also"></a>Vedere anche  
 [Definizione della compatibilità del documento](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md)