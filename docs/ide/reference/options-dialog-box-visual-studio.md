---
title: Finestra di dialogo Opzioni
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2b4b30607d5d0c677f7ef5e2401bc55c2398eb0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945581"
---
# <a name="options-dialog-box-visual-studio"></a>Finestra di dialogo Opzioni (Visual Studio)

La finestra di dialogo **Opzioni** consente di configurare l'ambiente di sviluppo integrato (IDE) in base alle proprie esigenze. Ad esempio, è possibile stabilire un percorso di salvataggio predefinito per i progetti, modificare l'aspetto e il comportamento predefiniti delle finestre e creare tasti di scelta rapida per i comandi di uso comune. Sono inoltre disponibili opzioni specifiche del linguaggio di sviluppo e della piattaforma. È possibile accedere alla finestra di dialogo **Opzioni** dal menu **Strumenti**.

## <a name="layout-of-the-options-dialog-box"></a>Layout della finestra di dialogo Opzioni

La finestra di dialogo **Opzioni** è suddivisa in due parti: un riquadro di spostamento a sinistra e un'area di visualizzazione a destra. Il controllo della struttura ad albero nel riquadro di spostamento include nodi di cartella, ad esempio Ambiente, Editor di testo, Progetti e soluzioni e Controllo del codice sorgente. Espandere un nodo di cartella per elencare le pagine di opzioni che contiene. Quando si seleziona il nodo per una pagina particolare, le relative opzioni appaiono nell'area di visualizzazione.

Le opzioni per una funzionalità IDE non appaiono nel riquadro di spostamento finché la funzionalità non viene caricata in memoria. Di conseguenza, è possibile che le opzioni visualizzate quando si inizia una nuova sessione non siano le stesse che apparivano quando si è chiusa l'ultima. Quando si crea un progetto o si esegue un comando che usa una determinata applicazione, i nodi per le relative opzioni vengono aggiunti alla finestra di dialogo Opzioni. Queste opzioni aggiunte rimarranno disponibili finché la funzionalità IDE rimane in memoria.

> [!NOTE]
> Alcune raccolte di impostazioni esaminano il numero di pagine visualizzate nel riquadro di spostamento della finestra di dialogo Opzioni. Per scegliere di visualizzare tutte le pagine possibili, selezionare **Mostra tutte le impostazioni**.

## <a name="how-options-are-applied"></a>Modalità di applicazione delle opzioni

Fare clic su OK nella finestra di dialogo **Opzioni** per salvare tutte le impostazioni in tutte le pagine. Fare clic su Annulla in qualsiasi pagina per annullare tutte le richieste di modifica, incluse quelle eseguite in altre pagine **Opzioni**. Alcune modifiche alle impostazioni delle opzioni, ad esempio quelle apportate in [Tipi di carattere e colori, Ambiente, finestra di dialogo Opzioni](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), avranno effetto solo quando si chiude e si riapre Visual Studio.

### <a name="show-all-settings"></a>Mostra tutte le impostazioni

Selezionando o deselezionando l'opzione **Mostra tutte le impostazioni** vengono applicate tutte le modifiche apportate nella finestra di dialogo **Opzioni**, anche se non si è ancora scelto **OK**.

## <a name="see-also"></a>Vedere anche

- [Personalizzazione dell'editor](../../ide/customizing-the-editor.md)