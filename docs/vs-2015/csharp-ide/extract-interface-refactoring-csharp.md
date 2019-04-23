---
title: Estrai interfaccia Refactoring (c#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 55b24facd3a9ec935277a42c211a64d824ed6d7f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116745"
---
# <a name="extract-interface-refactoring-c"></a>Refactoring Estrai interfaccia (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Estrai interfaccia è un'operazione di refactoring che fornisce un modo semplice per creare una nuova interfaccia con i membri che hanno origine da una classe esistente, struct o interfaccia.  
  
 Quando i client diversi utilizzano lo stesso subset di membri di una classe, struct o interfaccia oppure quando più classi, struct o interfacce hanno un subset di membri in comune, può essere utile incarnare i subset di membri in un'interfaccia. Per altre informazioni sull'uso di interfacce, vedere [interfacce](http://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37).  
  
 Estrai interfaccia consente di generare un'interfaccia in un nuovo file e posiziona il cursore all'inizio del nuovo file. È possibile specificare i membri da estrarre nella nuova interfaccia, il nome della nuova interfaccia e il nome del file generato usando il **Estrai interfaccia** nella finestra di dialogo.  
  
### <a name="to-use-extract-interface"></a>Usare Estrai interfaccia  
  
1. Creare un'applicazione console denominata `ExtractInterface`, quindi sostituire `Program` con il codice seguente  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2. Con il cursore è posizionato in `MethodB`, fare clic su **Estrai interfaccia** sul **effettuare il refactoring** menu.  
  
     Il **Estrai interfaccia** verrà visualizzata la finestra di dialogo.  
  
     È anche possibile premere il tasto di scelta rapida CTRL + R, posso visualizzare la **Estrai interfaccia** nella finestra di dialogo.  
  
     È anche possibile fare doppio clic il mouse, scegliere **refactoring**e quindi fare clic su **Estrai interfaccia** per visualizzare il **Estrai interfaccia** nella finestra di dialogo.  
  
3. Fare clic su **Seleziona tutto**.  
  
4. Fare clic su **OK**.  
  
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
 Questa funzionalità è accessibile solo quando il cursore è posizionato in classe, struct o interfaccia che contiene i membri che si vuole estrarre. Quando il cursore si trova in questa posizione, richiamare l'operazione di refactoring Estrai interfaccia.  
  
 Quando si richiama Estrai interfaccia in una classe o uno struct, l'elenco di basi e interfacce viene modificato per includere il nome della nuova interfaccia. Quando si richiama Estrai interfaccia su un'interfaccia, non viene modificato l'elenco di basi e interfacce.  
  
## <a name="see-also"></a>Vedere anche  
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)