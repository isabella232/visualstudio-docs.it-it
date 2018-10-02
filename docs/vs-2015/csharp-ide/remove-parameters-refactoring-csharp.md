---
title: Rimuovere i parametri di Refactoring (c#) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.remove
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 529950d72ac11ebfd443a85db597adfcbc89bba1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530823"
---
# <a name="remove-parameters-refactoring-c"></a>Refactoring Rimuovi parametri (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` è un'operazione di refactoring che fornisce un modo semplice per rimuovere i parametri da metodi, indicizzatori o delegati. Rimuovere la dichiarazione; le modifiche di parametri in tutti i percorsi in cui il membro viene chiamato, viene rimosso il parametro in modo da riflettere la dichiarazione di nuovi.  
  
 Eseguire l'operazione di Rimuovi parametri, posizionare il cursore su un metodo, l'indicizzatore o delegato. Mentre il cursore si trova nella posizione, per richiamare il metodo Remove `Parameters` operazione, scegliere il **effettuare il refactoring** menu, premere il tasto di scelta rapida o selezionare il comando dal menu di scelta rapida.  
  
> [!NOTE]
>  È possibile rimuovere il primo parametro in un metodo di estensione.  
  
### <a name="to-remove-parameters"></a>Per rimuovere i parametri  
  
1.  Creare un'applicazione console denominata `RemoveParameters`, quindi sostituire `Program` con il codice seguente.  
  
    ```csharp  
    class A  
    {  
        // Invoke on 'A'.  
        public A(string s, int i) { }  
    }  
  
    class B  
    {  
        void C()  
        {  
            // Invoke on 'A'.  
            A a = new A("a", 2);  
        }  
    }  
    ```  
  
2.  Posizionare il cursore sul metodo `A`, nella dichiarazione del metodo o la chiamata al metodo.  
  
3.  Dal **refactoring** dal menu **Rimuovi parametri** per visualizzare il **Rimuovi parametri** nella finestra di dialogo.  
  
     È anche possibile premere il tasto di scelta rapida CTRL + R, V per visualizzare il **Rimuovi parametri** nella finestra di dialogo.  
  
     È anche possibile fare doppio clic sul cursore, scegliere **refactoring**e quindi fare clic su **Rimuovi parametri** per visualizzare il **Rimuovi parametri** nella finestra di dialogo.  
  
4.  Usando il **parametri** campo, posizionare il cursore sulla `int i`, quindi fare clic su **rimuovere**.  
  
5.  Fare clic su **OK**.  
  
6.  Nel **Anteprima modifiche: Rimuovi parametri** finestra di dialogo, fare clic su **applica**.  
  
## <a name="remarks"></a>Note  
 È possibile rimuovere i parametri da una dichiarazione di metodo o una chiamata al metodo. Posizionare il cursore nel nome del delegato o dichiarazione di metodo e rimuovere parametri di richiamo.  
  
> [!CAUTION]
>  Rimuovi parametri consente di rimuovere un parametro di cui viene fatto riferimento nel corpo del membro, ma non rimuove i riferimenti al parametro nel corpo del metodo. Ciò può introdurre errori di compilazione nel codice. Tuttavia, è possibile usare la **Anteprima modifiche** finestra di dialogo per esaminare il codice prima di eseguire l'operazione di refactoring.  
  
 Se viene modificato un parametro che viene rimosso durante la chiamata a un metodo, la rimozione del parametro rimuoverà anche la modifica. Ad esempio, se una chiamata al metodo viene modificata da  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 in  
  
```csharp  
MyMethod(param2);  
```  
  
 per l'operazione di refactoring, `param1` non verrà incrementato.  
  
## <a name="see-also"></a>Vedere anche  
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)