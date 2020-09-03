---
title: "Procedura: creare o aggiornare criteri di archiviazione standard dell'analisi del codice | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5e8016032a0ea8d1b8c62b2dfc2bbdf72251590c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661782"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Procedura: Creare o aggiornare criteri di archiviazione standard dell'analisi del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile richiedere l'esecuzione dell'analisi del codice in tutti i progetti di codice in un progetto team usando i criteri di archiviazione dell'analisi del codice. La richiesta di analisi del codice può migliorare la qualità del codice archiviato nella codebase.

> [!NOTE]
> Questa funzionalità è disponibile solo se si usa Team Foundation Server.

 I criteri di archiviazione dell'analisi codice sono impostati nelle impostazioni del progetto team e si applicano a ogni progetto di codice nel progetto team. Le esecuzioni dell'analisi del codice sono configurate per i progetti di codice nel file di progetto (con estensione xxproj) per il progetto di codice. Le esecuzioni dell'analisi del codice vengono eseguite nel computer locale. Quando si Abilita un criterio di archiviazione dell'analisi del codice, i file in un progetto di codice da archiviare devono essere compilati dopo l'ultima modifica e un'esecuzione dell'analisi del codice che contiene almeno le regole nelle impostazioni del progetto team devono essere eseguite nel computer in cui sono state apportate le modifiche.

- Per il codice gestito, è possibile impostare i criteri di archiviazione specificando un *set* di regole contenente un subset delle regole di analisi del codice.

- Per il codice C/C++, i criteri di archiviazione richiedono l'esecuzione di tutte le regole di analisi del codice. È possibile aggiungere direttive del pre-processore per disabilitare regole specifiche per i singoli progetti di codice nel progetto team.

  Dopo aver specificato i criteri di archiviazione per il codice gestito, i membri del team possono sincronizzare le impostazioni di analisi del codice per i progetti di codice nelle impostazioni dei criteri del progetto team.

### <a name="to-open-the-check-in-policy-editor"></a>Per aprire l'editor dei criteri di archiviazione

1. In Team Explorer fare clic con il pulsante destro del mouse sul nome del progetto team, scegliere **Impostazioni progetto team**, quindi fare clic su **controllo del codice sorgente**.

2. Nella finestra di dialogo **controllo del codice sorgente** selezionare la scheda **criteri di archiviazione** .

3. Eseguire una delle operazioni seguenti:

    - Fare clic su **Aggiungi** per creare nuovi criteri di archiviazione.

    - Fare doppio clic sull'elemento di **analisi del codice** esistente nell'elenco tipo di **criteri** per modificare il criterio.

### <a name="to-set-policy-options"></a>Per impostare le opzioni dei criteri

- Selezionare o deselezionare le opzioni seguenti:

    |Opzione|Descrizione|
    |------------|-----------------|
    |**Applicare l'archiviazione per contenere solo i file che fanno parte della soluzione corrente.**|L'analisi del codice può essere eseguita solo su file specificati nei file di configurazione della soluzione e del progetto. Questo criterio garantisce che tutto il codice che fa parte di una soluzione venga analizzato.|
    |**Applicare l'analisi codice C/C++ (/Analyze)**|Richiede che tutti i progetti C o C++ siano compilati con l'opzione del compilatore/analyze per eseguire l'analisi del codice prima di poterli archiviare.|
    |**Imponi analisi codice per codice gestito**|Richiede che tutti i progetti gestiti eseguano l'analisi del codice e vengano compilati prima di poterli archiviare.|

-

### <a name="to-specify-a-managed-rule-set"></a>Per specificare un set di regole gestite

- Dall'elenco **Esegui questo set di regole** , usare uno dei metodi seguenti:

  - Selezionare un set di regole standard Microsoft.

  - Per selezionare un set di regole personalizzato, fare clic su **\<Select Rule Set from Source Control...>** , quindi digitare il percorso del controllo della versione del set di regole nel Visualizzatore del controllo del codice sorgente. La sintassi di un percorso di controllo della versione è la seguente:

  - **$/** `TeamProjectName` **/** `VersionControlPath`

  - Per ulteriori informazioni su come creare e implementare un set di regole dei criteri di archiviazione personalizzato, vedere [implementazione di criteri di archiviazione personalizzati per il codice gestito](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Vedere anche
 [Creazione e utilizzo di criteri di archiviazione di analisi codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
