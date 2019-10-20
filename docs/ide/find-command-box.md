---
title: Casella Trova/Comando
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 024491180528dd4b8335c88623e7d261c0a2bbe2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653736"
---
# <a name="findcommand-box"></a>Trova/Comando (casella)

È possibile cercare testo ed eseguire i comandi di Visual Studio dalla casella **Trova/Comando**. La casella **Trova/Comando** è ancora disponibile nella barra degli strumenti, ma non è più visibile per impostazione predefinita. È possibile visualizzare la casella **Trova/Comando** scegliendo **Aggiungi o rimuovi pulsanti** nella barra degli strumenti **Standard** e scegliendo **Trova**.

Per eseguire un comando di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], anteporre il segno di maggiore di ( **>** ).

La casella **Trova/Comando** memorizza gli ultimi 20 elementi immessi e li visualizza in un elenco a discesa. È possibile spostarsi nell'elenco usando i **tasti di direzione**.

![Casella Trova&#47;Comando](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>Ricerca di testo

Per impostazione predefinita, quando si specifica il testo nella casella **Trova/Comando** e si preme il tasto **Invio**, Visual Studio esegue la ricerca nella finestra del documento o dello strumento corrente usando le opzioni specificate nella finestra di dialogo **Cerca nei file**. Per altre informazioni, vedere [Finding and Replacing Text](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Immissione di comandi

Per usare la casella **Trova/Comando** per eseguire un singolo comando o alias di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] invece che per cercare il testo, anteporre il comando con un simbolo di maggiore di ( **>** ). Esempio:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

In alternativa, è anche possibile usare la finestra di **comando** per immettere ed eseguire comandi singoli o multipli. Alcuni comandi o alias possono essere immessi ed eseguiti da soli, mentre altri richiedono l'immissione di argomenti nella sintassi. Per un elenco di comandi con argomenti, vedere [Comandi di Visual Studio](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Caratteri di escape

Un accento circonflesso ( **^** ) in un comando indica che il carattere immediatamente successivo viene interpretato letteralmente e non come carattere di controllo. In questo modo, è possibile incorporare virgolette diritte ( **"** ), spazi, barre iniziali, accenti circonflessi o qualsiasi altro carattere letterale nel valore di un parametro o di un'opzione, ad eccezione dei nomi di opzioni. Esempio:

```
>Edit.Find ^^t /regex
```

L'accento circonflesso presenta lo stesso funzionamento sia all'interno sia all'esterno delle virgolette. Se corrisponde all'ultimo carattere sulla riga, viene ignorato.

## <a name="see-also"></a>Vedere anche

- [Finestra di comando](../ide/reference/command-window.md)
- [Ricerca e sostituzione di testo](../ide/finding-and-replacing-text.md)