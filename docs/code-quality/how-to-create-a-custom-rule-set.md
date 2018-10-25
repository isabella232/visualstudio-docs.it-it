---
title: Creare una regola di analisi di codice personalizzato imposta in Visual Studio
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dce43c02f4976b51bab61a48f615fb0307102fc7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884186"
---
# <a name="customize-a-rule-set"></a>Personalizzare un set di regole

È possibile creare una regola personalizzata impostata per soddisfare specifiche esigenze del progetto per l'analisi codice.

## <a name="create-a-custom-rule-set"></a>Creare un set di regole personalizzato

Per creare una regola personalizzata set, è possibile aprire una set di regole predefinite di **editor set di regole**. Da qui, è possibile aggiungere o rimuovere le regole specifiche ed è possibile modificare l'azione che si verifica quando una regola viene violata&mdash;, ad esempio, Mostra un avviso o un errore.

1. Nelle **Esplora soluzioni**, fare clic sul progetto e quindi selezionare **proprietà**.

2. Nel **delle proprietà** pagine, selezionare la **analisi del codice** scheda.

3. Nel **eseguire questo set di regole** riepilogo, effettuare una delle operazioni seguenti:

   - Selezionare il set di regole che si desidera personalizzare.

     \- oppure -

   - Selezionare  **\<Sfoglia >** per specificare set di una regola esistente non incluso nell'elenco.

4. Selezionare **aperto** per visualizzare le regole nell'editor set di regole.

È anche possibile creare un nuovo file di set di regole dal **nuovo File** finestra di dialogo:

1. Selezionare **File** > **New** > **File**, o premere **Ctrl**+**N**.

2. Nel **nuovo File** finestra di dialogo, seleziona il **generali** categoria a sinistra e quindi selezionare **Set di regole di analisi codice**.

3. Selezionare **Apri**.

   Il nuovo *ruleSet* file verrà aperto nell'editor set di regole.

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Creare una regola personalizzata impostata da più set di regole

1. In Esplora soluzioni fare clic sul progetto e quindi selezionare **proprietà**.

2. Nel **delle proprietà** pagine, selezionare la **analisi del codice** scheda.

3. Selezionare  **\<Scegli più set di regole... >** dalla **eseguire questo set di regole**.

4. Nel **Aggiungi o Rimuovi set di regole** nella finestra di dialogo selezionare i set di regole si desidera includere nel nuovo set di regole.

   ![Aggiungere o rimuovere la finestra di dialogo set di regole](media/add-remove-rule-sets.png)

5. Selezionare **Salva con nome**, immettere un nome per il *ruleSet* e quindi selezionare **Salva**.

   Il nuovo set di regole è selezionato nel **eseguire questo set di regole** elenco.

6. Selezionare **aprire** per aprire il nuovo set di regole in editor set di regole.

## <a name="name-and-description"></a>Nome e descrizione

Per modificare il nome visualizzato di un set di regole che viene aperto nell'editor, aprire il **delle proprietà** finestra selezionando **View** > **finestra proprietà** nella barra dei menu. Immettere il nome visualizzato nei **nome** casella. È anche possibile immettere una descrizione per il set di regole.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver creato una regola impostata, il passaggio successivo consiste nel personalizzare le regole aggiungendo o rimuovendo le regole o modificando il livello di gravità di violazioni delle regole.

> [!div class="nextstepaction"]
> [Modificare le regole nell'editor set di regole](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Vedere anche

- [Procedura: Configurare l'analisi codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Tabella di riferimento del set di regole di analisi del codice](../code-quality/rule-set-reference.md)