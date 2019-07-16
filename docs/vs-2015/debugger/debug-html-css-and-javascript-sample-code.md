---
title: Il debug del codice di esempio HTML, CSS e JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 51893967-98c8-4141-ba40-03646f221760
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 134b4e3c5195e9008d951062ec813a939d0d4fe6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68161464"
---
# <a name="debug-html-css-and-javascript-sample-code"></a>Debug del codice di esempio HTML, CSS e JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si applica a Windows e Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Il codice in questo argomento è il file di esempio per [Guida introduttiva: Debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md). Gli errori presenti nella guida introduttiva, in base alla progettazione, vengono corretti in questa versione del codice.  
  
## <a name="sample-code"></a>Codice di esempio  
 Il codice HTML seguente viene usato nel tag \<body> della guida introduttiva.  
  
```html  
<div id="flipTemplate" data-win-control="WinJS.Binding.Template"  
         style="display:none">  
    <div class="fixedItem" >  
        <img src="#" data-win-bind="src: flipImg" />  
    </div>  
</div>  
<div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{  
    itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">  
</div>  
```  
  
 Il CSS riportato di seguito mostra le aggiunte apportate a default.css.  
  
```css  
#fView {  
    background-color:#0094ff;  
    height: 500px;  
    margin: 25px;  
}  
```  
  
 Nell'esempio di codice seguente viene illustrato il codice JavaScript completo in default.js. I riferimenti agli spazi dei nomi WinJS necessari per questo codice si trovano nel file default.html del modello.  
  
```javascript  
(function () {  
    "use strict";  
  
    var app = WinJS.Application;  
    var activation = Windows.ApplicationModel.Activation;  
  
    var myData = [];  
    for (var x = 0; x < 4; x++) {  
        myData[x] = { flipImg: "/images/logo.png" }  
    };  
  
    var pages = new WinJS.Binding.List(myData, { proxy: true });  
  
    app.onactivated = function (args) {  
        if (args.detail.kind === activation.ActivationKind.launch) {  
            if (args.detail.previousExecutionState !==  
            activation.ApplicationExecutionState.terminated) {  
                // TODO: . . .  
            } else {  
                // TODO: . . .  
            }  
            args.setPromise(WinJS.UI.processAll());  
  
            updateImages();  
        }  
    };  
  
    function updateImages() {  
  
        pages.setAt(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
        pages.setAt(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
        pages.setAt(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    };  
  
    app.oncheckpoint = function (args) {  
    };  
  
    app.start();  
  
    var publicMembers = {  
        items: pages  
    };  
  
    WinJS.Namespace.define("Data", publicMembers);  
  
})();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio rapido: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)
