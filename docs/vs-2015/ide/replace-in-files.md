---
title: Sostituisci nei file | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 001f1faa969275788b10bc9bd1e6398373a54b37
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669965"
---
# <a name="replace-in-files"></a>Sostituisci nei file
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sostituisci nei file** consente di cercare una stringa o un'espressione nel codice di un determinato set di file e di modificare alcune o tutte le corrispondenze trovate. Le corrispondenze trovate e le azioni eseguite sono elencate nella finestra **Risultati ricerca** selezionata in **Opzioni risultati**.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 È possibile usare uno dei metodi seguenti per visualizzare l'opzione **Sostituisci nei file** nella finestra **Trova e sostituisci**.

### <a name="to-display-replace-in-files"></a>Per visualizzare l'opzione Sostituisci nei file

1. Nel menu **Modifica** espandere **Trova e sostituisci**.

2. Scegliere **Sostituisci nei file**.

     oppure

     Se la finestra **Trova e sostituisci** è già visualizzata, scegliere **Sostituisci nei file** nella barra degli strumenti.

## <a name="find-what"></a>Trova
 Per cercare una nuova stringa di testo o espressione, specificarla nella casella. Per cercare una delle 20 stringhe cercate più di recente, aprire l'elenco e scegliere la stringa che si vuole cercare. Scegliere il pulsante **Generatore di espressioni** adiacente se si vuole usare una o più espressioni regolari nella stringa di ricerca. Per altre informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="replace-with"></a>Sostituisci con
 Per sostituire istanze della stringa nella casella **Trova** con un'altra stringa, immettere la stringa di sostituzione nella casella **Sostituisci con**. Per eliminare le istanze della stringa nella casella **Trova**, lasciare vuoto questo campo. Aprire l'elenco per visualizzare le ultime 20 stringhe cercate. Scegliere il pulsante **Generatore di espressioni** adiacente se si vuole usare una o più espressioni regolari nella stringa di sostituzione. Per altre informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Cerca in
 L'opzione selezionata nell'elenco a discesa **Cerca in** determina se la funzionalità **Sostituisci nei file** deve cercare solo nei file attualmente attivi o in tutti i file archiviati all'interno di determinate cartelle. Selezionare un ambito di ricerca dall'elenco, digitare il percorso di una cartella o fare clic sul pulsante **Sfoglia (...)** per visualizzare la finestra di dialogo **Seleziona cartelle di ricerca** e immettere il set di cartelle per la ricerca. È anche possibile digitare un percorso direttamente nella casella **Cerca in**.

> [!NOTE]
> Se l'opzione **Cerca in** selezionata fa sì che venga cercato un file estratto dal controllo del codice sorgente, la ricerca verrà eseguita solo nella versione del file scaricata nel computer locale.

## <a name="find-options"></a>Opzioni ricerca
 È possibile espandere o comprimere la sezione **Opzioni di ricerca**. È possibile selezionare o deselezionare le opzioni seguenti:

 Maiuscole/minuscole se selezionato, nelle finestre **Risultati ricerca** verranno visualizzate solo le istanze della stringa **trova** corrispondenti sia per contenuto che per caso. Ad esempio, la ricerca di "MyObject" con l'opzione **Maiuscole/minuscole** selezionata restituisce "MyObject" ma non "myobject" o "MYOBJECT".

 Trova la corrispondenza con una parola intera quando è selezionata, nelle finestre **Risultati ricerca** verranno visualizzate solo le istanze della stringa di **ricerca** che corrispondono alle parole complete. Ad esempio, la ricerca di "MyObject" restituisce "MyObject" ma non "CMyObject" o "MyObjectC".

 Usa espressioni regolari quando questa casella di controllo è selezionata, è possibile usare notazioni speciali per definire modelli di testo nelle caselle di testo **trova** o **Sostituisci con** . Per un elenco di queste notazioni, vedere [Uso delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Esaminare questi tipi di file Questo elenco indica i tipi di file da cercare nelle directory **Cerca in** . Se questo campo è vuoto, la ricerca verrà eseguita in tutti i file nelle directory **Cerca in**.

 Selezionare qualsiasi voce dell'elenco per immettere una stringa di ricerca preconfigurata che troverà i file dei tipi specificati.

## <a name="result-options"></a>Opzioni risultati
 È possibile espandere o comprimere la sezione **Opzioni risultati**. È possibile selezionare o deselezionare le opzioni seguenti:

 Finestra Risultati ricerca 1 quando selezionata, i risultati della ricerca corrente sostituiranno il contenuto della finestra **Risultati ricerca 1** . Questa finestra viene visualizzata automaticamente per mostrare i risultati della ricerca. Per aprire questa finestra manualmente, scegliere **Altre finestre** dal menu **Visualizza** e quindi **Risultati ricerca 1**.

 Finestra Risultati ricerca 2 Se selezionata, i risultati della ricerca corrente sostituiranno il contenuto della finestra **Risultati ricerca 2** . Questa finestra viene visualizzata automaticamente per mostrare i risultati della ricerca. Per aprire questa finestra manualmente, scegliere **Altre finestre** dal menu **Visualizza** e quindi **Risultati ricerca 2**.

 Visualizza nomi file solo quando questa casella di controllo è selezionata, le finestre Risultati ricerca elencano i nomi completi e i percorsi per tutti i file che contengono la stringa di ricerca. Tuttavia, i risultati non includono la riga di codice in cui viene visualizzata la stringa. Questa casella di controllo è disponibile solo per la ricerca nei file.

 Mantieni i file modificati aperti dopo replace all se selezionato, lascia aperti tutti i file in cui sono state effettuate le sostituzioni, in modo che sia possibile annullare o salvare le modifiche. I vincoli di memoria potrebbero limitare il numero di file che possono rimanere aperti dopo un'operazione di sostituzione.

> [!CAUTION]
> È possibile usare **Annulla** solo nei file che restano aperti per la modifica. Se questa opzione non è selezionata, i file che non sono già aperti per la modifica restano chiusi e l'opzione **Annulla** non è disponibile per i file.

## <a name="see-also"></a>Vedere anche
 [Ricerca e sostituzione](../ide/finding-and-replacing-text.md) [di ricerca di testo nei file](../ide/find-in-files.md) [comandi di Visual Studio](../ide/reference/visual-studio-commands.md)
