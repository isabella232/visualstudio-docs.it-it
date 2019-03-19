---
title: IActiveScriptProperty::GetProperty | Microsoft Docs
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
ms.openlocfilehash: e10d72e289fc2dc31464ce4505cea5c03e8d7f9d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160693"
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
 Il valore della proprietà da ottenere.  
  
 `pvarIndex`  
 Non usato.  
  
 `pvarValue`  
 Valore della proprietà.  
  
 I valori consentiti per `dwProperty` sono descritti nella tabella seguente.  
  
|Costante|Value|Significato|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Forza il motore di scripting per dividere in modalità di numero intero anziché in modalità del punto a virgola mobile.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Consente la funzione di confronto di stringa del motore di scripting da sostituire.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Segnala al motore di scripting non altri motori di script esistenti per contribuire all'oggetto globale.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Forza il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di script per selezionare un set di funzionalità del linguaggio a essere supportato. Il set predefinito di funzionalità del linguaggio supportate dal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] equivale a set di funzionalità del linguaggio che è disponibile nella versione 5.7 di motore di scripting di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di scripting.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di scripting non è ancora caricato o inizializzato).|  
  
## <a name="remarks"></a>Note  
 L'host può utilizzare la proprietà SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION per informare un motore di scripting non altri motori di script esistenti per contribuire all'oggetto globale. Ad esempio, Internet Explorer è possibile informare il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore contenente solo la pagina sottoposta a rendering [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] script. In questo modo, solo il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore può aggiungere nuove proprietà alla finestra di oggetti globali e nessun modulo di gestione di Visual Basic Scripting Edition (VBScript) per eseguire la stessa. Il motore può ignorano questo flag o usarlo per ottimizzare la gestione dei nuovi membri che vengono aggiunti all'oggetto globale.  
  
 L'host può utilizzare la proprietà SCRIPTPROP_INVOKEVERSIONING per selezionare il set di funzionalità del linguaggio a essere supportati quando il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di scripting viene avviato. Se questa proprietà è impostata su 1 (SCRIPTLANGUAGEVERSION_5_7), le funzionalità del linguaggio disponibili sono identici a quelli che è disponibile nella versione 5.7 del [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di scripting. Se è impostata su 2 (SCRIPTLANGUAGEVERSION_5_8), le funzionalità del linguaggio disponibili sono quelli che è disponibile nella versione 5.7, oltre a funzionalità che sono stati aggiunti nella versione 5.8. Per impostazione predefinita, questa proprietà è impostata su 0 (SCRIPTLANGUAGEVERSION_DEFAULT), che equivale a set di funzionalità del linguaggio che è disponibile nella versione 5.7, a meno che l'host supporta un comportamento predefinito diverso. Ad esempio, Internet Explorer 8 opts nel [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funzionalità del linguaggio supportate dalla versione 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di scripting per impostazione predefinita quando la modalità documento per Internet Explorer 8 è "Standard di Internet Explorer 8".  
  
## <a name="see-also"></a>Vedere anche  
 [Definizione della compatibilità del documento](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md)