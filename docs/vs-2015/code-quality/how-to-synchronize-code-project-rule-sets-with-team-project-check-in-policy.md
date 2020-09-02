---
title: 'Procedura: sincronizzare i set di regole del progetto di codice con i criteri di archiviazione del progetto team | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3c6e7550940f9d2efa5ca228123310f1b861ee76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651595"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Procedura: sincronizzare i set di regole del progetto di codice con i criteri di archiviazione del progetto team
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sincronizzare le impostazioni di analisi del codice per i progetti di codice con i criteri di archiviazione per il progetto team specificando un set di regole che contiene almeno le regole specificate nel set di regole per i criteri di archiviazione. Il responsabile dello sviluppatore può indicare il nome e la posizione del set di regole per i criteri di archiviazione. È possibile utilizzare una delle opzioni seguenti per assicurarsi che l'analisi del codice per il progetto utilizzi il set corretto di regole:

- Se i criteri di archiviazione utilizzano uno dei set di regole predefiniti Microsoft, aprire la finestra di dialogo proprietà per il progetto di codice, visualizzare la pagina analisi codice e selezionare il set di regole nella pagina analisi codice delle impostazioni del progetto di codice. I set di regole standard Microsoft vengono installati automaticamente con Visual Studio sono impostati in sola lettura e non devono essere modificati. Se i set di regole non vengono modificati, è garantita la corrispondenza tra le regole nei set di regole dei criteri e locali.

- Se i criteri di archiviazione utilizzano un set di regole personalizzato, eseguire un'operazione Get sul file del set di regole nel controllo della versione per creare una copia locale. Specificare quindi il percorso locale nelle impostazioni di analisi del codice per il progetto di codice. Le regole sono sicuramente corrispondenti se il set di regole per i criteri di archiviazione è aggiornato.

     Se si esegue il mapping del percorso del controllo della versione a una cartella locale che si trova nella stessa relazione con la radice del progetto team come progetto di codice, il percorso della regola viene impostato usando un percorso relativo. Il percorso relativo garantisce che l'impostazione del progetto di codice per l'analisi del codice possa essere spostata in altri computer.

- Personalizzare una copia del set di regole per i criteri di archiviazione per un progetto di codice. Verificare che il nuovo set di regole includa tutte le regole nei criteri di archiviazione e qualsiasi altra regola che si desidera includere. È necessario assicurarsi che il set di regole includa tutte le regole nel set di regole per i criteri di archiviazione.

### <a name="to-specify-a-microsoft-standard-rule-set"></a>Per specificare un set di regole standard Microsoft

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto di codice, quindi scegliere **Proprietà**.

2. Fare clic su **Analisi codice**.

3. Nell'elenco **Esegui questo set di regole** fare clic sul set di regole dei criteri di archiviazione.

### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Per specificare un set di regole dei criteri di archiviazione personalizzati

1. Se necessario, eseguire un'operazione Get sul file del set di regole che specifica i criteri di archiviazione.

2. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto di codice, quindi scegliere **Proprietà**.

3. Fare clic su **Analisi codice**.

4. Nell'elenco **Esegui questo set di regole** fare clic su **\<Browse...>** .

5. Nella finestra di dialogo **Apri** specificare il file del set di regole dei criteri di archiviazione.

### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Per creare un set di regole personalizzato per un progetto di codice

1. Seguire una delle procedure descritte in precedenza in questo argomento per selezionare i criteri di archiviazione del progetto team nella pagina analisi codice della finestra di dialogo Impostazioni progetto.

2. Fare clic su **Apri**.

3. Aggiungere o rimuovere regole usando l'editor set di regole.

     Per altre informazioni, vedere [creazione di set di regole personalizzati](../code-quality/creating-custom-code-analysis-rule-sets.md).

4. Salvare il set di regole modificato in un file con estensione RuleSet nel computer locale o in un percorso UNC.

5. Aprire la finestra di dialogo proprietà per il progetto di codice e visualizzare la pagina **analisi codice** .

6. Nell'elenco **Esegui questo set di regole** fare clic su **\<Browse...>** .

7. Nella finestra di dialogo **Apri** specificare il file del set di regole.
