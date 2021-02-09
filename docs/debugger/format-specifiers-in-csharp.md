---
title: Identificatori di formato nel debugger (C#) | Microsoft Docs
description: Usare un identificatore di formato per modificare il formato di visualizzazione di un valore nel finestra Espressioni di controllo. Questo articolo fornisce i dettagli di utilizzo.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: abc824cf5d0413f01ad5f3f4423b974aeca40b03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870584"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Identificatori di formato in C# nel debugger di Visual Studio
È possibile modificare il formato in cui un valore viene visualizzato nella finestra **espressioni di controllo** usando gli identificatori di formato. È anche possibile usare gli identificatori di formato nella finestra di **controllo immediato** , nella finestra di **comando** , in [punti](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)e nelle finestre di origine. Se si sospende un'espressione in queste finestre, il risultato verrà visualizzato in un  [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) nella visualizzazione del formato specificato.

Per usare un identificatore di formato, immettere l'espressione della variabile seguita da una virgola e dall'identificatore appropriato.

## <a name="set-format-specifiers"></a>Imposta identificatori di formato
Verrà usato il codice di esempio seguente:

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Aggiungere la `my_var1` variabile alla finestra **espressioni di controllo** durante il debug, **eseguire il debug** di  >  **Windows**  >  **Watch**  >  **Watch 1**. Fare quindi clic con il pulsante destro del mouse sulla variabile e scegliere **visualizzazione esadecimale**. A questo punto la finestra **espressioni di controllo** Mostra il valore 0x0065. Per visualizzare questo valore come intero decimale anziché come intero esadecimale, aggiungere l'identificatore di formato decimale **, d** nella colonna **nome** dopo il nome della variabile. La colonna **valore** ora Visualizza **101**.

![Screenshot di Visual Studio finestra Espressioni di controllo con una riga che mostra my_var1, d con un valore di 101 e un tipo di int.](../debugger/media/watchformatcsharp.png)

::: moniker range=">= vs-2019" 

È possibile visualizzare e selezionare da un elenco di identificatori di formato disponibili aggiungendo una virgola (,) al valore nella finestra **espressioni di controllo** . 

![FormatSpecCSharp](../debugger/media/vs-2019/format-specs-csharp.png "FormatSpecCSharp")

::: moniker-end

## <a name="format-specifiers"></a>Identificatori di formato
La tabella seguente descrive gli identificatori di formato C# per il debugger di Visual Studio.

|Identificatore|Formato|Valore dell'espressione di controllo originale|Visualizza|
|---------------|------------|--------------------------|--------------|
|ac|Forza la valutazione di un'espressione, che può essere utile quando la valutazione implicita delle proprietà e delle chiamate di funzione implicite è disattivata.|Messaggio "La valutazione della funzione implicita è stata disattivata dall'utente"|\<value>|
|d|intero decimale|0x0065|101|
|dinamico|Visualizza l'oggetto specificato usando una visualizzazione dinamica|Visualizza tutti i membri dell'oggetto, inclusa la visualizzazione dinamica|Visualizza solo la visualizzazione dinamica|
|h|intero esadecimale|61541|0x0000F065|
|nq|stringa senza virgolette|"Stringa"|Stringa|
|NSE|Specifica il comportamento, non il formato. Valuta l'espressione con "nessun effetto collaterale". Se l'espressione non può essere interpretata e può essere risolta solo da una valutazione, ad esempio una chiamata di funzione, verrà visualizzato un errore.|N/D|N/D|
|hidden|Visualizza tutti i membri pubblici e non pubblici|Visualizza i membri pubblici|Visualizza tutti i membri|
|raw|Visualizza l'elemento così come appare nel nodo degli elementi non elaborati. Valido unicamente sugli oggetti proxy.|Dizionario\<T>|Visualizzazione non elaborata del dizionario\<T>|
|results|Utilizzato con una variabile di un tipo che implementa IEnumerable o IEnumerable \<T> , in genere il risultato di un'espressione di query. Visualizza solo i membri che contengono il risultato della query.|Visualizza tutti i membri|Visualizza i membri che soddisfano le condizioni della query|

## <a name="see-also"></a>Vedi anche
- [Finestre espressioni di controllo e controllo immediato](../debugger/watch-and-quickwatch-windows.md)
- [Finestre auto e variabili locali](../debugger/autos-and-locals-windows.md)
