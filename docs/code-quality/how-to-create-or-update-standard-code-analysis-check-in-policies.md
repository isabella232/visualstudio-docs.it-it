---
title: Creare/aggiornare i criteri di archiviazione dell'analisi codice standard
description: Informazioni su come assicurarsi che l'analisi del codice venga eseguita in tutti i progetti di codice in un Azure DevOps progetto. Vedere come configurare i criteri di archiviazione dell'analisi del codice del progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 70442184ae7a8ce36657ce9c2dbc8887f9d3b9e7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631968"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Procedura: Creare o aggiornare criteri di archiviazione standard dell'analisi del codice

È possibile richiedere che l'analisi del codice sia eseguita in tutti i progetti di codice in un progetto Azure DevOps usando i criteri di archiviazione dell'analisi del codice. La richiesta di analisi del codice può migliorare la qualità del codice archiviato nella codebase.

> [!NOTE]
> Questa funzionalità è disponibile solo se si usa Team Foundation Server .

I criteri di archiviazione dell'analisi codice vengono impostati nelle impostazioni del progetto e si applicano a ogni progetto di codice. Le esecuzioni dell'analisi del codice vengono configurate per i progetti di codice nel file di progetto (con estensione xxproj) per il progetto di codice. Le esecuzioni dell'analisi del codice vengono eseguite nel computer locale. Quando si abilitano i criteri di archiviazione dell'analisi codice, i file in un progetto di codice che devono essere archiviati devono essere compilati dopo l'ultima modifica e un'esecuzione dell'analisi del codice che contenga almeno le regole nelle impostazioni del progetto nel computer in cui sono state apportate le modifiche.

- Per il codice gestito, impostare i criteri di archiviazione specificando un set di *regole* che contiene un subset delle regole di analisi del codice.

- Per il codice C/C++, in Visual Studio 2017 versione 15.6 e precedenti, i criteri di archiviazione richiedono l'esecuzione di tutte le regole di analisi del codice. È possibile aggiungere direttive di pre-elaborazione per disabilitare regole specifiche per i singoli progetti di codice nel Azure DevOps progetto. Nella versione 15.7 e successive è possibile usare **/analyze:ruleset** per specificare le regole da eseguire. Per altre informazioni, vedere [Uso di set di regole per specificare le regole C++ da eseguire.](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run)

Dopo aver specificato i criteri di archiviazione per il codice gestito, i membri del team possono sincronizzare le impostazioni di analisi del codice per i progetti di codice Azure DevOps impostazioni dei criteri del progetto.

## <a name="to-open-the-check-in-policy-editor"></a>Per aprire l'editor dei criteri di archiviazione

1. In Team Explorer fare clic con il pulsante destro del mouse sul nome del progetto, scegliere **Project Impostazioni** e quindi fare clic su **Controllo del codice sorgente**.

1. Nella finestra **di dialogo** Controllo del codice sorgente selezionare la scheda **Criteri di** archiviazione.

1. Eseguire una delle operazioni seguenti:

    - Fare **clic su** Aggiungi per creare un nuovo criterio di archiviazione.

    - Fare doppio clic **sull'elemento Code Analysis** esistente nell'elenco Tipo **di** criterio per modificare i criteri.

## <a name="to-set-policy-options"></a>Per impostare le opzioni dei criteri

Selezionare o deselezionare le opzioni seguenti:

|Opzione|Descrizione|
|------------|-----------------|
|**Applicare l'archiviazione per contenere solo i file che fanno parte della soluzione corrente.**|L'analisi del codice può essere eseguita solo sui file specificati nei file di configurazione della soluzione e del progetto. Questo criterio garantisce l'analisi di tutto il codice che fa parte di una soluzione.|
|**Applicare il Code Analysis C/C++ (/analyze)**|Richiede che tutti i progetti C o C++ siano compilati con l'opzione del compilatore /analyze per eseguire l'analisi del codice prima di poter essere archiviati.|
|**Imponi Code Analysis codice gestito**|Richiede che tutti i progetti gestiti esevano l'analisi del codice e la compilazione prima di poter essere archiviati.|

## <a name="to-specify-a-managed-rule-set"></a>Per specificare un set di regole gestite

**Nell'elenco Esegui questo set di** regole usare uno dei metodi seguenti:

- Selezionare un set di regole standard Microsoft.

- Selezionare un set di regole personalizzato facendo clic su **\<Select Rule Set from Source Control...>** . Digitare quindi il percorso del controllo della versione del set di regole nel browser del controllo del codice sorgente. La sintassi di un percorso di controllo della versione è:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Per altre informazioni su come creare e implementare un set di regole dei criteri di archiviazione personalizzato, vedere Implementare criteri di archiviazione [personalizzati per codice gestito.](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)

## <a name="see-also"></a>Vedi anche

- [Implementare i criteri di archiviazione di analisi codice personalizzati per il codice gestito](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)
