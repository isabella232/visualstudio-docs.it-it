---
title: Visualizzazione delle definizioni dei tipi
ms.date: 01/10/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code editor, view definition
- go to definition
- peek definition
- type definition [Visual Studio]
- member definition [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 95302b61da30cc2034edfe495a695efb510430d3
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269839"
---
# <a name="view-type-and-member-definitions"></a>Visualizzare le definizioni di tipi e membri

Gli sviluppatori devono spesso visualizzare le definizioni del codice sorgente per i tipi o i membri di classe che usano nel codice. In Visual Studio, le funzionalità **Vai a definizione** e **Visualizza definizione** consentono di visualizzare facilmente la definizione di un tipo o di un membro. Se il codice sorgente non è disponibile, vengono invece visualizzati i metadati.

## <a name="go-to-definition"></a>Vai a definizione

La funzionalità **Vai a definizione** consente di passare al sorgente di un tipo o di un membro e di aprire il risultato in una nuova scheda. Se si preferisce usare la tastiera, posizionare il cursore di testo in un punto qualsiasi all'interno del simbolo e premere **F12**. Se si preferisce usare il mouse, scegliere **Vai a definizione** dal menu di scelta rapida o usare la funzionalità **CTRL+clic** descritta nella sezione seguente.

### <a name="ctrl-click-go-to-definition"></a>Vai a definizione con Ctrl+clic

In Visual Studio 2017 versione 15.4, per gli utenti che preferiscono il mouse è più facile accedere rapidamente alla funzionalità **Vai a definizione**. Quando si preme **Ctrl** e si passa il puntatore del mouse su un tipo o su un membro, è possibile fare clic sui simboli. Per passare rapidamente alla definizione di un simbolo, premere **Ctrl** e quindi fare clic sul simbolo. È facile!

![Animazione di Vai a definizione con un clic del mouse](../ide/media/click_gotodef.gif)

È possibile cambiare il tasto di modifica per la funzionalità **Vai a definizione** con clic del mouse da **Strumenti** > **Opzioni** > **Editor di testo** > **Generale**. Selezionare quindi **ALT** o **CTRL + ALT** dall'elenco a discesa **Usa tasto di modifica**. È anche possibile disabilitare la funzionalità **Vai a definizione** con clic del mouse deselezionando la casella di controllo **Abilita clic del mouse per eseguire Vai a definizione**.

![Abilitazione del clic del mouse per Vai a definizione](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Visualizza definizione

La funzionalità **Visualizza definizione** consente di visualizzare in anteprima la definizione di un tipo senza abbandonare la posizione corrente nell'editor. Se si preferisce usare la tastiera, posizionare il cursore di testo in un punto qualsiasi all'interno del nome del tipo o del membro e premere **Alt+F12**. Se si preferisce usare il mouse, è possibile scegliere **Visualizza definizione** dal menu di scelta rapida. In Visual Studio 2017 15.4 e versioni successive è disponibile un nuovo modo per visualizzare in anteprima una definizione tramite il mouse. Per prima cosa, passare a **Strumenti** > **Opzioni** > **Editor di testo** > **Generale**. Selezionare l'opzione **Apri definizione in visualizzazione rapida** e fare clic su **OK** per chiudere la finestra di dialogo **Opzioni**.

![Impostazione dell'opzione Visualizza definizione con clic del mouse](../ide/media/editor_options_peek_view.png)

Premere quindi **Ctrl** (o il tasto di modifica selezionato in **Opzioni**) e fare clic sul tipo o sul membro.

![Animazione della funzionalità Visualizza definizione](../ide/media/peek_definition.gif)

Se viene visualizzata una definizione diversa da quella della finestra popup, è possibile seguire un percorso di navigazione usando i cerchi e le frecce visualizzati sopra la finestra popup.

Per altre informazioni, vedere [Procedura: Visualizzare e modificare il codice tramite la finestra Visualizza definizione (ALT+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Visualizzare i metadati come codice sorgente (C#)

Quando si visualizza la definizione di tipi o membri C# per i quali il codice sorgente non è disponibile, vengono visualizzati i relativi metadati. È possibile visualizzare le dichiarazioni di tipi e membri, ma non la relativa implementazione.

Quando si esegue il comando **Vai a definizione** o **Visualizza definizione** per un elemento il cui codice sorgente non è disponibile, nell'editor del codice viene visualizzato un documento a schede che contiene una visualizzazione dei metadati dell'elemento visualizzati come codice sorgente. Il nome del tipo, seguito da **[da metadati]**, viene visualizzato nella scheda del documento.

Ad esempio, se si esegue il comando **Vai a definizione** per <xref:System.Console>, i metadati per <xref:System.Console> vengono visualizzati nell'editor del codice come codice sorgente C#. Il codice corrisponde alla relativa dichiarazione, ma non mostra un'implementazione.

![Metadati come origine](../ide/media/metadatasource.png)

> [!NOTE]
> Quando si prova a eseguire il comando **Vai a definizione** o **Visualizza definizione** per i tipi o i membri contrassegnati come interni, Visual Studio non visualizza i metadati come codice sorgente, indipendentemente dal fatto che l'assembly di riferimento sia o meno un elemento friend.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Visualizzare le definizioni del codice sorgente decompilato invece dei metadati (C#)

Una novità di Visual Studio 2017 versione 15.6 consente di impostare un'opzione per visualizzare il codice sorgente decompilato quando si visualizza la definizione di un tipo o di un membro C# per il quale non è disponibile il codice sorgente. Per attivare questa funzionalità, scegliere **Strumenti** > **Opzioni** dalla barra dei menu. Espandere quindi **Editor di testo** > **C#** > **Avanzate** e selezionare **Enable navigation to decompiled sources** (Abilita navigazione a origini decompilate).

![Visualizzazione di una definizione decompilata](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio ricostruisce i corpi dei metodi tramite la decompilazione ILSpy. Al primo accesso a questa funzionalità, è necessario accettare una dichiarazione di non responsabilità relativa alla licenza del software e alle leggi su copyright e marchi.

## <a name="see-also"></a>Vedere anche

- [Spostarsi all'interno del codice](../ide/navigating-code.md)
- [Procedura: Visualizzare e modificare il codice tramite la finestra Visualizza definizione (ALT+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)