---
title: Riordina parametri Refactoring (c#) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 03316fba63267a4eb7fc3b59c8f6823d3678b438
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273104"
---
# <a name="reorder-parameters-refactoring-c"></a>Refactoring Riordina parametri (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` è un linguaggio Visual c# il refactoring di operazione che fornisce un modo semplice per modificare l'ordine dei parametri per metodi, indicizzatori e delegati. `Reorder Parameters` la dichiarazione viene modificata e in tutti i percorsi in cui viene chiamato il membro, i parametri vengono riorganizzati in modo da riflettere il nuovo ordine.  
  
 Per eseguire il `Reorder Parameters` operazione, posizionare il cursore sopra o accanto a un metodo, l'indicizzatore o delegato. Quando il cursore si trova nella posizione, richiamare il `Reorder Parameters` operazione premendo il tasto di scelta rapida oppure scegliendo il comando dal menu di scelta rapida.  
  
> [!NOTE]
>  Non è possibile riordinare il primo parametro in un metodo di estensione.  
  
### <a name="to-reorder-parameters"></a>Per riordinare i parametri  
  
1.  Creare una libreria di classi denominata `ReorderParameters`, quindi sostituire `Class1` con il codice di esempio seguente.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Posizionare il cursore sulla `MethodB`, nella dichiarazione del metodo o la chiamata al metodo.  
  
3.  Nel **refactoring** menu, fare clic su **Riordina parametri**.  
  
     Il **Riordina parametri** verrà visualizzata la finestra di dialogo.  
  
4.  Nel **Riordina parametri** finestra di dialogo `int i` nel **parametri** elenco e quindi fare clic sul pulsante a discesa.  
  
     In alternativa, è possibile trascinare `int i` dopo aver `bool b` nel **parametri** elenco.  
  
5.  Nel **Riordina parametri** finestra di dialogo, fare clic su **OK**.  
  
     Se il **Anteprima modifiche riferimento** opzione è selezionata nel **Riordina parametri** della finestra di dialogo il **Anteprima modifiche - Riordina parametri** verrà visualizzata la finestra di dialogo. Fornisce un'anteprima delle modifiche nell'elenco dei parametri per `MethodB` sia la firma e la chiamata al metodo.  
  
    1.  Se il **Anteprima modifiche - Riordina parametri** verrà visualizzata la finestra di dialogo, fare clic su **applica**.  
  
         In questo esempio, la dichiarazione del metodo e tutto il metodo di chiamata siti per `MethodB` vengono aggiornati.  
  
## <a name="remarks"></a>Note  
 È possibile riordinare i parametri da una dichiarazione di metodo o una chiamata al metodo. Posizionare il cursore sul o accanto la dichiarazione di metodo o delegato, ma non nel corpo.  
  
## <a name="see-also"></a>Vedere anche  
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)