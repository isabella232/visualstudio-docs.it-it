---
title: IDispatchEx::InvokeEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.InvokeEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33494836e463c9c2fd74acf7835d7e4630747b0e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000752"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Fornisce l'accesso a proprietà e metodi esposti da un `IDispatchEx` oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `id`  
 Identifica il membro. Viene utilizzato `GetDispID` o `GetNextDispID` per ottenere l'ID dispatch.  
  
 `lcid`  
 Contesto di impostazioni locali all'interno del quale devono essere interpretati gli argomenti. Il `lcid` viene passato a `InvokeEx` per consentire all'oggetto interpretare gli argomenti specifici per le impostazioni locali.  
  
 `wFlags`  
 I valori per le note legali `wFlags` sono:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Flag che descrivono il contesto del `InvokeEx` chiamare:  
  
|Value|Significato|  
|-----------|-------------|  
|DISPATCH_METHOD|Come un metodo viene richiamato il membro. Se una proprietà ha lo stesso nome, può essere impostato sia ciò che il flag DISPATCH_PROPERTYGET (definito da `IDispatch`).|  
|DISPATCH_PROPERTYGET|Il membro viene recuperato come un proprietà o un membro dati (definito da `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Il membro viene modificato come un proprietà o un membro dati (definito da `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Il membro viene modificato da un'assegnazione di riferimento anziché da un'assegnazione di valore. Questo flag è valido solo quando la proprietà accetta un riferimento a un oggetto (definito da `IDispatch`).|  
|DISPATCH_CONSTRUCT|Il membro è utilizzato come costruttore. (Si tratta di un nuovo valore definito da `IDispatchEx`). I valori per le note legali `wFlags` sono:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Puntatore a una struttura contenente una matrice di argomenti, una matrice di DISPID per argomenti denominati e i conteggi del numero di elementi nelle matrici. Vedere il `IDispatch` documentazione per una descrizione completa della struttura DISPPARAMS.  
  
 `pVarRes`  
 Puntatore alla posizione in cui il risultato viene archiviato o Null se il chiamante si aspetta alcun risultato. Questo argomento viene ignorato se si specifica DISPATCH_PROPERTYPUT o DISPATCH_PROPERTYPUTREF.  
  
 `pei`  
 Puntatore a una struttura contenente informazioni sull'eccezione. Se è necessario specificare questa struttura `DISP_E_EXCEPTION` viene restituito. Può essere Null. Vedere le `IDispatch` documentazione per una descrizione completa del `EXCEPINFO` struttura.  
  
 `pspCaller`  
 Puntatore a un oggetto provider di servizi fornito dal chiamante, che consente all'oggetto ottenere i servizi dal chiamante. Può essere Null.  
  
 `IDispatchEx::InvokeEx` fornisce tutte le stesse funzionalità `IDispatch::Invoke` e aggiunge alcune estensioni:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Indica che l'elemento viene utilizzato come un costruttore.|  
|`pspCaller`|Il `pspCaller` consente l'accesso agli oggetti per i servizi forniti dal chiamante. Servizi specifici possono essere gestiti dal chiamante se stesso o delegati ai chiamanti ulteriormente la catena di chiamate. Ad esempio, se un motore di script all'interno di un browser invia un `InvokeEx` chiamata a un oggetto esterno, l'oggetto è possibile seguire il `pspCaller` catena per ottenere i servizi dal motore di script o browser. (Si noti che la catena di chiamate non è quello utilizzato per la catena di creazione, noto anche come catena di contenitore o la catena di sito. La catena di creazione potrebbe essere disponibile tramite un altro meccanismo, ad esempio `IObjectWithSite`.)|  
|Puntatore `this`|Quando è impostata DISPATCH_METHOD `wFlags`, potrebbe esserci un "parametro denominato" per il valore di "this". DISPID sarà DISPID_THIS e deve essere il primo parametro denominato.|  
  
 Inutilizzata `riid` parametro in `IDispatch::Invoke` è stata rimossa.  
  
 Il `puArgArr` parametro in `IDispatch::Invoke` è stata rimossa.  
  
 Vedere il `IDispatch::Invoke` documentazione per gli esempi seguenti:  
  
 "Chiama un metodo senza argomenti"  
  
 "Ottenere e impostare le proprietà"  
  
 "Passaggio di parametri"  
  
 "Le proprietà indicizzate"  
  
 "Generazione di eccezioni durante Invoke"  
  
 "Restituzione di errori"  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|||  
|-|-|  
|`S_OK`|Operazione completata.|  
|DISP_E_BADPARAMCOUNT|Il numero di elementi forniti al DISPPARAMS è diverso dal numero di argomenti accettati dal metodo o proprietà.|  
|DISP_E_BADVARTYPE|Uno degli argomenti in `rgvarg` non è un tipo variant valido.|  
|DISP_E_EXCEPTION|L'applicazione deve generare un'eccezione. In questo caso, la struttura passato `pei` deve essere compilato.|  
|DISP_E_MEMBERNOTFOUND|Il membro richiesto non esiste, altrimenti la chiamata a `InvokeEx` ha provato a impostare il valore di una proprietà di sola lettura.|  
|DISP_E_NONAMEDARGS|Questa implementazione di `IDispatch` non supporta argomenti denominati.|  
|DISP_E_OVERFLOW|Uno degli argomenti in `rgvarg` non può essere assegnato forzatamente al tipo specificato.|  
|DISP_E_PARAMNOTFOUND|Uno dei DISPID di parametro non corrisponde a un parametro del metodo.|  
|DISP_E_TYPEMISMATCH|Uno o più argomenti non possono essere forzati.|  
|DISP_E_UNKNOWNLCID|Il membro richiamato interpreta gli argomenti stringa secondo l'identificatore LCID, e l'identificatore LCID non riconosciuto. Se l'identificatore LCID non è necessaria per interpretare gli argomenti, questo errore non deve essere restituito.|  
|DISP_E_PARAMNOTOPTIONAL|È stato omesso un parametro obbligatorio.|  
  
## <a name="example"></a>Esempio  
  
```cpp
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)