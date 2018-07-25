---
title: Gestione degli eventi di Windows Runtime in JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7e5780a2462e8980c22c474ae6236c87aee599b
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302811"
---
# <a name="handling-windows-runtime-events-in-javascript"></a>Gestione degli eventi di Windows Runtime in JavaScript
Gli eventi di Windows Runtime non sono rappresentati nello stesso modo in JavaScript rispetto a C++ o .NET Framework. Non sono proprietà di classi, ma sono piuttosto rappresentati come identificatori di stringa (in lettere minuscole) passati ai metodi `addEventListener` e `removeEventListener` della classe. Ad esempio, è possibile aggiungere un gestore dell'evento per l'evento [Geolocator.PositionChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) passando la stringa "positionchanged" al metodo `Geolocator.addEventListener`:  
  
```JavaScript  
var locator = new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 È anche possibile impostare la proprietà `locator.onpositionchanged`:  
  
```JavaScript  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
Un'altra differenza tra .NET o C++ e JavaScript è il numero di parametri usati da un gestore dell'evento. In .NET o C++ un gestore accetta due oggetti: mittente dell'evento e dati dell'evento. In JavaScript i due oggetti vengono aggregati come singolo oggetto `Event`. Nell'esempio seguente il parametro `ev` contiene sia il mittente dell'evento (la proprietà `target`), sia le proprietà dei dati dell'evento (in questo caso, solo `position`). Le proprietà dei dati dell'evento sono documentate per ogni evento.
  
```JavaScript  
function (ev) {  
    console.log("Sender: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
```  
  
> [!IMPORTANT]
>  Le funzionalità di Windows Runtime non sono disponibili per app eseguite in Internet Explorer.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di Windows Runtime in JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
