---
title: 'IDispatchEx:: InvokeEx | Microsoft Docs'
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
ms.openlocfilehash: 8a15acb3211c0d3dd19c0d262efb6cbd3327ab9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575311"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Fornisce l'accesso alle proprietà e ai metodi esposti da un oggetto `IDispatchEx`.  
  
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
 Identifica il membro. USA `GetDispID` o `GetNextDispID` per ottenere l'identificatore di invio.  
  
 `lcid`  
 Contesto di impostazioni locali all'interno del quale devono essere interpretati gli argomenti. Il `lcid` viene passato a `InvokeEx` per consentire all'oggetto di interpretare gli argomenti specifici delle impostazioni locali.  
  
 `wFlags`  
 I valori validi per `wFlags` sono:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Flag che descrivono il contesto della chiamata `InvokeEx`:  
  
|Value|Significato|  
|-----------|-------------|  
|DISPATCH_METHOD|Il membro viene richiamato come metodo. Se una proprietà ha lo stesso nome, è possibile impostare sia il flag che il flag DISPATCH_PROPERTYGET (definito da `IDispatch`).|  
|DISPATCH_PROPERTYGET|Il membro viene recuperato come una proprietà o un membro dati (definito da `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Il membro viene modificato come una proprietà o un membro dati (definito da `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Il membro viene modificato da un'assegnazione di riferimento anziché da un'assegnazione di valore. Questo flag è valido solo quando la proprietà accetta un riferimento a un oggetto (definito da `IDispatch`).|  
|DISPATCH_CONSTRUCT|Il membro viene usato come costruttore. Si tratta di un nuovo valore definito da `IDispatchEx`. I valori validi per `wFlags` sono:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Puntatore a una struttura contenente una matrice di argomenti, una matrice di DISPID per argomenti denominati e i conteggi del numero di elementi nelle matrici. Per una descrizione completa della struttura DISPPARAMS, vedere la documentazione `IDispatch`.  
  
 `pVarRes`  
 Puntatore alla posizione in cui deve essere archiviato il risultato o null se il chiamante non prevede alcun risultato. Questo argomento viene ignorato se è specificato DISPATCH_PROPERTYPUT o DISPATCH_PROPERTYPUTREF.  
  
 `pei`  
 Puntatore a una struttura contenente informazioni sull'eccezione. Questa struttura deve essere compilata se viene restituito `DISP_E_EXCEPTION`. Può essere null. Per una descrizione completa della struttura `EXCEPINFO`, vedere la documentazione `IDispatch`.  
  
 `pspCaller`  
 Puntatore a un oggetto provider di servizi fornito dal chiamante, che consente all'oggetto di ottenere servizi dal chiamante. Può essere null.  
  
 `IDispatchEx::InvokeEx` offre tutte le stesse funzionalità di `IDispatch::Invoke` e aggiunge alcune estensioni:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Indica che l'elemento viene utilizzato come costruttore.|  
|`pspCaller`|Il `pspCaller` consente all'oggetto di accedere ai servizi forniti dal chiamante. I servizi specifici possono essere gestiti dal chiamante stesso o delegati ai chiamanti più in alto nella catena di chiamate. Se, ad esempio, un modulo di gestione di script all'interno di un browser esegue una chiamata `InvokeEx` a un oggetto esterno, l'oggetto può seguire la catena di `pspCaller` per ottenere servizi dal motore di script o dal browser. Si noti che la catena di chiamate non corrisponde alla catena di creazione, nota anche come catena di contenitori o catena di siti. La catena di creazione può essere disponibile tramite un altro meccanismo, ad esempio `IObjectWithSite`.|  
|Puntatore `this`|Quando DISPATCH_METHOD è impostato in `wFlags`, è possibile che sia presente un "parametro denominato" per il valore "This". Il DISPID sarà DISPID_THIS e deve essere il primo parametro denominato.|  
  
 Il parametro `riid` non usato in `IDispatch::Invoke` è stato rimosso.  
  
 Il parametro `puArgArr` in `IDispatch::Invoke` è stato rimosso.  
  
 Vedere la documentazione `IDispatch::Invoke` per gli esempi seguenti:  
  
 "Chiamata a un metodo senza argomenti"  
  
 "Recupero e impostazione delle proprietà"  
  
 "Passaggio di parametri"  
  
 "Proprietà indicizzate"  
  
 "Generazione di eccezioni durante la chiamata"  
  
 "Restituzione degli errori"  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|||  
|-|-|  
|`S_OK`|Operazione completata.|  
|DISP_E_BADPARAMCOUNT|Il numero di elementi fornito a DISPPARAMS è diverso dal numero di argomenti accettati dal metodo o dalla proprietà.|  
|DISP_E_BADVARTYPE|Uno degli argomenti in `rgvarg` non è un tipo Variant valido.|  
|DISP_E_EXCEPTION|L'applicazione deve generare un'eccezione. In questo caso, è necessario compilare la struttura passata in `pei`.|  
|DISP_E_MEMBERNOTFOUND|Il membro richiesto non esiste o la chiamata a `InvokeEx` ha tentato di impostare il valore di una proprietà di sola lettura.|  
|DISP_E_NONAMEDARGS|Questa implementazione di `IDispatch` non supporta argomenti denominati.|  
|DISP_E_OVERFLOW|Non è stato possibile assegnare uno degli argomenti in `rgvarg` al tipo specificato.|  
|DISP_E_PARAMNOTFOUND|Uno dei DISPID del parametro non corrisponde a un parametro nel metodo.|  
|DISP_E_TYPEMISMATCH|Non è stato possibile assegnare uno o più argomenti.|  
|DISP_E_UNKNOWNLCID|Il membro richiamato interpreta gli argomenti stringa in base all'identificatore LCID e l'identificatore LCID non è riconosciuto. Se l'identificatore LCID non è necessario per interpretare gli argomenti, questo errore non dovrebbe essere restituito.|  
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
 @No__t_1 [IDispatchEx:: GetDispID](../../winscript/reference/idispatchex-getdispid.md)  
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)