---
title: 'Procedura: creare un Set di regole personalizzato | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e4b6c401b602575b34fb80ab98b31bb4ebcd1620
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255502"
---
# <a name="how-to-create-a-custom-rule-set"></a>Procedura: Creare un set di regole personalizzato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nelle [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)], e [!INCLUDE[vsPro](../includes/vspro-md.md)], è possibile creare e modificare un oggetto personalizzato *set di regole* per soddisfare specifiche esigenze del progetto associate con l'analisi del codice. Per creare una regola personalizzata impostata, si apre uno o più standard regola imposta nell'editor set di regole. È quindi possibile aggiungere o rimuovere le regole specifiche ed è possibile modificare l'azione che si verifica quando l'analisi del codice determina che una regola è stata violata.  
  
 Per creare una nuova regola personalizzata impostata, è necessario salvarlo con un nuovo nome file. Il set di regole personalizzato viene assegnato automaticamente al progetto.  
  
## <a name="opening-the-rule-set-editor"></a>Editor set di apertura della regola  
  
#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>Per aprire un oggetto vuoto regola set di file nell'editor set di regole  
  
1.  Nel **File** dal menu del [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], scegliere **New** e quindi fare clic su **File**.  
  
2.  Nel **nuovo File** della finestra di dialogo fare clic su **generali** nel **modelli installati** elenco e quindi selezionare **Set di regole di analisi codice**.  
  
3.  Viene visualizzato l'editor set di regole. Nell'elenco dell'editor è selezionata alcuna regola.  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Per creare una regola personalizzata da un singolo set di regole esistente  
  
1.  In Esplora soluzioni fare clic sul progetto e quindi selezionare **proprietà**.  
  
2.  Nel **delle proprietà** scheda, fare clic su **analisi del codice**.  
  
3.  Nel **del Set di regole** riepilogo, effettuare una delle operazioni seguenti:  
  
    -   Selezionare il set di regole che si desidera personalizzare.  
  
     \- oppure -  
  
    -   Selezionare  **\<Sfoglia >** per specificare set di una regola esistente non incluso nell'elenco.  
  
4.  Fare clic su **aperto** per visualizzare le regole nell'editor set di regole.  
  
#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>Per creare una regola personalizzata impostata da più set di regole esistente  
  
1.  In Esplora soluzioni fare clic sul progetto e quindi selezionare **proprietà**.  
  
2.  Nel **delle proprietà** scheda, fare clic su **analisi del codice**.  
  
3.  Selezionare  **\<Scegli più set di regole... >** dalla **eseguire questo set di regole**.  
  
4.  Nel **Aggiungi o Rimuovi set di regole** finestra di dialogo, seleziona i set di regole in cui si vuole basare il nuovo set di regole e quindi fare clic su **OK**.  
  
5.  Salvare il nuovo set di regole.  
  
     Il nome del nuovo set di regole è selezionato nel **eseguire questo set di regole** elenco. È possibile modificare il nome visualizzato della regola impostata nel passaggio successivo.  
  
6.  (Facoltativo) Per modificare il nome visualizzato del set di regole, scegliere il **View** menu, fare clic su **finestra proprietà**. Digitare il nome visualizzato nei **nome** casella.  
  
7.  Per aggiungere, rimuovere, o modificare le regole di analisi di codice specifico del nuovo set di regole, fare clic su **aperto**.  
  
## <a name="modifying-a-rule-set"></a>Modifica di un set di regole  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Per modificare una regola impostata nell'editor set di regole  
  
-   Per modificare il nome visualizzato del set di regole, scegliere il **View** menu, fare clic su **finestra proprietà**. Immettere il nome visualizzato nei **nome** casella. Si noti che il nome visualizzato può essere diverso dal nome del file.  
  
-   Per aggiungere tutte le regole del gruppo a un set di regole personalizzate, selezionare la casella di controllo del gruppo. Per rimuovere tutte le regole del gruppo, deselezionare la casella di controllo.  
  
-   Per aggiungere una regola specifica per il set di regole personalizzate, selezionare la casella di controllo della regola. Per rimuovere la regola dal set di regole, deselezionare la casella di controllo.  
  
-   Per modificare l'azione eseguita quando viene violata una regola in un'analisi del codice, fare clic nella **azione** campo per la regola e quindi selezionare uno dei valori seguenti:  
  
     **Avvisa** -genera un avviso.  
  
     **Errore** -verrà generato un errore.  
  
     **Nessuno** -disabilita la regola. Questa azione è quello utilizzato per la rimozione della regola dal set di regole.  
  
## <a name="changing-the-rule-set-editor-display"></a>Modifica la regola del set di visualizzazione dell'editor  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Per raggruppare, filtrare o modificare i campi nell'editor set di regole utilizzando la barra degli strumenti editor set di regole  
  
-   Per espandere le regole in tutti i gruppi, fare clic su **Espandi tutto**.  
  
-   Per comprimere le regole in tutti i gruppi, fare clic su **Comprimi tutto**.  
  
-   Per modificare il campo che sono raggruppate le regole, selezionare il campo dal **Group By** elenco. Per visualizzare le regole separate, selezionare  **\<None >**.  
  
-   Per aggiungere o rimuovere i campi nelle colonne della regola, fare clic su **opzioni di colonna**.  
  
-   Per le regole che non si applicano alla soluzione corrente, nascondere **nascondere le regole che non si applicano alla soluzione corrente**.  
  
-   Per visualizzare e nascondere le regole che vengono assegnate l'azione di errore, fare clic su **Mostra regole che possono generare errori di analisi codice**.  
  
-   Per visualizzare e nascondere le regole di cui sono assegnate l'azione di avviso, fare clic su **Mostra regole che possono generare avvisi di analisi codice**.  
  
-   Per alternare mostrando e nascondendo le regole che vengono assegnate le **None** azione, fare clic su **Mostra regole che non sono abilitate**.  
  
-   Per aggiungere o rimuovere set di regole predefinito per il set di regole corrente di Microsoft, fare clic su **Aggiungi o Rimuovi set di regole figlio**.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: configurare l'analisi codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Tabella di riferimento del set di regole di analisi del codice](../code-quality/code-analysis-rule-set-reference.md)



