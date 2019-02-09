---
title: Creare o aggiornare i criteri di archiviazione standard di analisi codice
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 768efb3e874f6427cd23f63f14671aa2db1bea71
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55917077"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Procedura: Creare o aggiornare i criteri di archiviazione standard di analisi codice

È possibile richiedere che l'analisi del codice deve essere eseguito in tutti i progetti di codice in un progetto Azure DevOps usando i criteri di controllo dell'analisi codice. Richiedere l'analisi del codice, è possibile migliorare la qualità del codice che viene archiviata nella codebase.

> [!NOTE]
> Questa funzionalità è disponibile solo se si usa Team Foundation Server.

Criteri di controllo dell'analisi del codice vengono impostati nelle impostazioni del progetto e si applicano a ogni progetto di codice. Esecuzioni dell'analisi del codice sono configurate per i progetti di codice nel file di progetto (con estensione xxproj) per il progetto di codice. Esecuzioni dell'analisi del codice vengono eseguite nel computer locale. Quando si abilita un criterio di controllo dell'analisi codice, file in un progetto di codice che devono essere archiviati devono essere compilati termine dell'ultima modifica e analisi del codice eseguito che contiene, come minimo, le regole nelle impostazioni del progetto devono essere eseguite nel computer in cui la modifica s sono state apportate.

- Per codice gestito, si impostano i criteri di archiviazione specificando una *set di regole* che contiene un sottoinsieme di regole di analisi codice.

- Per codice C/C++, in Visual Studio 2017 versione 15.6 e versioni precedenti, i criteri di controllo richiedono che vengano eseguite tutte le regole di analisi codice. È possibile aggiungere le direttive del preprocessore per disabilitare regole specifiche per singoli progetti di codice nel progetto Azure DevOps. Nella versione 15.7 e successive, è possibile utilizzare **/analyze: ruleset** per specificare le regole da eseguire. Per altre informazioni, vedere [usando i set di regole per specificare le regole C++ da eseguire](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

Dopo aver specificato un criterio di controllo per il codice gestito, i membri del team possono sincronizzare le impostazioni di analisi codice per progetti di codice alle impostazioni dei criteri del progetto DevOps di Azure.

## <a name="to-open-the-check-in-policy-editor"></a>Per aprire l'editor Criteri di archiviazione

1. In Team Explorer, fare clic sul nome del progetto, scegliere **impostazioni del progetto**, quindi fare clic su **controllo del codice sorgente**.

1. Nel **controllo del codice sorgente** finestra di dialogo, seleziona la **dei criteri di archiviazione** scheda.

1. Eseguire una delle operazioni seguenti:

    - Fare clic su **Add** per creare un nuovo criterio di controllo.

    - Fare doppio clic su esistente **analisi del codice** degli elementi nella **tipo di criterio** elenco per modificare i criteri.

## <a name="to-set-policy-options"></a>Per impostare le opzioni dei criteri

Selezionare o deselezionare le opzioni seguenti:

|Opzione|Descrizione|
|------------|-----------------|
|**Consenti archiviazione dei soli file che fanno parte della soluzione corrente.**|Analisi del codice può eseguire solo sui file specificati nel file di configurazione soluzione e progetto. Questo criterio garantisce che tutto il codice che fa parte di una soluzione verrà analizzato.|
|**Applicare analisi del codice C/C++ (/analyze)**|Richiede che tutti i progetti C o C++ deve essere compilato con la /ANALYZE opzione del compilatore per eseguire l'analisi del codice prima che possano essere archiviati.|
|**Applicare l'analisi del codice per il codice gestito**|Richiede che tutti i progetti gestiti Esegui analisi del codice e compilare prima che possano essere archiviati.|

## <a name="to-specify-a-managed-rule-set"></a>Per specificare un set di regole gestite

Dal **eseguire questo set di regole** elencare, usare uno dei metodi seguenti:

- Selezionare un set di regole standard Microsoft.

- Selezionare una regola personalizzata impostata facendo  **\<seleziona Set di regole dal controllo del codice sorgente... >**. Quindi, digitare il percorso controllo della versione della regola impostata nel browser di controllo di origine. La sintassi di un percorso controllo della versione è:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Per altre informazioni su come creare ed implementare una regola di criteri di archiviazione personalizzati, vedere [criteri di controllo implementare personalizzati per codice gestito](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Vedere anche

- [Creare e usare criteri di controllo dell'analisi del codice](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)