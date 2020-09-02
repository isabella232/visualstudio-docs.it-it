---
title: 'Procedura: creare un set di regole personalizzato | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e4aef02a2bb320112d7d268da28cf66b1ec6751
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657453"
---
# <a name="how-to-create-a-custom-rule-set"></a>Procedura: Creare un set di regole personalizzato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] , [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] e [!INCLUDE[vsPro](../includes/vspro-md.md)] è possibile creare e modificare un *set di regole* personalizzate per soddisfare specifiche esigenze di progetto associate all'analisi del codice. Per creare un set di regole personalizzato, è possibile aprire uno o più set di regole standard nell'Editor set di regole. È quindi possibile aggiungere o rimuovere regole specifiche ed è possibile modificare l'azione che si verifica quando l'analisi del codice determina che una regola è stata violata.

 Per creare un nuovo set di regole personalizzate, salvarlo con un nuovo nome file. Il set di regole personalizzate viene assegnato automaticamente al progetto.

## <a name="opening-the-rule-set-editor"></a>Apertura dell'editor set di regole

#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>Per aprire un file del set di regole vuoto nell'Editor set di regole

1. Scegliere nuovo **File** dal menu file [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , quindi fare **New** clic su **file**.

2. Nella finestra di dialogo **nuovo file** fare clic su **generale** nell'elenco **modelli installati** , quindi selezionare **set di regole di analisi codice**.

3. Verrà visualizzato l'editor set di regole. Nessuna regola selezionata nell'elenco dell'editor.

#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Per creare una regola personalizzata da un singolo set di regole esistente

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.

2. Nella scheda **Proprietà** fare clic su **analisi codice**.

3. Nell'elenco a discesa **set di regole** effettuare una delle operazioni seguenti:

   - Selezionare il set di regole che si desidera personalizzare.

     \- - oppure -

   - Selezionare **\<Browse...>** questa impostazione per specificare un set di regole esistente non presente nell'elenco.

4. Fare clic su **Apri** per visualizzare le regole nell'Editor set di regole.

#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>Per creare un set di regole personalizzato da più set di regole esistenti

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.

2. Nella scheda **Proprietà** fare clic su **analisi codice**.

3. Selezionare **\<Choose multiple rule sets...>** da **Esegui questo set di regole**.

4. Nella finestra di dialogo **Aggiungi o Rimuovi set di regole** selezionare i set di regole su cui si desidera basare il nuovo set di regole e quindi fare clic su **OK**.

5. Salvare il nuovo set di regole.

     Il nome del nuovo set di regole è selezionato nell'elenco **Esegui questo set di regole** . Nel passaggio successivo è possibile modificare il nome visualizzato del set di regole.

6. Opzionale Per modificare il nome visualizzato del set di regole, scegliere **finestra Proprietà**dal menu **Visualizza** . Digitare il nome visualizzato nella casella **nome** .

7. Per aggiungere, rimuovere o modificare specifiche regole di analisi del codice nel nuovo set di regole, fare clic su **Apri**.

## <a name="modifying-a-rule-set"></a>Modifica di un set di regole

#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Per modificare un set di regole nell'Editor set di regole

- Per modificare il nome visualizzato del set di regole, scegliere **finestra Proprietà**dal menu **Visualizza** . Immettere il nome visualizzato nella casella **nome** . Si noti che il nome visualizzato può essere diverso dal nome del file.

- Per aggiungere tutte le regole del gruppo a un set di regole personalizzate, selezionare la casella di controllo del gruppo. Per rimuovere tutte le regole del gruppo, deselezionare la casella di controllo.

- Per aggiungere una regola specifica al set di regole personalizzate, selezionare la casella di controllo relativa alla regola. Per rimuovere la regola dal set di regole, deselezionare la casella di controllo.

- Per modificare l'azione eseguita quando una regola viene violata in un'analisi del codice, fare clic nel campo **azione** per la regola, quindi selezionare uno dei valori seguenti:

     **Warn** : genera un avviso.

     **Errore** : genera un errore.

     **None** : Disabilita la regola. Questa azione equivale a rimuovere la regola dal set di regole.

## <a name="changing-the-rule-set-editor-display"></a>Modifica della visualizzazione dell'editor set di regole

#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Per raggruppare, filtrare o modificare i campi nell'editor del set di regole tramite la barra degli strumenti Editor set di regole

- Per espandere le regole in tutti i gruppi, fare clic su **Espandi tutto**.

- Per comprimere le regole in tutti i gruppi, fare clic su **Comprimi tutto**.

- Per modificare il campo in base al quale vengono raggruppate le regole, selezionare il campo dall'elenco **Raggruppa per** . Per visualizzare le regole non raggruppate, selezionare **\<None>** .

- Per aggiungere o rimuovere campi nelle colonne delle regole, fare clic su **Opzioni colonne**.

- Per nascondere le regole che non si applicano alla soluzione corrente, **nascondere le regole che non si applicano alla soluzione corrente**.

- Per passare tra le regole di visualizzazione e di occultamento a cui è stata assegnata l'azione errore, fare clic su **Mostra regole che possono generare errori di analisi del codice**.

- Per passare tra le regole di visualizzazione e di occultamento a cui è stata assegnata l'azione di avviso, fare clic su **Mostra regole che possono generare avvisi di analisi codice**.

- Per passare tra le regole di visualizzazione e di occultamento a cui è stata assegnata l'azione **Nessuna** , fare clic su **Mostra regole non abilitate**.

- Per aggiungere o rimuovere set di regole predefinite di Microsoft sul set di regole corrente, fare clic su **Aggiungi o Rimuovi set di regole figlio**.

## <a name="see-also"></a>Vedere anche
 [Procedura: configurare l'analisi del codice per un riferimento al set di regole di analisi del codice di un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [Code analysis rule set reference](../code-quality/code-analysis-rule-set-reference.md)
