---
title: Cercare e sostituire testo
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7051b90dde45965b76e8a9e08b33b5326ff2848c
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106752"
---
# <a name="find-and-replace-text"></a>Cercare e sostituire testo

È possibile trovare e sostituire testo nell'editor di Visual Studio usando [Trova e sostituisci](#find-and-replace-control) oppure [Ricerca/sostituzione nei file](#find-in-files-and-replace-in-files).

> [!TIP]
> Se si stanno rinominando simboli del codice, ad esempio variabili e i metodi, è preferibile *[effettuarne il refactoring](../ide/reference/rename.md)* anziché usare la funzionalità di ricerca e sostituzione. Il refactoring è un'opzione avanzata in grado di rilevare l'ambito, mentre con la ricerca e sostituzione vengono sostituite indifferentemente tutte le istanze.

La funzionalità di ricerca e sostituzione è disponibile nell'editor, in alcune altre finestre basate su testo, ad esempio le finestre dei **risultati della ricerca**, nelle finestre di progettazione, ad esempio la finestra di progettazione XAML e quella di Progettazione Windows Form, e nelle finestre degli strumenti.

È possibile definire l'ambito di ricerca per il documento corrente, la soluzione corrente o un set di cartelle personalizzato. È inoltre possibile specificare un set di estensioni di nomi di file per le ricerche su più file. Personalizzare la sintassi di ricerca usando le [espressioni regolari](../ide/using-regular-expressions-in-visual-studio.md) .NET.

> [!TIP]
> La casella [Trova/Comando](../ide/find-command-box.md) è disponibile nella barra degli strumenti, ma non è visibile per impostazione predefinita. Per visualizzare la casella **Trova/Comando**, selezionare **Aggiungi o rimuovi pulsanti** nella barra degli strumenti **Standard** e quindi selezionare **Trova**.

## <a name="find-and-replace-control"></a>Controllo Trova e sostituisci

Il controllo **Trova e sostituisci** viene visualizzato nell'angolo superiore destro della finestra dell'editor di codice. Il controllo **Trova e sostituisci** evidenzia immediatamente tutte le occorrenze della stringa di ricerca specificata nel documento corrente. È possibile spostarsi da un'occorrenza all'altra scegliendo il pulsante **Trova successivo** o **Trova precedente** nel controllo di ricerca.

![Controllo Trova e sostituisci](media/find-and-replace-box.png)

È possibile accedere alle opzioni di sostituzione scegliendo il pulsante accanto alla casella di testo **Trova**. Per eseguire una sostituzione per volta, scegliere il pulsante **Sostituisci successivo** accanto alla casella di testo **Sostituisci** . Per sostituire tutte le corrispondenze, scegliere il pulsante **Sostituisci tutto**.

Per modificare il colore di evidenziazione per le corrispondenze, scegliere il menu **Strumenti**, selezionare **Opzioni**, quindi scegliere **Ambiente** e selezionare **Tipi di carattere e colori**. Nell'elenco **Show settings for** (Mostra impostazioni per), selezionare **Editor di testo**, quindi nell'elenco **Elementi visualizzati**, selezionare **Trova evidenziato (estensione)**.

### <a name="search-tool-windows"></a>Finestre degli strumenti di ricerca

È possibile usare il controllo **Trova** nelle finestre di codice o del testo, ad esempio le finestre **Output** e **Risultati ricerca**, selezionando **Modifica** > **Trova e sostituisci** o premendo **CTRL+F**.

Una versione del controllo di **ricerca** è disponibile anche in alcune finestre degli strumenti. Ad esempio, è possibile filtrare l'elenco di controlli nella finestra **Casella degli strumenti** immettendo il testo nella casella di ricerca. Tra le altre finestre degli strumenti che consentono di cercare il relativo contenuto sono incluse **Esplora soluzioni**, **Proprietà** e **Team Explorer**.

## <a name="find-in-files-and-replace-in-files"></a>Cerca nei file e Sostituisci nei file

**Find/Replace in Files** (Trova/Sostituisci nei file) funziona come il controllo **Trova e sostituisci**, con la differenza che è possibile definire un ambito per la ricerca. Non solo è possibile cercare il file aperto corrente nell'editor, ma anche tutti i documenti aperti, l'intera soluzione, il progetto corrente e gli insiemi di cartelle selezionati. È inoltre possibile eseguire la ricerca in base all'estensione del nome file. Per accedere alla finestra di dialogo **Cerca/Sostituisci nei file**, selezionare **Trova e sostituisci** dal menu **Modifica** o premere **CTRL+MAIUSC+F**.

![Cerca nei file (finestra di dialogo)](media/find-in-files-box.png)

### <a name="find-results"></a>Risultati ricerca

Quando si sceglie **Find All**  (Trova tutti), si apre una finestra **Risultati ricerca** che elenca le corrispondenze della ricerca. Selezionando un risultato nell'elenco viene visualizzato il file associato ed evidenziata la corrispondenza. Se il file non è già aperto per la modifica, viene aperto in una scheda di anteprima a destra della finestra scheda. È possibile utilizzare il controllo **Trova** per eseguire la ricerca nell'elenco dei **Risultati ricerca**.

### <a name="create-custom-search-folder-sets"></a>Creare set personalizzati di cartelle di ricerca

È possibile definire un ambito di ricerca scegliendo il pulsante **Seleziona cartelle di ricerca** (simile a **...** ) accanto alla casella **Cerca in**. Nella finestra di dialogo **Seleziona cartelle di ricerca**, è possibile specificare un set di cartelle in cui eseguire la ricerca nonché salvare la specifica in modo da poterla usare di nuovo in un secondo tempo.

> [!TIP]
> Se è stato eseguito il mapping dell'unità di un computer remoto nel computer locale, è possibile specificare cartelle in cui eseguire la ricerca nel computer remoto.

### <a name="create-custom-component-sets"></a>Creare set di componenti personalizzati

È possibile definire set di componenti nell'ambito di ricerca scegliendo il pulsante **Modifica insieme di componenti personalizzato** accanto alla casella **Cerca in**. È possibile specificare i componenti .NET o COM installati, i progetti Visual Studio che sono inclusi nella soluzione, o qualunque assembly o libreria dei tipi (*.dll*, *.tlb*, *.olb*, *.exe* o *.ocx*). Per individuare i riferimenti, selezionare la casella **Cerca in riferimenti**.

## <a name="see-also"></a>Vedere anche

- [Usare espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Refactoring del codice in Visual Studio](../ide/refactoring-in-visual-studio.md)