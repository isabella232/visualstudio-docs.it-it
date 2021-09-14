---
title: Sincronizzare i set di regole del progetto con i criteri di archiviazione
ms.date: 11/04/2016
description: Informazioni su come sincronizzare un set Visual Studio regole del progetto di codice con Azure DevOps criteri di archiviazione del progetto.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 20c4d0c6fc5583686648507be2a36c5183ca70c6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631920"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-an-azure-devops-project-check-in-policy"></a>Procedura: Sincronizzare il codice Project set di regole con Azure DevOps Project criteri di archiviazione

Sincronizzare le impostazioni di analisi del codice per i progetti di codice con i criteri di archiviazione per il progetto Azure DevOps specificando un set di regole che contiene almeno le regole specificate nel set di regole per i criteri di archiviazione. Il responsabile dello sviluppatore può informare l'utente del nome e del percorso del set di regole per i criteri di archiviazione. È possibile usare una delle opzioni seguenti per assicurarsi che l'analisi del codice per il progetto usi il set corretto di regole:

- Se i criteri di archiviazione utilizzano uno dei set di regole predefiniti di Microsoft, aprire la finestra di dialogo delle proprietà per il progetto di codice, visualizzare la pagina Code Analysis e selezionare il set di regole. I set di regole standard Microsoft vengono installati automaticamente con Visual Studio sono impostati su sola lettura e non devono essere modificati. Se i set di regole non vengono modificati, è garantita la corrispondenza delle regole nei criteri e nei set di regole locali.

- Se i criteri di archiviazione utilizzano un set di regole personalizzato, eseguire un'operazione get sul file del set di regole nel controllo della versione per creare una copia locale. Specificare quindi il percorso locale nelle impostazioni di analisi del codice per il progetto di codice. È garantito che le regole corrispondano se il set di regole per i criteri di archiviazione è aggiornato.

     Se si esegue il mapping del percorso del controllo della versione a una cartella locale che si trova nella stessa relazione con la radice del progetto Azure DevOps del progetto di codice, il percorso della regola viene impostato usando un percorso relativo. Il percorso relativo garantisce che l'impostazione del progetto di codice per l'analisi del codice possa essere spostata in altri computer.

- Personalizzare una copia del set di regole per i criteri di archiviazione per un progetto di codice. Assicurarsi che il nuovo set di regole contenga tutte le regole nei criteri di archiviazione e tutte le altre regole che si desidera includere. È necessario assicurarsi che il set di regole includa tutte le regole nel set di regole per i criteri di archiviazione.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Per specificare un set di regole standard Microsoft

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto di codice e quindi scegliere **Proprietà**.

2. Fare clic su **Analisi codice**.

::: moniker range="vs-2017"

3. **Nell'elenco Esegui questo set di regole** selezionare il set di regole dei criteri di archiviazione.

::: moniker-end

::: moniker range=">=vs-2019"

3. **Nell'elenco Regole attive** selezionare il set di regole dei criteri di archiviazione.

::: moniker-end

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Per specificare un set di regole dei criteri di archiviazione personalizzato

1. Se necessario, eseguire un'operazione get sul file del set di regole che specifica i criteri di archiviazione.

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto di codice e quindi scegliere **Proprietà**.

3. Fare clic su **Analisi codice**.

::: moniker range="vs-2017"

4. **Nell'elenco Esegui questo set di regole** fare clic su **\<Browse>** .

::: moniker-end

::: moniker range=">=vs-2019"

4. **Nell'elenco Regole attive** fare clic su **\<Browse>** .

::: moniker-end

5. Nella finestra **di dialogo** Apri specificare il file del set di regole dei criteri di archiviazione.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Per creare un set di regole personalizzato per un progetto di codice

Per informazioni sulla creazione di un set di regole personalizzato, vedere [Personalizzare un set di regole](how-to-create-a-custom-rule-set.md).
