---
title: Comprimere ed espandere le aree di codice
description: Informazioni su come usare i comandi espandi e comprimi per lavorare in modalità struttura in Visual Studio
ms.custom: SEO-VS-2020
ms.date: 10/15/2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8fdd0a67bb561f3b339ad7d8f6743c51182fa74ab9fd33dbd6cb39a6bafcc4a7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121412829"
---
# <a name="outlining"></a>struttura

È possibile scegliere di nascondere il codice dalla visualizzazione comprimendo un'area di codice in modo che venga visualizzata sotto un segno più ( **+** ). Per espandere un'area compressa fare clic sul segno più. Se si è un utente della tastiera, è possibile scegliere **CTRL** + **M** + **per** comprimere ed espandere. È anche possibile comprimere un'area della struttura facendo doppio clic su qualsiasi riga nell'area a margine della struttura, che viene visualizzata a sinistra del codice. Il contenuto di un'area compressa può essere visualizzato come descrizione comando quando si passa il mouse sull'area compressa.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Editor standard (Visual Studio per Mac)](/visualstudio/mac/source-editor).

Le aree nel margine della struttura vengono evidenziate anche quando si passa il mouse sul margine. Il valore predefinito del colore dell'evidenziazione può sembrare piuttosto debole in alcune configurazioni di colore. È possibile modificarlo **in** Strumenti Opzioni Ambiente Tipi di  >    >    >  **carattere e colori**  >  **Area comprimibile**.

Quando si usa il codice di struttura, è possibile espandere le sezioni che si intende usare, comprimerle al termine delle operazioni e quindi passare ad altre sezioni. Quando non si vuole avere la struttura visualizzata, con il comando **Rimuovi struttura** è possibile rimuovere le informazioni sulla struttura senza alterare il codice sottostante.

I comandi **Annulla** e **Ripristina** nel menu **Modifica** hanno effetto su queste azioni. Le operazioni **Copia**, **Taglia**, **Incolla** e di trascinamento della selezione mantengono le informazioni relative alla struttura ma non lo stato dell'area comprimibile. Ad esempio, quando si copia un'area compressa, l'operazione **Incolla** incollerà il testo copiato come area espansa.

> [!CAUTION]
> Quando si modifica un'area della struttura, la struttura potrebbe andare persa. Ad esempio, le eliminazioni **o le operazioni** Trova e sostituisci possono cancellare la fine dell'area.

I comandi seguenti sono disponibili nel **sottomenu**  >  **Modifica struttura.**

|Nome|Descrizione|
|-|-|
|Nascondi selezione|(**CTRL+** + **M,** **CTRL** H : comprime un blocco di codice selezionato che normalmente non sarebbe disponibile per la struttura, ad esempio + un `if` blocco . Per rimuovere l'area personalizzata, usare **Visualizza selezione nascosta** (o **Ctrl**+**M**, **Ctrl**+**U**). Non disponibile in Visual Basic.|
|Espandi/comprimi struttura| (**CTRL+** + **M**, **CTRL** M : inverte lo stato nascosto o espanso corrente della sezione di struttura più interna quando il cursore si trova + in una sezione compressa annidata.|
|Attiva/disattiva tutta la struttura|(**CTRL+** + **M,** **CTRL** + **L**: imposta tutte le aree sullo stesso stato compresso o espanso. Se alcune aree sono espanse e altre compresse, quelle compresse vengono espanse.|
|Arresta struttura|(**CTRL+** + **M,** **CTRL** + **P**: rimuove tutte le informazioni di struttura per l'intero documento.|
|Visualizza selezione nascosta|(**CTRL+** + **M,** **CTRL** + **U**: rimuove le informazioni di struttura per l'area definita dall'utente attualmente selezionata. Non disponibile in Visual Basic.|
|Comprimi alle definizioni|(**CTRL+** + **M**, **CTRL** + **O**) - Comprime i membri di tutti i tipi.|
|Comprimi blocco:\<logical boundary>|(C++) Comprime un'area nella funzione contenente il punto di inserimento. Ad esempio, se il punto di inserimento si trova all'interno di un ciclo, il ciclo è nascosto.|
|Comprimi tutto in: \<logical structures>|(C++) Comprime tutte le strutture all'interno della funzione.|

È anche possibile usare Visual Studio SDK per definire le aree di testo che si intende espandere o comprimere. Vedere [Walkthrough: Outlining](../extensibility/walkthrough-outlining.md) (Procedura dettagliata: struttura).

## <a name="see-also"></a>Vedi anche

- [Funzionalità dell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)
- [Editor standard (Visual Studio per Mac)](/visualstudio/mac/source-editor)
