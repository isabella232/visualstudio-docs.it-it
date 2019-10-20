---
title: Refactoring Rimuovi parametri (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40c373c3575f007952143e29c8dfc2cfac3d080f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667485"
---
# <a name="remove-parameters-refactoring-c"></a>Refactoring Rimuovi parametri (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` è un'operazione di refactoring che fornisce un modo semplice per rimuovere i parametri da metodi, indicizzatori o delegati. Rimuovi parametri modifica la dichiarazione; in qualsiasi posizione in cui viene chiamato il membro, il parametro viene rimosso per riflettere la nuova dichiarazione.

 Per eseguire l'operazione di rimozione dei parametri, posizionare innanzitutto il cursore su un metodo, un indicizzatore o un delegato. Quando il cursore si trova in posizione, per richiamare l'operazione Rimuovi `Parameters`, fare clic sul menu **refactoring** , premere il tasto di scelta rapida oppure selezionare il comando dal menu di scelta rapida.

> [!NOTE]
> Non è possibile rimuovere il primo parametro in un metodo di estensione.

### <a name="to-remove-parameters"></a>Per rimuovere i parametri

1. Creare un'applicazione console denominata `RemoveParameters`, quindi sostituire `Program` con il codice seguente.

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

2. Posizionare il cursore sul metodo `A`, nella dichiarazione del metodo o nella chiamata al metodo.

3. Dal menu **refactoring** selezionare **Rimuovi parametri** per visualizzare la finestra di dialogo **Rimuovi parametri** .

     È anche possibile digitare il tasto di scelta rapida CTRL + R, V per visualizzare la finestra di dialogo **Rimuovi parametri** .

     È inoltre possibile fare clic con il pulsante destro del mouse sul cursore, scegliere **refactoring**, quindi fare clic su **Rimuovi parametri** per visualizzare la finestra di dialogo **Rimuovi parametri** .

4. Utilizzando il campo **parametri** , posizionare il cursore su `int i` e quindi fare clic su **Rimuovi**.

5. Fare clic su **OK**.

6. Nella finestra di dialogo **Anteprima modifiche-Rimuovi parametri** fare clic su **applica**.

## <a name="remarks"></a>Note
 È possibile rimuovere i parametri da una dichiarazione di metodo o da una chiamata al metodo. Posizionare il cursore nella dichiarazione del metodo o nel nome del delegato e richiamare Rimuovi parametri.

> [!CAUTION]
> Rimuovi parametri consente di rimuovere un parametro a cui si fa riferimento nel corpo del membro, ma non rimuove i riferimenti al parametro nel corpo del metodo. Questo può introdurre errori di compilazione nel codice. Tuttavia, è possibile usare la finestra di dialogo **Anteprima modifiche** per esaminare il codice prima di eseguire l'operazione di refactoring.

 Se un parametro da rimuovere viene modificato durante la chiamata a un metodo, la rimozione del parametro eliminerà anche la modifica. Ad esempio, se una chiamata al metodo viene modificata da

```csharp
MyMethod(param1++, param2);
```

 in

```csharp
MyMethod(param2);
```

 con l'operazione di refactoring, `param1` non verrà incrementato.

## <a name="see-also"></a>Vedere anche
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)