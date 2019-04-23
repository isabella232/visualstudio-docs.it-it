---
title: 'Procedura dettagliata: Analisi C -C++ per i difetti del codice | Microsoft Docs'
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
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: dcd862b6ff9c94b8de3fc8b5a56164549fefe8ca
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099505"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Procedura dettagliata: Analisi del codice C/C++ per l'identificazione degli errori
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura dettagliata illustra come analizzare il codice C/C++ per i potenziali difetti di codice usando lo strumento di analisi codice per il codice C/C++.  
  
 In questa procedura dettagliata, passo passo il processo di uso di analisi del codice per analizzare il codice C/C++ per potenziali difetti del codice.  
  
 Si completerà la procedura seguente:  
  
- Esegui analisi del codice nel codice nativo.  
  
- Analizzare gli avvisi degli errori di codice.  
  
- Considera avviso come errore.  
  
- Annotare il codice sorgente per migliorare l'analisi degli errori del codice.  
  
## <a name="prerequisites"></a>Prerequisiti  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] o [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].  
  
- Una copia del [esempio dimostrativo](../code-quality/demo-sample.md).  
  
- Conoscenza di base di C/C++.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>Per eseguire analisi degli errori del codice nel codice nativo  
  
1. Aprire la soluzione Demo in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     La soluzione Demo ora Popola **Esplora soluzioni**.  
  
2. Nel menu **Compila** fare clic su **Ricompila soluzione**.  
  
     La soluzione venga compilata senza errori o avvisi.  
  
3. Nelle **Esplora soluzioni**, selezionare il progetto CodeDefects.  
  
4. Scegliere **Proprietà** dal menu **Progetto**.  
  
     Il **pagine delle proprietà CodeDefects** verrà visualizzata la finestra di dialogo.  
  
5. Fare clic su **analisi del codice**.  
  
6. Scegliere il **Attiva analisi codice per C/C++ in fase di compilazione** casella di controllo.  
  
7. Ricompilare il progetto CodeDefects.  
  
     Avvisi dell'analisi codice vengono visualizzati nei **elenco errori**.  
  
### <a name="to-analyze-code-defect-warnings"></a>Per analizzare gli avvisi degli errori di codice  
  
1. Nel **View** menu, fare clic su **elenco errori**.  
  
     In base al profilo di sviluppo scelto nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], potrebbe essere necessario puntare a **Other Windows** sul **vista** menu e quindi fare clic su **elenco errori**.  
  
2. Nel **elenco errori**, fare doppio clic sull'avviso seguente:  
  
     avviso C6230: Cast implicito tra tipi integer semanticamente diversi: utilizzo di HRESULT in un contesto booleano.  
  
     L'editor di codice viene visualizzata la riga che ha causato l'avviso nella funzione `bool``ProcessDomain()`. Questo avviso indica che un valore HRESULT è in uso in un'istruzione 'if' in cui è previsto un risultato booleano.  
  
3. Risolvere il problema utilizzando la macro SUCCEEDED. Il codice dovrebbe essere simile al seguente:  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4. Nel **elenco errori**, fare doppio clic sull'avviso seguente:  
  
     avviso C6282: Operatore errato: assegnazione di costante in contesto di test. È stato = = previsto?  
  
5. Risolvere il problema eseguendo il test per verificarne l'uguaglianza. Il codice dovrebbe essere simile al codice seguente:  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>Interpreta un avviso come errore  
  
1. Nel file bug. cpp, aggiungere il codice seguente `#pragma` istruzione all'inizio del file da considerare l'avviso C6001 come errore:  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2. Ricompilare il progetto CodeDefects.  
  
     Nel **elenco errori**, C6001 viene ora visualizzato come un errore.  
  
3. Correggere gli errori C6001 due rimanenti nel **elenco errori** inizializzando `i` e `j` su 0.  
  
4. Ricompilare il progetto CodeDefects.  
  
     Il progetto viene compilato senza eventuali avvisi o errori.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Per correggere gli avvisi di annotazione di codice sorgente nella Annotation  
  
1. In Esplora soluzioni selezionare il progetto di annotazioni.  
  
2. Scegliere **Proprietà** dal menu **Progetto**.  
  
     Il **pagine delle proprietà di annotazioni** verrà visualizzata la finestra di dialogo.  
  
3. Fare clic su **analisi del codice**.  
  
4. Selezionare il **Attiva analisi codice per C/C++ in fase di compilazione** casella di controllo.  
  
5. Ricompilare il progetto di annotazioni.  
  
6. Nel **elenco errori**, fare doppio clic sull'avviso seguente:  
  
     avviso C6011: Deferenziazione del puntatore NULL 'newNode'.  
  
     Questo avviso indica un errore dal chiamante per controllare il valore restituito. In questo caso, una chiamata a **AllocateNode** potrebbe restituire un valore NULL (vedere il file di intestazione Annotations. h per la dichiarazione di funzione per AllocateNode).  
  
7. Aprire il file Annotations.  
  
8. Per risolvere questo problema, utilizzare un'istruzione 'if' per testare il valore restituito. Il codice dovrebbe essere simile al seguente:  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Ricompilare il progetto di annotazioni.  
  
     Il progetto viene compilato senza eventuali avvisi o errori.  
  
### <a name="to-use-source-code-annotation"></a>Per utilizzare l'annotazione del codice sorgente  
  
1. Annotare i parametri formali e valore restituito di funzione `AddTail` utilizzando le condizioni di Pre e Post, come illustrato in questo esempio:  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2. Ricompilare il progetto di annotazioni.  
  
3. Nel **elenco errori**, fare doppio clic sull'avviso seguente:  
  
     avviso C6011: Deferenziazione del puntatore NULL 'node'.  
  
     Questo avviso indica che il nodo passato alla funzione potrebbe essere null e indica il numero di riga in cui è stato generato l'avviso.  
  
4. Per risolvere questo problema, utilizzare un'istruzione 'if' per testare il valore restituito. Il codice dovrebbe essere simile al seguente:  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5. Ricompilare il progetto di annotazioni.  
  
     Il progetto viene compilato senza eventuali avvisi o errori.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Analisi del codice gestito per individuarne i difetti](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
