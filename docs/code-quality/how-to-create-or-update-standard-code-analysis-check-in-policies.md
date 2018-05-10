---
title: Creare o aggiornare criteri di controllo dell'analisi del codice Standard
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96fa2dd75c590e0841d7479e4e071154add04857
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Procedura: Creare o aggiornare criteri di archiviazione standard dell'analisi del codice

È possibile richiedere che l'analisi del codice deve essere eseguito in tutti i progetti di codice in un progetto team usando i criteri di controllo dell'analisi codice. Richiedere l'analisi del codice, è possibile migliorare la qualità del codice che viene archiviato nella codebase.

> [!NOTE]
> Questa funzionalità è disponibile solo se si utilizza Team Foundation Server.

Criteri di controllo dell'analisi del codice vengono impostati nelle impostazioni del progetto team e si applicano a ogni progetto di codice nel progetto team. Esecuzioni dell'analisi del codice sono configurate per i progetti di codice nel file di progetto (con estensione xxproj) per il progetto di codice. Esecuzioni dell'analisi del codice vengono eseguite nel computer locale. Quando si abilita un criterio di controllo dell'analisi codice, devono essere compilati in un progetto di codice che devono essere archiviati file termine dell'ultima modifica e l'analisi del codice esegue che contiene, come minimo, le regole nelle impostazioni del progetto team devono essere eseguite nel computer in cui il c sono state apportate le revisioni.

- Per codice gestito, si impostano i criteri di archiviazione specificando un *set di regole* che contiene un subset delle regole di analisi codice.

- Per il codice C/C++, in Visual Studio 2017 15,6 e versioni precedenti, i criteri di controllo richiedono che tutte le regole di analisi di codice vengono eseguite. È possibile aggiungere le direttive del preprocessore per disabilitare regole specifiche per singoli progetti di codice nel progetto team. In 15.7 e versioni successive, è possibile utilizzare **/analyze: ruleset** per specificare le regole da eseguire. Per altre informazioni, vedere [utilizzo di set di regole per specificare le regole di C++ per l'esecuzione](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

Dopo aver specificato un criterio di controllo per il codice gestito, i membri del team possono sincronizzare le impostazioni di analisi codice per i progetti di codice alle impostazioni dei criteri del progetto team.

## <a name="to-open-the-check-in-policy-editor"></a>Per aprire l'editor Criteri di archiviazione

1. In Team Explorer, fare clic sul nome del progetto team, scegliere **impostazioni progetto Team**, quindi fare clic su **controllo del codice sorgente**.

1. Nel **controllo del codice sorgente** la finestra di dialogo, seleziona il **criteri di archiviazione** scheda.

1. Eseguire una delle operazioni seguenti:

    - Fare clic su **Aggiungi** per creare un nuovo criterio di controllo.

    - Fare doppio clic su esistente **analisi del codice** elemento il **tipo di criteri** elenco per modificare i criteri.

## <a name="to-set-policy-options"></a>Per impostare le opzioni dei criteri

Selezionare o deselezionare le opzioni seguenti:

|Opzione|Descrizione|
|------------|-----------------|
|**Consenti archiviazione dei soli file che fanno parte della soluzione corrente.**|Analisi del codice è possibile eseguire solo sui file specificati nel file di configurazione di soluzione e progetto. Questo criterio assicura che tutto il codice che fa parte di una soluzione viene analizzato.|
|**Applicare l'analisi del codice C/C++ (/analyze)**|Richiede che tutti i progetti C o C++ generati con la / analizzare l'opzione del compilatore per eseguire l'analisi del codice prima che possano essere archiviati.|
|**Applicare l'analisi del codice per il codice gestito**|Richiede che tutti i progetti gestiti, eseguire l'analisi del codice e compilare prima che possano essere archiviati.|

## <a name="to-specify-a-managed-rule-set"></a>Per specificare un set di regole gestito

Dal **eseguire il set di regole** elenco, utilizzare uno dei metodi seguenti:

- Selezionare un set di regole standard Microsoft.

- Selezionare una regola personalizzata imposta facendo clic  **\<seleziona Set di regole dal controllo del codice sorgente... >**. Quindi, digitare il percorso controllo della versione del set di regole nel browser del controllo del codice sorgente. La sintassi di un percorso di controllo della versione è:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Per ulteriori informazioni su come creare e implementare una regola di criteri di controllo personalizzati, vedere [criteri di controllo implementare personalizzati per codice gestito](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Vedere anche

- [Creare e usare criteri di controllo dell'analisi del codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)