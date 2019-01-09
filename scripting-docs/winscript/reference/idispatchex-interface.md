---
title: Interfaccia IDispatchEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a59f30c5b42301d29b73a4a079837423614da49
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087581"
---
# <a name="idispatchex-interface"></a>Interfaccia IDispatchEx
`IDispatchEx`, un'estensione del `IDispatch` interfaccia, il supporto di funzionalità appropriate per linguaggi dinamici quali linguaggi di scripting. Questa sezione vengono descritte le `IDispatchEx` interfaccia stessa, le differenze tra `IDispatch` e `IDispatchEx`e la base logica per le estensioni. È previsto che i lettori abbiano familiari `IDispatch` e avere accesso al `IDispatch` documentazione.  
  
## <a name="remarks"></a>Note  
 `IDispatch` essenzialmente è stato sviluppato per Microsoft Visual Basic. La limitazione principale di `IDispatch` è che presuppone che gli oggetti sono statici. In altre parole, poiché gli oggetti non vengono modificano durante la fase di esecuzione, le informazioni sul tipo possono completamente descriverli in fase di compilazione. I modelli in fase di esecuzione dinamici presenti nei linguaggi di scripting, ad esempio Visual Basic Scripting Edition (VBScript) e [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] e modelli a oggetti, ad esempio HTML dinamico è necessaria un'interfaccia più flessibile.  
  
 `IDispatchEx` è stato sviluppato per fornire tutti i servizi di `IDispatch` , nonché alcune estensioni che sono appropriate per le lingue con associazione tardiva più dinamiche, ad esempio linguaggi di scripting. Le funzionalità aggiuntive del `IDispatchEx` oltre a quelli forniti da `IDispatch` sono:  
  
- Aggiungere nuovi membri a un oggetto ("expando"), usare `GetDispID` con il `fdexNameEnsure` flag.  
  
- Eliminare i membri di un oggetto, usare `DeleteMemberByName` o `DeleteMemberByDispID`.  
  
- Le operazioni di invio tra maiuscole e minuscole, usare `fdexNameCaseSensitive` o `fdexNameCaseInsensitive`.  
  
- Ricerca di membri con nome implicito, ovvero usare `fdexNameImplicit`.  
  
- Enumerare i DISPID di un oggetto, ovvero usare `GetNextDispID`.  
  
- Mappa di DISPID per nome dell'elemento, ovvero usare `GetMemberName`.  
  
- Ottenere le proprietà dei membri dell'oggetto, ovvero usare `GetMemberProperties`.  
  
- Chiamata al metodo con `this` puntatore, ovvero usare `InvokeEx` con DISPATCH_METHOD.  
  
- Consenti browser che supportano il concetto di spazi dei nomi per ottenere l'elemento padre dello spazio del nome di un oggetto, ovvero usare `GetNameSpaceParent`.  
  
  Gli oggetti che supportano `IDispatchEx` potrebbe inoltre supportare `IDispatch` per garantire la compatibilità con le versioni precedenti. La natura dinamica degli oggetti che supportano `IDispatchEx` presenta alcune implicazioni per il `IDispatch` interfaccia di tali oggetti. Ad esempio, `IDispatch` presuppone seguenti:  
  
- Il membro e il parametro DISPID devono rimanere costanti per la durata dell'oggetto. In questo modo un client ottenere i DISPID una sola volta e memorizzarli nella cache per un uso successivo.  
  
  Poiché `IDispatchEx` consente l'aggiunta e l'eliminazione di membri, il set di DISPID valido non rimanere costante. Tuttavia, `IDispatchEx` richiede che il mapping tra nome membro e DISPID rimanere costante. Ciò significa che se un membro viene eliminato:  
  
- DISPID non può essere riutilizzato fino a quando non viene creato un membro con lo stesso nome.  
  
- DISPID deve rimanere valido per `GetNextDispID`.  
  
- DISPID deve essere accettato normalmente da uno qualsiasi dei `IDispatch` o `IDispatchEx` metodi, ovvero devono riconoscere il membro come eliminato e restituire un codice di errore appropriati (in genere DISP_E_MEMBERNOTFOUND o S_FALSE).  
  
## <a name="examples"></a>Esempi  
 Ciò [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] codice di test () la funzione esegue le operazioni seguenti:  
  
- Crea un nuovo oggetto chiamando il `Object` costruttore e assegna un puntatore al nuovo oggetto per la variabile oggetto.  
  
- Crea un nuovo elemento denominato Elem nell'oggetto e assegna a questo elemento di un puntatore per il team cat (funzione).  
  
- Chiama questa funzione. Poiché deve essere chiamato come un metodo, il `this` puntatore fa riferimento all'oggetto file obj. La funzione aggiunge un nuovo elemento, a barre, all'oggetto.  
  
  Il codice HTML completo è:  
  
```html
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 Un controllo inserito nella stessa pagina Web è stato possibile ottenere un puntatore dispatch per i motori di script dal browser. Il controllo è stato quindi implementare il test (funzione):  
  
```html
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 Dal controllo del codice, test, esegue la stessa operazione come la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funzione `test()`. Si noti che queste chiamate al dispatch si effettuano l'esecuzione [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] del motore e modificare lo stato del motore di:  
  
- Ottiene il puntatore dispatch per la funzione cat utilizzando `GetDispID()`.  
  
- Ottiene il puntatore dispatch all'oggetto funzione utilizzando `GetDispID()`.  
  
- Costruisce un oggetto chiamando la funzione dell'oggetto con `InvokeEx()` e ottiene un puntatore dispatch all'oggetto appena costruito.  
  
- Crea un nuovo elemento, Elem, usando l'oggetto `GetDispID()` con il `fdexNameEnsure` flag.  
  
- Inserisce il puntatore dispatch cat usando l'elemento `InvokeEx()`.  
  
- Chiama il puntatore dispatch al cat come metodo chiamando `InvokeEx()` e passando il puntatore dispatch all'oggetto costruito come il `this` puntatore.  
  
- Il metodo cat crea un nuovo elemento, barra, su corrente `this` oggetto.  
  
- Verifica che il nuovo elemento, a barre, è stato creato nell'oggetto costruito da enumerare gli elementi usando `GetNextDispID()`.  
  
  Il codice per il controllo di test:  
  
```cpp
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>Metodi  
 [Metodi IDispatchEx](../../winscript/reference/idispatchex-methods.md)