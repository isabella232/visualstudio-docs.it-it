---
title: 'Procedura dettagliata: analisi delC++ codice C per i difetti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 37
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: c822dbcc6a1ece2040da22a3442dd584c3926d97
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272443"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Procedura guidata: analisi del codice C/C++ per l'identificazione degli errori
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura dettagliata illustra come analizzare C/C++ codice per i potenziali difetti del codice usando lo strumento di analisi del codiceC++ per C/code.  
  
 In questa procedura dettagliata viene illustrato il processo di utilizzo dell'analisi del codice per analizzare il codiceC++ C/codice per i potenziali difetti del codice.  
  
 I passaggi eseguiti sono i seguenti:  
  
- Eseguire l'analisi del codice sul codice nativo.  
  
- Analizza gli avvisi di errore del codice.  
  
- Considera l'avviso come un errore.  
  
- Annotare il codice sorgente per migliorare l'analisi del difetto del codice.  
  
## <a name="prerequisites"></a>Prerequisites  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] o [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].  
  
- Una copia dell' [esempio di demo](../code-quality/demo-sample.md).  
  
- Conoscenza di base di CC++/.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>Per eseguire l'analisi del difetto del codice sul codice nativo  
  
1. Aprire la soluzione demo in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     La soluzione Demo ora popola **Esplora soluzioni**.  
  
2. Nel menu **Compila** fare clic su **Ricompila soluzione**.  
  
     La soluzione viene compilata senza errori o avvisi.  
  
3. In **Esplora soluzioni**selezionare il progetto codedifettos.  
  
4. Scegliere **Proprietà** dal menu **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **pagine delle proprietà Codedifettos** .  
  
5. Fare clic su **Analisi codice**.  
  
6. Fare clic sulla casella di controllo **Abilita analisiC++ codice per la compilazione C/on** .  
  
7. Ricompilare il progetto codedifettos.  
  
     Gli avvisi di analisi del codice vengono visualizzati nel **Elenco errori**.  
  
### <a name="to-analyze-code-defect-warnings"></a>Per analizzare gli avvisi di errore del codice  
  
1. Scegliere **Elenco errori** dal menu **Visualizza**.  
  
     A seconda del profilo dello sviluppatore scelto in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], potrebbe essere necessario puntare ad **altre finestre** dal menu **Visualizza** , quindi fare clic su **Elenco errori**.  
  
2. Nella **Elenco errori**fare doppio clic sull'avviso seguente:  
  
     avviso C6230: cast implicito tra tipi semanticamente diversi: utilizzo di HRESULT in un contesto booleano.  
  
     Nell'editor di codice viene visualizzata la riga che ha provocato l'avviso nella funzione `bool``ProcessDomain()`. Questo avviso indica che è in uso un HRESULT in un'istruzione ' If ' in cui è previsto un risultato booleano.  
  
3. Correggere questo avviso utilizzando la macro SUCCEEDed. Il codice dovrebbe essere simile al codice seguente:  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4. Nella **Elenco errori**fare doppio clic sull'avviso seguente:  
  
     avviso C6282: operatore errato: assegnazione alla costante nel contesto di test. Is = = designato?  
  
5. Correggere questo avviso verificando l'uguaglianza. Il codice dovrebbe essere simile al codice seguente:  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>Per considerare l'avviso come un errore  
  
1. Nel file bug. cpp aggiungere l'istruzione `#pragma` seguente all'inizio del file per considerare il C6001 di avviso come errore:  
  
    ```  
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
  
3. Fare clic su **Analisi codice**.  
  
4. Selezionare la casella di controllo **Abilita analisi codiceC++ per la compilazione C/on** .  
  
5. Ricompilare il progetto delle annotazioni.  
  
6. Nella **Elenco errori**fare doppio clic sull'avviso seguente:  
  
     avviso C6011: dereferenziazione del puntatore NULL ' newNode '.  
  
     Questo avviso indica un errore del chiamante per verificare il valore restituito. In questo caso, una chiamata a **AllocateNode** potrebbe restituire un valore null (vedere il file di intestazione Annotations. h per la dichiarazione di funzione per AllocateNode).  
  
7. Aprire il file Annotations. cpp.  
  
8. Per correggere il problema, utilizzare un'istruzione ' If ' per testare il valore restituito. Il codice dovrebbe essere simile al codice seguente:  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Ricompilare il progetto delle annotazioni.  
  
     Il progetto viene compilato senza avvisi o errori.  
  
### <a name="to-use-source-code-annotation"></a>Per utilizzare l'annotazione del codice sorgente  
  
1. Annotare i parametri formali e il valore restituito della funzione `AddTail` usando le condizioni pre e post, come illustrato nell'esempio seguente:  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2. Ricompilare il progetto delle annotazioni.  
  
3. Nella **Elenco errori**fare doppio clic sull'avviso seguente:  
  
     avviso C6011: dereferenziazione del puntatore NULL ' node '.  
  
     Questo avviso indica che il nodo passato nella funzione potrebbe essere null e indica il numero di riga in cui è stato generato l'avviso.  
  
4. Per correggere il problema, utilizzare un'istruzione ' If ' per testare il valore restituito. Il codice dovrebbe essere simile al codice seguente:  
  
    ```  
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
 [Procedura dettagliata: analisi del codice gestito per l'identificazione di errori del codice](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
