---
title: "Procedura: creare o aggiornare criteri di controllo dell'analisi del codice Standard | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6821d218c22f2d83108205d8753fc2d5beac4f28
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939436"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Procedura: Creare o aggiornare criteri di archiviazione standard dell'analisi del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile richiedere che l'analisi del codice deve essere eseguito in tutti i progetti di codice in un progetto team usando i criteri di controllo dell'analisi codice. Richiedere l'analisi del codice, è possibile migliorare la qualità del codice che viene archiviata nella codebase.  
  
> [!NOTE]
>  Questa funzionalità è disponibile solo se si usa Team Foundation Server.  
  
 Criteri di controllo dell'analisi del codice vengono impostati nelle impostazioni del progetto team e si applicano a ogni progetto di codice nel progetto team. Esecuzioni dell'analisi del codice sono configurate per i progetti di codice nel file di progetto (con estensione xxproj) per il progetto di codice. Esecuzioni dell'analisi del codice vengono eseguite nel computer locale. Quando si abilita un criterio di controllo dell'analisi codice, file in un progetto di codice che devono essere archiviati devono essere compilati termine dell'ultima modifica e analisi del codice eseguito che contiene, come minimo, le regole nelle impostazioni del progetto team devono essere eseguite nel computer in cui il c sono state apportate modifiche in sospeso.  
  
- Per codice gestito, si impostano i criteri di archiviazione specificando una *set di regole* che contiene un sottoinsieme di regole di analisi codice.  
  
- Per codice C/C++, i criteri di controllo richiedono che vengano eseguite tutte le regole di analisi codice. È possibile aggiungere le direttive del preprocessore per disabilitare regole specifiche per singoli progetti di codice nel progetto team.  
  
  Dopo aver specificato un criterio di controllo per il codice gestito, i membri del team possono sincronizzare le impostazioni di analisi codice per progetti di codice alle impostazioni dei criteri del progetto team.  
  
### <a name="to-open-the-check-in-policy-editor"></a>Per aprire l'editor Criteri di archiviazione  
  
1.  In Team Explorer, fare clic sul nome del progetto team, scegliere **le impostazioni del progetto Team**, quindi fare clic su **controllo del codice sorgente**.  
  
2.  Nel **controllo del codice sorgente** finestra di dialogo, seleziona la **dei criteri di archiviazione** scheda.  
  
3.  Eseguire una delle operazioni seguenti:  
  
    -   Fare clic su **Add** per creare un nuovo criterio di controllo.  
  
    -   Fare doppio clic su esistente **analisi del codice** degli elementi nella **tipo di criterio** elenco per modificare i criteri.  
  
### <a name="to-set-policy-options"></a>Per impostare le opzioni dei criteri  
  
-   Selezionare o deselezionare le opzioni seguenti:  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |**Consenti archiviazione dei soli file che fanno parte della soluzione corrente.**|Analisi del codice può eseguire solo sui file specificati nel file di configurazione soluzione e progetto. Questo criterio garantisce che tutto il codice che fa parte di una soluzione verrà analizzato.|  
    |**Applicare analisi del codice C/C++ (/analyze)**|Richiede che tutti i progetti C o C++ deve essere compilato con la /ANALYZE opzione del compilatore per eseguire l'analisi del codice prima che possano essere archiviati.|  
    |**Applicare l'analisi del codice per il codice gestito**|Richiede che tutti i progetti gestiti Esegui analisi del codice e compilare prima che possano essere archiviati.|  
  
-  
  
### <a name="to-specify-a-managed-rule-set"></a>Per specificare un set di regole gestite  
  
-   Dal **eseguire questo set di regole** elencare, usare uno dei metodi seguenti:  
  
    -   Selezionare un set di regole standard Microsoft.  
  
    -   Per selezionare un set di regole personalizzato, fare clic su  **\<seleziona Set di regole dal controllo del codice sorgente... >**, quindi digitare il percorso controllo della versione della regola impostata nel browser di controllo di origine. La sintassi di un percorso controllo della versione è:  
  
    -   **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    -   Per altre informazioni su come creare ed implementare una regola di criteri di archiviazione personalizzati, vedere [criteri di controllo che implementa personalizzati per codice gestito](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione e uso di criteri di archiviazione di analisi codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)



