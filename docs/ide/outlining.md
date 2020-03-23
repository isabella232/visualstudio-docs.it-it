---
title: Comprimere ed espandere le aree di codice
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 781c9a6bc30f7d3a29bcb89e743600e6b29e6445
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585756"
---
# <a name="outlining"></a>Struttura

È possibile scegliere di nascondere il codice dalla visualizzazione comprimendo un'area**+** di codice in modo che venga visualizzato sotto un segno più ( ). Per espandere un'area compressa fare clic sul segno più. Se sei un utente della tastiera, puoi scegliere **Ctrl**+**M**+**M** per comprimere ed espandere. È anche possibile comprimere un'area della struttura facendo doppio clic su qualsiasi riga nell'area a margine della struttura, che viene visualizzata a sinistra del codice. Il contenuto di un'area compressa può essere visualizzato come descrizione comando quando si passa il mouse sull'area compressa.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Editor standard (Visual Studio per Mac)](/visualstudio/mac/source-editor).

Le aree nel margine della struttura vengono evidenziate anche quando si passa il mouse sul margine. Il valore predefinito del colore dell'evidenziazione può sembrare piuttosto debole in alcune configurazioni di colore. È possibile modificarlo in **Opzioni di strumenti** > **Opzioni** > **di ambiente** > **Tipi di carattere e colori** > **area di colori.**

Quando si usa il codice di struttura, è possibile espandere le sezioni che si intende usare, comprimerle al termine delle operazioni e quindi passare ad altre sezioni. Quando non si vuole avere la struttura visualizzata, con il comando **Rimuovi struttura** è possibile rimuovere le informazioni sulla struttura senza alterare il codice sottostante.

I comandi **Annulla** e **Ripristina** nel menu **Modifica** hanno effetto su queste azioni. Le operazioni **Copia**, **Taglia**, **Incolla** e di trascinamento della selezione mantengono le informazioni relative alla struttura ma non lo stato dell'area comprimibile. Ad esempio, quando si copia un'area compressa, l'operazione **Incolla** incollerà il testo copiato come area espansa.

> [!CAUTION]
> Quando si modifica un'area della struttura, la struttura potrebbe andare persa. Ad esempio, le operazioni di eliminazione o Trova e Sostituisci potrebbero cancellare la parte finale dell'area.

I seguenti comandi sono disponibili nel sottomenu **Modifica** > **struttura.**

|||
|-|-|
|Nascondi selezione|(**Ctrl**+**M**, **Ctrl**+**H**) - Comprime un blocco di codice selezionato `if` che normalmente non sarebbe disponibile per la struttura, ad esempio un blocco. Per rimuovere l'area personalizzata, usare **Visualizza selezione nascosta** (o **Ctrl**+**M**, **Ctrl**+**U**). Non disponibile in Visual Basic.|
|Espandi/comprimi struttura|- Consente di invertire lo stato nascosto o espanso corrente della sezione di struttura più interna quando il cursore si trova in una sezione compressa nidificata.|
|Attiva/disattiva tutta la struttura|(**Ctrl**+**M**, **Ctrl**+**L**) - Imposta tutte le regioni sullo stesso stato compresso o espanso. Se alcune aree sono espanse e altre compresse, quelle compresse vengono espanse.|
|Arresta struttura|(**Ctrl**+**M**, **Ctrl**+**P**) - Rimuove tutte le informazioni di struttura per l'intero documento.|
|Visualizza selezione nascosta|(**Ctrl**+**M**, **Ctrl**+**U**) - Rimuove le informazioni di struttura per l'area definita dall'utente attualmente selezionata. Non disponibile in Visual Basic.|
|Comprimi alle definizioni|(**Ctrl**+**M**, **Ctrl**+**O**) - Comprime i membri di tutti i tipi.|
|Comprimi blocco:\<limite logico>|(C)) Comprime un'area della funzione contenente il punto di inserimento. Ad esempio, se il punto di inserimento si trova all'interno di un ciclo, il ciclo è nascosto.|
|Comprimi tutto in:\<strutture logiche>|(C)) Comprime tutte le strutture all'interno della funzione.|

È anche possibile usare Visual Studio SDK per definire le aree di testo che si intende espandere o comprimere. Vedere [Walkthrough: Outlining](../extensibility/walkthrough-outlining.md) (Procedura dettagliata: struttura).

## <a name="see-also"></a>Vedere anche

- [Funzionalità dell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)
- [Editor standard (Visual Studio per Mac)](/visualstudio/mac/source-editor)
