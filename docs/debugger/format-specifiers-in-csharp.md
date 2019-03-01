---
title: Nel debugger di identificatori di formato (C#) | Microsoft Docs
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4091aa8c312938a725a89e5ef131923671af3169
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698989"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Formattare gli identificatori in C# nel debugger di Visual Studio
È possibile modificare il formato in cui viene visualizzato il valore nella **Watch** finestra usando identificatori di formato. È anche possibile usare gli identificatori di formato nel **controllo immediato** finestra, il **comando** finestra, in [i punti di analisi](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)e nelle finestre di origine. Se posiziona su un'espressione in queste finestre, il risultato verrà visualizzato in una [suggerimento dati](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) nella sezione delle opzioni di formato specificato.

Per usare un identificatore di formato, immettere l'espressione variabile, seguito da una virgola e l'identificatore appropriato.

## <a name="set-format-specifiers"></a>Set di identificatori di formato
Si userà l'esempio di codice seguente:

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Aggiungere la `my_var1` variabile per il **Watch** finestra durante il debug **Debug** > **Windows** > **guarda**  >  **Espressione di controllo 1**. Successivamente, la variabile e scegliere **visualizzazione esadecimale**. A questo punto il **Watch** finestra Mostra il valore 0x0065. Per visualizzare questo valore come un intero decimale invece che intero esadecimale, aggiungere l'identificatore di formato decimale **, d** nel **nome** colonna dopo il nome della variabile. Il **valore** colonna Visualizza ora **101**.

![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")

## <a name="format-specifiers"></a>Identificatori di formato
La tabella seguente descrive il C# per il debugger di Visual Studio identificatori di formato.

|Identificatore|Formato|Valore dell'espressione di controllo originale|Visualizza|
|---------------|------------|--------------------------|--------------|
|ac|Forzare la valutazione di un'espressione che può essere utile quando la valutazione implicita di proprietà e chiamate di funzione implicite è disattivata.|Messaggio "La valutazione della funzione implicita è stata disattivata dall'utente"|\<valore>|
|d|intero decimale|0x0065|101|
|dynamic|Visualizza l'oggetto specificato usando una visualizzazione dinamica|Visualizza tutti i membri dell'oggetto, inclusa la visualizzazione dinamica|Visualizza solo la visualizzazione dinamica|
|h|intero esadecimale|61541|0x0000F065|
|nq|stringa senza virgolette|"Stringa"|Stringa|
|protocollo nSe|Specifica il comportamento, non di formato. Valuta l'espressione "Senza effetti collaterali". Se l'espressione non può essere interpretato e può essere risolti solo da una versione di valutazione (ad esempio, una chiamata di funzione), si verrà visualizzato un errore.|N/D|N/D|
|hidden|Visualizza tutti i membri pubblici e non pubblici|Visualizza i membri pubblici|Visualizza tutti i membri|
|raw|Visualizza l'elemento così come appare nel nodo degli elementi non elaborati. Valido unicamente sugli oggetti proxy.|Dizionario\<T >|Visualizzazione non elaborata di Dictionary\<T >|
|results|Utilizzato con una variabile di un tipo che implementa IEnumerable o IEnumerable\<T >, generalmente il risultato di un'espressione di query. Visualizza solo i membri che contengono il risultato della query.|Visualizza tutti i membri|Visualizza i membri che soddisfano le condizioni della query|

## <a name="see-also"></a>Vedere anche
- [Finestre Espressioni di controllo e Controllo immediato](../debugger/watch-and-quickwatch-windows.md)
- [Finestre Auto e Variabili locali](../debugger/autos-and-locals-windows.md)
