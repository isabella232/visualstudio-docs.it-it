---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-interface
title: Estrai interfaccia Refactoring (c#) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: e3e606a86f5989ca928e0b093b564f997f92a559
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="extract-interface-refactoring-c"></a>Refactoring Estrai interfaccia (C#)
Estrai interfaccia è un'operazione di refactoring che fornisce un modo semplice per creare una nuova interfaccia con membri che provengono da un'interfaccia, una struct o una classe esistente.  
  
 Quando i client diversi utilizzano lo stesso subset di membri di una classe, struct o interfaccia oppure quando più classi, strutture o interfacce sono un subset di membri in comune, può essere utile incorporare il sottoinsieme di membri in un'interfaccia. Per ulteriori informazioni sull'utilizzo delle interfacce, vedere [interfacce](/dotnet/csharp/programming-guide/interfaces/index).  
  
 Estrai interfaccia genera un'interfaccia in un nuovo file e posiziona il cursore all'inizio del nuovo file. È possibile specificare i membri da estrarre nella nuova interfaccia, il nome della nuova interfaccia e il nome del file generato tramite il **Estrai interfaccia** la finestra di dialogo.  
  
### <a name="to-use-extract-interface"></a>Per utilizzare Estrai interfaccia  
  
1.  Creare un'applicazione console denominata `ExtractInterface`, quindi sostituire `Program` con il codice seguente  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  Con il cursore posizionato `MethodB`, fare clic su **Estrai interfaccia** nel **refactoring** menu.  
  
     Il **Estrai interfaccia** viene visualizzata la finestra di dialogo.  
  
     È anche possibile premere il tasto di scelta rapida CTRL + R, I per visualizzare il **Estrai interfaccia** la finestra di dialogo.  
  
     È anche possibile fare doppio clic il mouse, scegliere **refactoring**, quindi fare clic su **Estrai interfaccia** per visualizzare il **Estrai interfaccia** la finestra di dialogo.  
  
3.  Fare clic su **Seleziona tutto**.  
  
4.  Fare clic su **OK**.  
  
     Vengono visualizzati il nuovo file, IProtoA.cs e il codice seguente:  
  
    ```csharp  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## <a name="remarks"></a>Note  
 Questa funzionalità è accessibile solo quando il cursore viene posizionato nella classe, struct o interfaccia che contiene i membri che si desidera estrarre. Quando il cursore si trova in questa posizione, richiamare l'operazione di refactoring Estrai interfaccia.  
  
 Quando si richiama Estrai interfaccia in una classe o uno struct, viene modificato l'elenco delle basi e interfacce per includere il nuovo nome di interfaccia. Quando si richiama Estrai interfaccia su un'interfaccia, l'elenco delle basi e le interfacce non viene modificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Refactoring (C#)](refactoring-csharp.md)