---
title: Sincronizzare i set di regole del progetto con i criteri di archiviazione
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a35ba1b9d54507883882fbe62c0533805882560
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975063"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-an-azure-devops-project-check-in-policy"></a>Procedura: Sincronizzare i set di regole del progetto di codice con i criteri di archiviazione del progetto DevOps di Azure

Sincronizzare le impostazioni di analisi del codice per i progetti di codice con i criteri di archiviazione per il progetto DevOps di Azure specificando un set di regole che contiene almeno le regole specificate nel set di regole per i criteri di archiviazione. Il responsabile dello sviluppatore può indicare il nome e la posizione del set di regole per i criteri di archiviazione. È possibile utilizzare una delle opzioni seguenti per assicurarsi che l'analisi del codice per il progetto utilizzi il set corretto di regole:

- Se i criteri di archiviazione utilizzano uno dei set di regole predefiniti Microsoft, aprire la finestra di dialogo proprietà per il progetto di codice, visualizzare la pagina analisi codice e selezionare il set di regole. I set di regole standard Microsoft vengono installati automaticamente con Visual Studio sono impostati in sola lettura e non devono essere modificati. Se i set di regole non vengono modificati, è garantita la corrispondenza tra le regole nei set di regole dei criteri e locali.

- Se i criteri di archiviazione utilizzano un set di regole personalizzato, eseguire un'operazione Get sul file del set di regole nel controllo della versione per creare una copia locale. Specificare quindi il percorso locale nelle impostazioni di analisi del codice per il progetto di codice. Le regole sono sicuramente corrispondenti se il set di regole per i criteri di archiviazione è aggiornato.

     Se si esegue il mapping del percorso del controllo della versione a una cartella locale che si trova nella stessa relazione con la radice del progetto DevOps di Azure come progetto di codice, il percorso della regola viene impostato usando un percorso relativo. Il percorso relativo garantisce che l'impostazione del progetto di codice per l'analisi del codice possa essere spostata in altri computer.

- Personalizzare una copia del set di regole per i criteri di archiviazione per un progetto di codice. Verificare che il nuovo set di regole includa tutte le regole nei criteri di archiviazione e qualsiasi altra regola che si desidera includere. È necessario assicurarsi che il set di regole includa tutte le regole nel set di regole per i criteri di archiviazione.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Per specificare un set di regole standard Microsoft

1. Nelle **Esplora soluzioni**, fare clic sul progetto codice e quindi fare clic su **proprietà**.

2. Fare clic su **analisi codice**.

::: moniker range="vs-2017"

3. Nell'elenco **Esegui questo set di regole** selezionare il set di regole dei criteri di archiviazione.

::: moniker-end

::: moniker range=">=vs-2019"

3. Nell'elenco **regole attive** selezionare il set di regole dei criteri di archiviazione.

::: moniker-end

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Per specificare un set di regole dei criteri di archiviazione personalizzati

1. Se necessario, eseguire un'operazione Get sul file del set di regole che specifica i criteri di archiviazione.

2. Nelle **Esplora soluzioni**, fare clic sul progetto codice e quindi fare clic su **proprietà**.

3. Fare clic su **analisi codice**.

::: moniker range="vs-2017"

4. Nell'elenco **Esegui questo set di regole** fare clic su **\<Browse >** .

::: moniker-end

::: moniker range=">=vs-2019"

4. Nell'elenco **regole attive** fare clic su **\<Browse >** .

::: moniker-end

5. Nella finestra di dialogo **Apri** specificare il file del set di regole dei criteri di archiviazione.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Per creare un set di regole personalizzato per un progetto di codice

Per informazioni sulla creazione di un set di regole personalizzato, vedere [personalizzare un set di regole](how-to-create-a-custom-rule-set.md).
