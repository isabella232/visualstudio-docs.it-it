---
title: Uso del metodo bind (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bind method [JavaScript]
- this object [JavaScript]
ms.assetid: f608f95b-3b9d-437a-a67a-5a4ef8f6c07f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c49f6e8c5606845f41cc947029ac9405f97665f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="using-the-bind-method-javascript"></a>Utilizzo del metodo bind (JavaScript)
Il metodo JavaScript `bind` può essere utilizzato in modi diversi. In genere, viene utilizzato per mantenere il contesto di esecuzione per una funzione in esecuzione in un altro contesto. `bind` crea una nuova funzione con lo stesso corpo della funzione originale. Il primo argomento passato a `bind` specifica il valore della parola chiave `this` nella funzione associata. È inoltre possibile passare argomenti aggiuntivi facoltativi a `bind`. Per esempi di altri utilizzi, vedere [Metodo bind (Function)](../../javascript/reference/bind-method-function-javascript.md). Per un esempio sull'uso di `bind` per applicare funzioni in modo parziale, vedere [Modelli e suggerimenti sulla programmazione asincrona in JavaScript per Hilo (Windows Store)](http://msdn.microsoft.com/library/windows/apps/jj649740.aspx).  
  
## <a name="preserving-the-execution-context-using-bind"></a>Mantenere il contesto di esecuzione utilizzando bind  
 La funzione `bind` viene spesso utilizzata quando si aggiungono listener di eventi. Nell'esempio di codice seguente `bind` viene utilizzato per mantenere il contesto dell'oggetto corrente (`DataObject`). L'oggetto dati viene passato a `bind` utilizzando la parola chiave `this` che fornisce l'accesso a proprietà e funzioni dell'oggetto dati quando il gestore eventi (`dataReadyHandler`) viene eseguito. Per illustrare il funzionamento di `bind`, questo codice crea un evento personalizzato.  
  
```JavaScript  
var data;  
  
var dataReadyEvent = document.createEvent("Event");  
dataReadyEvent.initEvent("dataReady", true, false);  
  
function DataObject() {  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReadyHandler;  
    document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
    // To see the result of not using bind, comment out the preceding line,   
    // and uncomment the following line of code.  
    // document.addEventListener('dataReady', this.onDataCompleted);  
}  
function dataReadyHandler() {  
    if (console && console.log) {  
        console.log("Data object property value: " + this.name);  
        console.log("Data object property value: " + this.data());  
    }  
}  
  
setTimeout(function () {  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
    }, 5000);  
}  
  
var dataObj = new DataObject();  
  
// Output:  
// Data Object  
// 0,1,2,3  
  
```  
  
 Se si commenta la riga di codice che utilizza `bind`, si rimuove il commento dalla riga di codice che chiama `addEventListener` senza `bind`, quindi si riesegue il codice, la funzione `dataReadyHandler` avrà esito negativo. In `dataReadyHander`, ad esempio, `this.name` non sarà definito e `this.data()` restituirà un errore perché l'oggetto `this` non fa più riferimento all'oggetto dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo bind (Function)](../../javascript/reference/bind-method-function-javascript.md)