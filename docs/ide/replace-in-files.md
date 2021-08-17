---
title: Trova e sostituisci nei file
description: Informazioni sulla funzionalità Sostituisci nei file e su come consente di cercare una stringa o un'espressione nel codice di un set specificato di file e modificare alcune o tutte le corrispondenze trovate.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- find and replace
- replace in files
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 614757f7a4d6fde6d4df113d3b933d7e4b6d5a9b9f0a83ff88c5f450a35139dd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121232224"
---
# <a name="replace-in-files"></a>Sostituisci nei file

**Sostituisci nei file** consente di cercare una stringa o un'espressione nel codice di un determinato set di file e di modificare alcune o tutte le corrispondenze trovate. Le corrispondenze trovate e le azioni eseguite sono elencate nella **finestra Risultati** ricerca selezionata in **Opzioni risultato**.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti **nella** Guida a seconda delle impostazioni attive o dell'edizione. Per modificare le impostazioni, ad esempio per implementare le impostazioni **Generali** o **Visual C++**, scegliere **Strumenti** > **Importa/Esporta impostazioni** e quindi scegliere **Reimposta tutte le impostazioni**.

È possibile usare uno dei metodi seguenti per visualizzare l'opzione **Sostituisci nei file** nella finestra **Trova e sostituisci**.

## <a name="to-display-replace-in-files"></a>Per visualizzare l'opzione Sostituisci nei file

1. Nel menu **Modifica** espandere **Trova e sostituisci**.

2. Scegliere **Sostituisci nei file**.

   - o -

   Se la finestra **Trova e sostituisci** è già visualizzata, scegliere **Sostituisci nei file** nella barra degli strumenti.

## <a name="find-what"></a>Trova

Per cercare una nuova stringa di testo o espressione, specificarla nella casella. Per cercare una delle 20 stringhe cercate più di recente, aprire l'elenco a discesa e scegliere una stringa. Scegliere il pulsante **Generatore di espressioni** adiacente se si vuole usare una o più espressioni regolari nella stringa di ricerca. Per altre informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> Il pulsante **Generatore di espressioni** viene abilitato solo se è stata selezionata l'opzione **Usa espressioni regolari** in **Opzioni di ricerca**.

## <a name="replace-with"></a>Sostituire con

Per sostituire istanze della stringa nella casella **Trova** con un'altra stringa, immettere la stringa di sostituzione nella casella **Sostituisci con**. Per eliminare le istanze della stringa nella casella **Trova**, lasciare vuoto questo campo. Aprire l'elenco per visualizzare le ultime 20 stringhe cercate. Scegliere il pulsante **Generatore di espressioni** adiacente se si vuole usare una o più espressioni regolari nella stringa di sostituzione. Per altre informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Cerca in

L'opzione selezionata nell'elenco a discesa **Cerca in** determina se la funzione **Sostituisci nei file** eseguirà la ricerca solo nei file attualmente attivi oppure in tutti i file archiviati all'interno di determinate cartelle. Selezionare un ambito di ricerca dall'elenco, digitare il percorso di una cartella o fare clic sul pulsante **Sfoglia (...)** per visualizzare la finestra di dialogo **Seleziona cartelle di ricerca** e immettere il set di cartelle per la ricerca. È anche possibile digitare un percorso direttamente nella casella **Cerca in**.

> [!NOTE]
> Se l'opzione **Cerca in** selezionata fa sì che venga cercato un file estratto dal controllo del codice sorgente, la ricerca verrà eseguita solo nella versione del file scaricata nel computer locale.

## <a name="find-options"></a>Opzioni ricerca

È possibile espandere o comprimere la **sezione Opzioni di** ricerca. È possibile selezionare o deselezionare le opzioni seguenti:

**Maiuscole/minuscole**

Quando questa opzione è selezionata, le finestre **Risultati ricerca** visualizzano solo le istanze della stringa specificata in **Trova** corrispondenti per contenuto e combinazione di maiuscole/minuscole. Ad esempio, la ricerca di "MyObject" con l'opzione **Maiuscole/minuscole** selezionata restituisce "MyObject" ma non "myobject" o "MYOBJECT".

**Parola intera**

Quando questa opzione è selezionata, le finestre **Risultati ricerca** visualizzano solo le istanze della stringa specificata in **Trova** con l'esatta corrispondenza di parole. Ad esempio, la ricerca di "MyObject" restituisce "MyObject" ma non "CMyObject" o "MyObjectC".

**Usare espressioni regolari**

Se questa casella di controllo è selezionata, è possibile usare le notazioni speciali per definire modelli di testo nelle caselle di testo **Trova** o **Sostituisci con**. Per un elenco di queste notazioni, vedere [Uso delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Cerca i seguenti tipi di file**

L'elenco indica i tipi di file da cercare nelle directory **Cerca in**. Se questo campo è vuoto, la ricerca verrà eseguita in tutti i file nelle directory **Cerca in**. Selezionare qualsiasi voce dell'elenco per immettere una stringa di ricerca preconfigurata che troverà i file dei tipi specificati.

## <a name="result-options"></a>Opzioni risultati

È possibile espandere o comprimere la **sezione Opzioni risultato.** È possibile selezionare o deselezionare le opzioni seguenti:

**Finestra Risultati ricerca 1**

Quando questa opzione è selezionata, i risultati della ricerca corrente sostituiranno il contenuto della finestra **Risultati ricerca 1**. Questa finestra viene aperta automaticamente per visualizzare i risultati della ricerca. Per aprire questa finestra manualmente, scegliere **Altre finestre** dal menu **Visualizza** e quindi **Risultati ricerca 1**.

**Finestra Risultati ricerca 2**

Quando questa opzione è selezionata, i risultati della ricerca corrente sostituiranno il contenuto della finestra **Risultati ricerca 2**. Questa finestra viene aperta automaticamente per visualizzare i risultati della ricerca. Per aprire questa finestra manualmente, scegliere **Altre finestre** dal menu **Visualizza** e quindi **Risultati ricerca 2**.

**Mostra solo nomi file**

Quando questa casella di controllo è selezionata, **le** finestre Risultati ricerca elencano i nomi e i percorsi completi per tutti i file che contengono la stringa di ricerca. Tuttavia, i risultati non includono la riga di codice in cui viene visualizzata la stringa. Questa casella di controllo è disponibile solo **per Trova nei** file.

**Non chiudere i file modificati con Sostituisci tutto**

Se questa casella di controllo è selezionata, i file in cui sono state eseguite sostituzioni rimangono aperti, in modo che sia possibile annullare o salvare le modifiche. È possibile che la quantità di memoria disponibile limiti il numero di file che possono rimanere aperti dopo un'operazione di sostituzione.

> [!CAUTION]
> Il comando **Annulla** può essere usato solo nei file che rimangono aperti per le modifiche. Se questa opzione non è selezionata, i file non ancora aperti per essere modificati rimarranno chiusi e non sarà disponibile alcuna opzione **Annulla** per tali file.

## <a name="see-also"></a>Vedi anche

- [Cercare e sostituire testo](../ide/finding-and-replacing-text.md)
- [Trovare nei file](../ide/find-in-files.md)
- [Comandi di Visual Studio](../ide/reference/visual-studio-commands.md)
