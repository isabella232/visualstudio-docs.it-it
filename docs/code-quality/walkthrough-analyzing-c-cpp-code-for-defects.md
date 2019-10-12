---
title: "Procedura dettagliata: Analisi del codice C/C++ per l'identificazione degli errori"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: bdb99cf487995859b9623f11b3559f1b5e7e3ca7
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018348"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Procedura dettagliata: Analisi del codice C/C++ per l'identificazione degli errori

Questa procedura dettagliata illustra come analizzare C/C++ codice per i potenziali difetti del codice usando lo strumento di analisi del codiceC++ per C/code.

- Eseguire l'analisi del codice sul codice nativo.
- Analizza gli avvisi di errore del codice.
- Considera l'avviso come un errore.
- Annotare il codice sorgente per migliorare l'analisi del difetto del codice.

## <a name="prerequisites"></a>Prerequisiti

- Una copia dell' [esempio di demo](../code-quality/demo-sample.md).
- Conoscenza di base di CC++/.

### <a name="to-run-code-defect-analysis-on-native-code"></a>Per eseguire l'analisi del difetto del codice sul codice nativo

1. Aprire la soluzione demo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

     La soluzione Demo ora popola **Esplora soluzioni**.

2. Nel menu **Compila** fare clic su **Ricompila soluzione**.

     La soluzione viene compilata senza errori o avvisi.

3. In **Esplora soluzioni**selezionare il progetto codedifettos.

4. Scegliere **Proprietà** dal menu **Progetto**.

     Verrà visualizzata la finestra di dialogo **pagine delle proprietà Codedifettos** .

5. Fare clic su **analisi codice**.

6. Fare clic sulla casella di controllo **Abilita analisiC++ codice per la compilazione C/on** .

7. Ricompilare il progetto codedifettos.

     Gli avvisi di analisi del codice vengono visualizzati nel **Elenco errori**.

### <a name="to-analyze-code-defect-warnings"></a>Per analizzare gli avvisi di errore del codice

1. Scegliere **Elenco errori**dal menu **Visualizza** .

     A seconda del profilo dello sviluppatore scelto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], potrebbe essere necessario puntare ad **altre finestre** dal menu **Visualizza** , quindi fare clic su **Elenco errori**.

2. Nella **Elenco errori**fare doppio clic sull'avviso seguente:

     avviso C6230: Cast implicito tra tipi semanticamente diversi: utilizzo di HRESULT in un contesto booleano.

     Nell'editor di codice viene visualizzata la riga che ha provocato l'avviso nella funzione `bool ProcessDomain()`. Questo avviso indica che è in uso un HRESULT in un'istruzione ' If ' in cui è previsto un risultato booleano.

3. Correggere questo avviso utilizzando la macro SUCCEEDed. Il codice dovrebbe essere simile al codice seguente:

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. Nella **Elenco errori**fare doppio clic sull'avviso seguente:

     avviso C6282: Operatore errato: assegnazione alla costante nel contesto di test. Is = = designato?

5. Correggere questo avviso verificando l'uguaglianza. Il codice dovrebbe essere simile al codice seguente:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>Per considerare l'avviso come un errore

1. Nel file bug. cpp aggiungere l'istruzione `#pragma` seguente all'inizio del file per considerare il C6001 di avviso come errore:

   ```cpp
   #pragma warning (error: 6001)
   ```

2. Ricompilare il progetto codedifettos.

     Nel **Elenco errori**, C6001 viene visualizzato come un errore.

3. Correggere i due errori C6001 rimanenti nella **Elenco errori** inizializzando `i` e `j` su 0.

4. Ricompilare il progetto codedifettos.

     Il progetto viene compilato senza avvisi o errori.

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Per correggere gli avvisi di annotazione del codice sorgente nell'annotazione. c

1. In Esplora soluzioni selezionare il progetto annotazioni.

2. Scegliere **Proprietà** dal menu **Progetto**.

     Verrà visualizzata la finestra di dialogo **pagine delle proprietà delle annotazioni** .

3. Fare clic su **analisi codice**.

4. Selezionare la casella di controllo **Abilita analisi codiceC++ per la compilazione C/on** .

5. Ricompilare il progetto delle annotazioni.

6. Nella **Elenco errori**fare doppio clic sull'avviso seguente:

     avviso C6011: Dereferenziazione del puntatore NULL ' newNode '.

     Questo avviso indica un errore del chiamante per verificare il valore restituito. In questo caso, una chiamata a **AllocateNode** potrebbe restituire un valore null (vedere il file di intestazione Annotations. h per la dichiarazione di funzione per AllocateNode).

7. Aprire il file Annotations. cpp.

8. Per correggere il problema, utilizzare un'istruzione ' If ' per testare il valore restituito. Il codice dovrebbe essere simile al codice seguente:

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. Ricompilare il progetto delle annotazioni.

     Il progetto viene compilato senza avvisi o errori.

### <a name="to-use-source-code-annotation"></a>Per utilizzare l'annotazione del codice sorgente

1. Annotare i parametri formali e il valore restituito della funzione `AddTail` usando le condizioni pre e post, come illustrato nell'esempio seguente:

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. Ricompilare il progetto delle annotazioni.

3. Nella **Elenco errori**fare doppio clic sull'avviso seguente:

     avviso C6011: Dereferenziazione del puntatore NULL ' node '.

     Questo avviso indica che il nodo passato nella funzione potrebbe essere null e indica il numero di riga in cui è stato generato l'avviso.

4. Per correggere il problema, utilizzare un'istruzione ' If ' per testare il valore restituito. Il codice dovrebbe essere simile al codice seguente:

   ```cpp
   . . .
   LinkedList *newNode = NULL;
   if (NULL == node)
   {
        return NULL;
        . . .
   }
   ```

5. Ricompilare il progetto delle annotazioni.

     Il progetto viene compilato senza avvisi o errori.

## <a name="see-also"></a>Vedere anche

[Procedura dettagliata: Analisi del codice gestito per i difetti del codice @ no__t-0 @ no__t-1[analisi del codiceC++ per C/](../code-quality/code-analysis-for-c-cpp-overview.md)
