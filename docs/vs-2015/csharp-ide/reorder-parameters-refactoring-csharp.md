---
title: Refactoring Riordina parametri (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e39564fb108b63859620e2c4a650608cdf1e7e82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673137"
---
# <a name="reorder-parameters-refactoring-c"></a>Refactoring Riordina parametri (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` è un'operazione di refactoring di Visual C# che fornisce un modo semplice per modificare l'ordine dei parametri per metodi, indicizzatori e delegati. `Reorder Parameters` modifica la dichiarazione e in qualsiasi posizione in cui viene chiamato il membro, i parametri vengono ridisposti in modo da riflettere il nuovo ordine.

 Per eseguire l' `Reorder Parameters` operazione, posizionare il cursore su o accanto a un metodo, un indicizzatore o un delegato. Quando il cursore si trova nella posizione, richiamare l' `Reorder Parameters` operazione premendo il tasto di scelta rapida oppure facendo clic sul comando dal menu di scelta rapida.

> [!NOTE]
> Non è possibile riordinare il primo parametro in un metodo di estensione.

### <a name="to-reorder-parameters"></a>Per riordinare i parametri

1. Creare una libreria di classi denominata `ReorderParameters` , quindi sostituire `Class1` con il codice di esempio seguente.

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

2. Posizionare il cursore su `MethodB` , nella dichiarazione del metodo o nella chiamata al metodo.

3. Nel menu **refactoring** fare clic su **Riordina parametri**.

     Verrà visualizzata la finestra di dialogo **Riordina parametri** .

4. Nella finestra di dialogo **Riordina parametri** selezionare `int i` nell'elenco **parametri** , quindi fare clic sul pulsante in basso.

     In alternativa, è possibile trascinare `int i` after `bool b` nell'elenco **Parameters** .

5. Nella finestra di dialogo **Riordina parametri** fare clic su **OK**.

     Se l'opzione **Anteprima modifiche riferimenti** è selezionata nella finestra di dialogo **Riordina parametri** , verrà visualizzata la finestra di dialogo **Anteprima modifiche-Riordina parametri** . Fornisce un'anteprima delle modifiche nell'elenco di parametri per `MethodB` sia nella firma che nella chiamata al metodo.

    1. Se viene visualizzata la finestra di dialogo **Anteprima modifiche-Riordina parametri** , fare clic su **applica**.

         In questo esempio vengono aggiornate la dichiarazione del metodo e tutti i siti di chiamata al metodo per `MethodB` .

## <a name="remarks"></a>Osservazioni
 È possibile riordinare i parametri da una dichiarazione di metodo o da una chiamata al metodo. Posizionare il cursore su o accanto al metodo o alla dichiarazione del delegato, ma non nel corpo.

## <a name="see-also"></a>Vedere anche
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)