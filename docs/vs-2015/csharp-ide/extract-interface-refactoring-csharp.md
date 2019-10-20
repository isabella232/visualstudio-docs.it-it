---
title: Refactoring Estrai interfacciaC#() | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdcf281e1ace40d1d7cdac0be302810ea173581b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667557"
---
# <a name="extract-interface-refactoring-c"></a>Refactoring Estrai interfaccia (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Estrai interfaccia è un'operazione di refactoring che fornisce un modo semplice per creare una nuova interfaccia con membri che provengono da una classe, uno struct o un'interfaccia esistente.

 Quando più client utilizzano lo stesso subset di membri di una classe, uno struct o un'interfaccia oppure quando più classi, struct o interfacce hanno un subset di membri in comune, può essere utile incorporare il subset di membri in un'interfaccia. Per ulteriori informazioni sull'utilizzo delle interfacce, vedere [interfacce](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37).

 Estrai interfaccia genera un'interfaccia in un nuovo file e posiziona il cursore all'inizio del nuovo file. È possibile specificare i membri da estrarre nella nuova interfaccia, il nome della nuova interfaccia e il nome del file generato utilizzando la finestra di dialogo **Estrai interfaccia** .

### <a name="to-use-extract-interface"></a>Per utilizzare Estrai interfaccia

1. Creare un'applicazione console denominata `ExtractInterface`, quindi sostituire `Program` con il codice seguente

    ```csharp
    // Invoke Extract Interface on ProtoA.
    // Note:  the extracted interface will be created in a new file.
    class ProtoA
    {
        public void MethodB(string s) { }
    }
    ```

2. Con il cursore posizionato in `MethodB` e fare clic su **Estrai interfaccia** nel menu **refactoring** .

     Verrà visualizzata la finestra di dialogo **Estrai interfaccia** .

     È anche possibile digitare il tasto di scelta rapida CTRL + R per visualizzare la finestra di dialogo **Estrai interfaccia** .

     È anche possibile fare clic con il pulsante destro del mouse sul mouse, scegliere **refactoring**, quindi fare clic su **Estrai interfaccia** per visualizzare la finestra di dialogo **Estrai interfaccia** .

3. Fare clic su **Seleziona tutto**.

4. Fare clic su **OK**.

     Viene visualizzato il nuovo file, IProtoA.cs, e il codice seguente:

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
 Questa funzionalità è accessibile solo quando il cursore è posizionato in una classe, uno struct o un'interfaccia contenente i membri che si desidera estrarre. Quando il cursore si trova in questa posizione, richiamare l'operazione di refactoring Estrai interfaccia.

 Quando si richiama l'interfaccia Extract in una classe o in uno struct, l'elenco basi e interfacce viene modificato in modo da includere il nuovo nome dell'interfaccia. Quando si richiama l'interfaccia Extract su un'interfaccia, l'elenco basi e interfacce non viene modificato.

## <a name="see-also"></a>Vedere anche
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)