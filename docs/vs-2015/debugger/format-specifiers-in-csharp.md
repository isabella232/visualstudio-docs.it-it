---
title: Format Specifiers in c# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- CSharp
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
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3521f39227b5abcb51a4db6b61e6bf0d853e5afe
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2019
ms.locfileid: "59001260"
---
# <a name="format-specifiers-in-c"></a>Identificatori di formato in C# #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile modificare il formato con cui viene visualizzato il valore nella finestra **Espressioni di controllo** usando gli identificatori di formato. Gli identificatori di formato possono essere usati anche nella finestra **Immediata** , nella finestra **Comando** e persino nelle finestre di origine. Se in queste finestre ci si posiziona su un'espressione, il risultato verrà visualizzato in un suggerimento dati. I suggerimenti dati riflettono l'identificatore di formato nella visualizzazione Suggerimento dati.  
  
 Per usare un identificatore di formato, digitare l'espressione seguita da una virgola e dall'identificatore appropriato.  
  
## <a name="using-format-specifiers"></a>Uso degli identificatori di formato  
 Se si ha il codice seguente:  
  
```  
{  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Aggiungere la variabile `my_var1` alla finestra Espressioni di controllo (durante il debug: **Debug/Windows/Espressioni di controllo/Espressione di controllo 1**) e impostare la visualizzazione su esadecimale (nella finestra **Espressioni di controllo** fare clic con il pulsante destro del mouse sulla variabile e selezionare **Visualizzazione esadecimale**). La finestra **Espressioni di controllo** mostra il valore 0x0065. Per visualizzare questo valore espresso come intero decimale invece che intero esadecimale, aggiungere l'identificatore di formato decimale dopo la variabile del nome nella colonna Nome: **, d**. La colonna Valore visualizza il valore decimale 101  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Identificatori di formato  
 Nella tabella riportata di seguito sono elencati gli identificatori di formato C# riconosciuti dal debugger.  
  
|Identificatore|Formato|Valore dell'espressione di controllo originale|Visualizza|  
|---------------|------------|--------------------------|--------------|  
|ac|Impone la valutazione di un'espressione. Può risultare utile quando la valutazione implicita di proprietà e di chiamate di funzione implicite è disattivata. Vedere [Side Effects and Expressions](http://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).|Messaggio "La valutazione della funzione implicita è stata disattivata dall'utente"|\<valore>|  
|d|intero decimale|0x0065|101|  
|dynamic|Visualizza l'oggetto specificato usando una visualizzazione dinamica|Visualizza tutti i membri dell'oggetto, inclusa la visualizzazione dinamica|Visualizza solo la visualizzazione dinamica|  
|h|intero esadecimale|61541|0x0000F065|  
|nq|stringa senza virgolette|"Stringa"|Stringa|  
|hidden|Visualizza tutti i membri pubblici e non pubblici|Visualizza i membri pubblici|Visualizza tutti i membri|  
|raw|Visualizza l'elemento così come appare nel nodo degli elementi non elaborati. Valido unicamente sugli oggetti proxy.|Dizionario\<T >|Visualizzazione non elaborata di Dictionary\<T >|  
|results|Utilizzato con una variabile di un tipo che implementa IEnumerable o IEnumerable\<T >, generalmente il risultato di un'espressione di query. Visualizza solo i membri che contengono il risultato della query.|Visualizza tutti i membri.|Visualizza i membri che soddisfano le condizioni della query.|  
  
## <a name="see-also"></a>Vedere anche  
 [Finestre Espressioni di controllo e Controllo immediato](../debugger/watch-and-quickwatch-windows.md)   
 [Finestra delle variabili](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
