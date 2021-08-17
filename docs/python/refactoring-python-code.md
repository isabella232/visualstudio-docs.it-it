---
title: Effettuare il refactoring del codice Python
description: Visual Studio semplifica il refactoring del codice Python grazie alla ridenominazione degli identificatori, l'estrazione dei metodi, l'aggiunta delle importazioni e la rimozione di quelle inutilizzate.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 21556deca0da180d145b11ed155e0d8b993301a00362e9a67a9af1d4aa02f9a6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121229702"
---
# <a name="refactor-python-code"></a>Effettuare il refactoring del codice Python

Visual Studio offre diversi comandi per la trasformazione e la pulizia automatiche del codice sorgente Python:

- [Rinomina](#rename) consente di modificare un nome di classe, metodo o variabile selezionato
- [Estrai metodo](#extract-method) consente di creare un nuovo metodo dal codice selezionato
- [Aggiungi importazione](#add-import) fornisce uno smart tag per aggiungere un'importazione mancante
- [Rimuovi importazioni](#remove-unused-imports) consente di rimuovere le importazioni inutilizzate

## <a name="rename"></a>Rinominare

1. Fare clic con il pulsante destro del mouse sull'identificatore che si vuole rinominare e scegliere **Rinomina** oppure posizionare il cursore su tale identificatore e selezionare il comando di menu **Modifica** > **Refactoring** > **Rinomina** (**F2**).
2. Nella finestra di dialogo **Rinomina** visualizzata immettere il nuovo nome per l'identificatore e selezionare **OK**:

   ![Richiesta del nuovo nome di identificatore per la ridenominazione](media/code-refactor-rename-1.png)

3. Nella finestra di dialogo successiva selezionare i file e le istanze nel codice a cui applicare la ridenominazione. Selezionare qualsiasi istanza singola per visualizzare in anteprima la modifica specifica:

   ![Selezione delle posizioni in cui applicare le modifiche nella finestra di dialogo Rinomina](media/code-refactor-rename-2.png)

4. Selezionare **Applica** per apportare le modifiche nei file di codice sorgente. Questa azione può essere annullata.

## <a name="extract-method"></a>Estrai metodo

1. Selezionare le righe di codice o l'espressione da estrarre in un metodo separato.
2. Selezionare il **comando di** menu Edit Refactor Extract method (Modifica  >  **refactoring)** o digitare  >   **CTRL** + **R**  >  **M**.
3. Nella finestra di dialogo visualizzata immettere un nuovo nome di metodo, indicare la posizione in cui estrarlo e selezionare eventuali variabili di chiusura. Le variabili non selezionate per la chiusura vengono trasformate in argomenti del metodo:

   ![Finestra di dialogo Estrai metodo](media/code-refactor-extract-method-1.png)

4. Selezionare **OK** e il codice verrà modificato di conseguenza:

   ![Effetto dell'estrazione di un metodo](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Aggiungi importazione

Quando si posiziona il cursore su un identificatore per cui mancano le informazioni sul tipo, Visual Studio offre uno smart tag, ovvero l'icona a forma di lampadina a sinistra del codice, i cui comandi consentono di aggiungere l'istruzione `import` o `from ... import` necessaria:

![Smart tag Aggiungi importazione](media/code-refactor-add-import-1.png)

Visual Studio offre la funzione di completamento di `import` per i pacchetti e i moduli di primo livello nel progetto corrente e nella libreria standard. Visual Studio offre anche la funzione di completamento di `from ... import` per moduli e pacchetti secondari, oltre che per membri di modulo. I completamenti includono funzioni, classi o dati esportati. Selezionando una delle due opzioni, l'istruzione viene aggiunta all'inizio del file dopo le altre importazioni oppure in un'istruzione `from ... import` esistente se lo stesso modulo è già importato.

![Risultato dell'aggiunta di un'importazione](media/code-refactor-add-import-2.png)

Visual Studio tenta di escludere i membri che non sono effettivamente definiti in un modulo, ad esempio i moduli importati in un altro, ma che non sono elementi figlio del modulo che effettua l'importazione. Ad esempio, molti moduli usano `import sys` invece di `from xyz import sys`, quindi il completamento dell'importazione di `sys` da altri moduli non è visibile, anche se per i moduli manca un membro `__all__` che esclude `sys`.

Analogamente, Visual Studio filtra le funzioni importate da altri moduli o dallo spazio dei nomi predefinito. Ad esempio, se un modulo importa la funzione `settrace` dal modulo `sys`, in teoria potrebbe essere possibile importarlo da tale modulo. È però preferibile usare `import settrace from sys` direttamente, quindi Visual Studio offre specificamente tale istruzione.

Infine, Visual Studio esclude l'importazione se un elemento viene normalmente escluso, ma ha altri valori che verrebbero inclusi, ad esempio perché al nome è stato assegnato un valore nel modulo. Questo comportamento presuppone che il valore non debba essere esportato perché è definito in un altro modulo ed è pertanto probabile che l'assegnazione aggiuntiva sia un valore fittizio, anch'esso non esportato.

## <a name="remove-unused-imports"></a>Rimuovi importazioni

Durante la scrittura del codice è facile ritrovarsi con istruzioni `import` per moduli che non vengono usati affatto. Dato che Visual Studio analizza il codice, può determinare automaticamente se un'istruzione `import` è necessaria verificando se il nome importato viene usato nell'ambito dell'istruzione.

Fare clic con il pulsante destro del mouse in un punto qualsiasi dell'editor e scegliere Rimuovi importazioni **,** che offre le opzioni da rimuovere da **Tutti** gli ambiti o solo dall'ambito **corrente:**

![Menu Rimuovi importazioni](media/code-refactor-remove-imports-1.png)

Visual Studio apporterà quindi le modifiche appropriate al codice:

![Effetto della rimozione delle importazioni](media/code-refactor-remove-imports-2.png)

Si noti che Visual Studio non tiene conto del flusso di controllo. L'uso di un nome prima di un'istruzione `import` viene interpretato come uso effettivo del nome. Visual Studio ignora anche tutte le importazioni `from __future__`, le importazioni che vengono eseguite all'interno di una definizione di classe, nonché da istruzioni `from ... import *`.
