---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: Riordina parametri Refactoring (c#) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.reorder
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 3a011794599bf1e56e905a40c6269b5639abadb2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="reorder-parameters-refactoring-c"></a>Refactoring Riordina parametri (C#)
`Reorder Parameters`è un Visual c# il refactoring di operazione che fornisce un modo semplice per modificare l'ordine dei parametri per metodi, gli indicizzatori e delegati. `Reorder Parameters`la dichiarazione, viene modificata e in tutti i percorsi in cui il membro viene chiamato, i parametri vengono riorganizzati in modo da riflettere il nuovo ordine.  
  
 Per eseguire il `Reorder Parameters` operazione, posizionare il cursore su o accanto a un metodo, l'indicizzatore o delegato. Quando il cursore si trova nella posizione, richiamare il `Reorder Parameters` operazione premendo il tasto di scelta rapida o scegliendo il comando dal menu di scelta rapida.  
  
> [!NOTE]
>  È possibile ridefinire il primo parametro di un metodo di estensione.  
  
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
  
2.  Posizionare il cursore su `MethodB`, nella dichiarazione di metodo o la chiamata al metodo.  
  
3.  Nel **refactoring** menu, fare clic su **Riordina parametri**.  
  
     Il **Riordina parametri** viene visualizzata la finestra di dialogo.  
  
4.  Nel **Riordina parametri** nella finestra di dialogo `int i` nel **parametri** elenco e quindi fare clic sul pulsante a discesa.  
  
     In alternativa, è possibile trascinare `int i` dopo `bool b` nel **parametri** elenco.  
  
5.  Nel **Riordina parametri** la finestra di dialogo, fare clic su **OK**.  
  
     Se il **Anteprima modifiche riferimento** opzione è selezionata nel **Riordina parametri** nella finestra di dialogo di **Anteprima modifiche - Riordina parametri** verrà visualizzata la finestra di dialogo. Fornisce un'anteprima delle modifiche nell'elenco di parametri per `MethodB` nella firma e la chiamata al metodo.  
  
    1.  Se il **Anteprima modifiche - Riordina parametri** viene visualizzata la finestra di dialogo, fare clic su **applica**.  
  
         In questo esempio, la dichiarazione di metodo e tutti il metodo di chiamata siti per `MethodB` vengono aggiornati.  
  
## <a name="remarks"></a>Note  
 È possibile riordinare i parametri da una dichiarazione di metodo o una chiamata al metodo. Posizionare il cursore su o accanto la dichiarazione di metodo o il delegato, ma non nel corpo.  
  
## <a name="see-also"></a>Vedere anche  
 [Refactoring (C#)](refactoring-csharp.md)