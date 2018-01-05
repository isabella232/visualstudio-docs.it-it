---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: Rimuovere i parametri di Refactoring (c#) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.remove
dev_langs: CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 549914476db028cc5135de3c954ac841ab2da628
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="remove-parameters-refactoring-c"></a>Refactoring Rimuovi parametri (C#)
`Remove Parameters`è un'operazione di refactoring che fornisce un modo semplice per rimuovere i parametri da metodi, indicizzatori o delegati. Rimuovere le modifiche di parametri di dichiarazione. in tutti i percorsi in cui il membro viene chiamato, il parametro viene rimosso per riflettere la nuova dichiarazione.  
  
 Eseguire l'operazione Rimuovi parametri posizionando il cursore su un metodo, l'indicizzatore o delegato. Mentre il cursore si trova nella posizione, per richiamare il metodo Remove `Parameters` operazione, fare clic su di **refactoring** menu, premere il tasto di scelta rapida o selezionare il comando dal menu di scelta rapida.  
  
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
  
2.  Posizionare il cursore nel metodo `A`, nella dichiarazione di metodo o la chiamata al metodo.  
  
3.  Dal **refactoring** dal menu **Rimuovi parametri** per visualizzare il **Rimuovi parametri** la finestra di dialogo.  
  
     È anche possibile premere il tasto di scelta rapida CTRL + R, V per visualizzare il **Rimuovi parametri** la finestra di dialogo.  
  
     È anche possibile fare doppio clic sul cursore, scegliere **effettuare il refactoring**, quindi fare clic su **Rimuovi parametri** per visualizzare il **Rimuovi parametri** la finestra di dialogo.  
  
4.  Utilizzando il **parametri** campo, posizionare il cursore sulla `int i`, quindi fare clic su **rimuovere**.  
  
5.  Fare clic su **OK**.  
  
6.  Nel **Anteprima modifiche-Rimuovi parametri** la finestra di dialogo, fare clic su **applica**.  
  
## <a name="remarks"></a>Note  
 È possibile rimuovere i parametri da una dichiarazione di metodo o una chiamata al metodo. Posizionare il cursore nel nome del delegato o dichiarazione di metodo e richiamare Rimuovi parametri.  
  
> [!CAUTION]
>  Rimuovi parametri consente di rimuovere un parametro a cui fa riferimento nel corpo del membro, ma non rimuovere i riferimenti a tale parametro nel corpo del metodo. Questo può introdurre errori di compilazione nel codice. Tuttavia, è possibile utilizzare il **Anteprima modifiche** la finestra di dialogo per esaminare il codice prima di eseguire l'operazione di refactoring.  
  
 Se il parametro da rimuovere viene modificato durante la chiamata a un metodo, la rimozione del parametro rimuoverà anche la modifica. Ad esempio, se una chiamata al metodo viene modificata da  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 in  
  
```csharp  
MyMethod(param2);  
```  
  
 per l'operazione di refactoring, `param1` non verrà incrementato.  
  
## <a name="see-also"></a>Vedere anche  
 [Refactoring (C#)](refactoring-csharp.md)