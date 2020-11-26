---
title: Frammenti di codice per R
description: I frammenti di codice per R in Visual Studio offrono collegamenti per inserire rapidamente blocchi di codice di lunghezza arbitraria. In questo modo non è necessario digitare più volte codice simile.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 31dfa975cea519d4d064856090a265b844f265f6
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189108"
---
# <a name="code-snippets-for-r"></a>Frammenti di codice per R

I frammenti di codice in Visual Studio offrono collegamenti per inserire rapidamente blocchi di codice di lunghezza arbitraria. In questo modo non è necessario digitare più volte un codice simile. R Tools per Visual Studio (RTVS) aggiunge decine di frammenti R utili alla raccolta di Visual Studio.

Per inserire un frammento di codice, digitare il nome abbreviato del frammento (IntelliSense fornito), quindi premere **Tab** per inserire.

Di seguito alcuni semplici esempi:

- Digitare `=` e premere TAB. RTVS si espande fino all'operatore di assegnazione `<-`.
- Digitare `>` e premere TAB. RTVS si espande fino all'operatore pipe `%>%`.

I frammenti di codice sono molto più che un semplice completamento di caratteri. Con frammento di codice per la lettura di un file con estensione csv con la funzione `read.csv`, ad esempio, non è più necessario dover ricordare i nomi dei parametri:

![Animazione dell'uso di un frammento di codice per inserire una chiamata a read.csv](media/code-snippet-expansion.gif)

In questo caso, durante la digitazione di `readc`, IntelliSense visualizza un elenco di completamento. Selezionando il completamento nell'elenco a discesa e premendo **Tab** `readc` e premendo nuovamente **Tab** si espande il frammento di codice. Per questo motivo, l'espansione del frammento equivale spesso a "digitare il frammento e premere TAB due volte". Nella maggior parte dei casi, la prima volta che si preme TAB si completa la selezione di IntelliSense e la seconda volta si attiva l'espansione.

Per visualizzare tutti i frammenti disponibili, aprire la finestra di dialogo **strumenti**  >  **Gestione frammenti di codice** (**CTRL** + **K**,**B**) e selezionare **R** per **lingua**. Espandere i gruppi e selezionare singoli frammenti per visualizzare una descrizione e il testo del collegamento:

![Finestra di dialogo dei frammenti di codice per R](media/code-snippet-dialog.png)

Per creare frammenti di codice personalizzati, attenersi alle istruzioni in [Procedura dettagliata: Creare un frammento di codice](../ide/walkthrough-creating-a-code-snippet.md). Un frammento di codice è in definitiva semplicemente un file XML. Il codice seguente, ad esempio, è il frammento di codice per l'operazione di pipe (collegamento `>`):

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

I file XML per tutti i frammenti di codice vengono installati con RTVS. Nel campo **Posizione** in **Gestione frammenti di codice** è specificato il percorso. È possibile individuarli anche nel codice sorgente di RTVS su GitHub in [src/Package/Impl/Snippets](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets).
