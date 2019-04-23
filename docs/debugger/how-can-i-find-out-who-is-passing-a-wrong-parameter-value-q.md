---
title: Individuare chi passa un valore di parametro errato | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 548851a4e5811864e60d3a14368d6380f14f9e7e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089393"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Come è possibile individuare chi passa un valore di parametro errato?
## <a name="problem-description"></a>Descrizione del problema
 Il valore di parametro errato è stato passato a una delle funzioni utilizzate. Questa funzione viene chiamata da numerosissime posizioni. Come è possibile capire quale elemento passa il valore errato?

## <a name="solution"></a>Soluzione

#### <a name="to-resolve-this-problem"></a>Per risolvere questo problema

1. Impostare un punto di interruzione del percorso all'inizio della funzione.

2. Fare clic con il pulsante destro del mouse sul punto di interruzione e scegliere **Condizione**.

3. Nella finestra di dialogo **Condizione punto di interruzione** selezionare la casella di controllo **Condizione**. Visualizzare [punti di interruzione avanzati](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

4. Nella casella di testo immettere un'espressione, ad esempio `Var==3`, in cui `Var` è il nome del parametro che contiene il valore errato e `3` il valore errato passato.

5. Selezionare il pulsante di opzione **è true**, quindi scegliere **OK**.

6. Eseguire nuovamente il programma. Il punto di interruzione causa l'arresto del programma all'inizio della funzione, quando il parametro `Var` ha valore `3`.

7. Utilizzare la finestra Stack di chiamate per individuare la funzione chiamante e passare al relativo codice sorgente. Per altre informazioni, vedere [Procedura: Usare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).

## <a name="see-also"></a>Vedere anche
- [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)
- [Punti di interruzione](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)
- [Debug del codice nativo](../debugger/debugging-native-code.md)