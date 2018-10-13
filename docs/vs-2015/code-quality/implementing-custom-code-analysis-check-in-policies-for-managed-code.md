---
title: Implementazione di criteri analisi codice personalizzati Check-in per codice gestito | Microsoft Docs
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
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 82f360bb9dc256fd78a8b06aca66d9e49c57ab22
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268970"
---
# <a name="implementing-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementazione di criteri di archiviazione dell'analisi codice personalizzati per codice gestito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un'analisi del codice dei criteri di archiviazione consente di specificare un set di regole che i membri di un progetto team devono eseguire nel codice sorgente prima che venga verificata controllo della versione. Microsoft offre un set di standard *set di regole* tale analisi del codice di gruppo le regole in aree funzionali. *Set di regole di criteri di archiviazione personalizzati* specificano un set di regole di analisi di codice specifici di un progetto team. Un set di regole viene archiviato in un file con estensione ruleset.  
  
 I criteri di archiviazione vengono impostati a livello di progetto team e specificati dalla posizione di un file con estensione ruleset nella struttura di controllo della versione. Non sono previste restrizioni sul percorso controllo della versione del set di regole personalizzate dei criteri del team.  
  
 Analisi del codice è configurato per singoli progetti di codice nella finestra proprietà per ogni progetto. Una regola personalizzata impostata per un progetto di codice viene specificata dalla posizione fisica del file con estensione ruleset nel computer locale. Quando un file con estensione ruleset viene specificato che si trova nella stessa unità come progetto di codice, Visual Studio Usa un percorso relativo del file di configurazione del progetto.  
  
 Una pratica consigliata per la creazione di un set di regole personalizzate del progetto team consiste nell'archiviare i file con estensione ruleset dei criteri di archiviazione in una cartella speciale che non fa parte di qualsiasi progetto di codice. Se si archivia il file in una cartella dedicata, è possibile applicare le autorizzazioni che limitano l'utilizzo di chi possono modificare il file di regole ed è possibile spostare facilmente la struttura di directory che contiene il progetto da un computer o un'altra directory.  
  
## <a name="creating-the-team-project-custom-check-in-rule-set"></a>La creazione del Set di regole personalizzato Check-in progetto Team  
 Per creare una regola personalizzata impostata per un progetto team, creare innanzitutto una cartella speciale per la regola dei criteri di archiviazione impostata **Esplora controllo codice sorgente**. È quindi possibile creare il file del set di regole e aggiungere il file al controllo della versione. Infine, si specifica il set di regole come il codice check-in Criteri di analisi per il progetto team.  
  
> [!NOTE]
>  Per creare una cartella in un progetto team, è necessario mappare la radice del progetto team in un percorso nel computer locale. Per altre informazioni, vedere [creare e usare aree di lavoro (precedente)](http://msdn.microsoft.com/en-us/db4d5692-179a-44fe-ad31-0c1c900c9cb2).  
  
#### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Per creare la cartella controllo della versione per il set di regole dei criteri di archiviazione  
  
1.  Nelle [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], espandere il nodo del progetto team e quindi fare clic su **controllo del codice sorgente**.  
  
2.  Nel **cartelle** riquadro, fare clic sul progetto team e quindi fare clic su **nuova cartella**.  
  
3.  Nel riquadro di controllo del codice sorgente principale, fare doppio clic su **nuova cartella**, fare clic su **rinominare**e digitare un nome per la regola del set di cartelle.  
  
#### <a name="to-create-the-check-in-policy-rule-set"></a>Per creare il set di regole dei criteri di archiviazione  
  
1.  Nel **File** dal menu **New**, quindi fare clic su **File**.  
  
2.  Nel **categorie** fare clic su **generali**.  
  
3.  Nel **modelli** elenco, fare doppio clic su **Set di regole di analisi codice**.  
  
4.  Specificare le regole da includere nel set di regole e quindi salvare il file del set di regole per la cartella di set di regole creato.  
  
     Per altre informazioni, vedere [la creazione di set di regole personalizzate](../code-quality/creating-custom-code-analysis-rule-sets.md)  
  
#### <a name="to-add-the-rule-set-file-to-version-control"></a>Per aggiungere la regola di set di file al controllo della versione  
  
1.  Nelle **Esplora controllo codice sorgente**, fare doppio clic su nuova cartella e quindi fare clic su **aggiungere elementi alla cartella**.  
  
     Per altre informazioni, vedere [controllo della versione](http://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314).  
  
2.  Scegliere il set di regole file creato e quindi fare clic su **fine**.  
  
     Il file viene aggiunto al controllo del codice sorgente ed estratto automaticamente.  
  
3.  Nel **Esplora controllo codice sorgente** finestra Dettagli, fare doppio clic il nome del file e quindi fare clic su **archiviare modifiche in sospeso**.  
  
4.  Nel **Check-in** della finestra di dialogo è possibile aggiungere un commento e quindi fare clic su **Archivia**.  
  
    > [!NOTE]
    >  Se si è già configurato un criterio di controllo dell'analisi codice per il progetto team ed è stata selezionata la **Consenti archiviazione dei soli file che fanno parte della soluzione corrente**, si attiverà un avviso di errore nel criterio. Nella finestra di dialogo di errore dei criteri, selezionare **ora errore criteri e continua archiviazione**. Aggiungere un commento richiesto e quindi fare clic su **OK**.  
  
#### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Per specificare la regola di set di file come i criteri di controllo  
  
1.  Nel **Team** dal menu **le impostazioni del progetto Team**, quindi fare clic su **controllo del codice sorgente**.  
  
2.  Fare clic su **dei criteri di archiviazione**, quindi fare clic su **Add**.  
  
3.  Nel **dei criteri di archiviazione** elenco, fare doppio clic su **analisi del codice**e assicurarsi che il **Attiva analisi codice per il codice gestito** casella di controllo è selezionata.  
  
4.  Nel **eseguire questo set di regole** fare clic su  **\<seleziona Set di regole dal controllo del codice sorgente >**.  
  
5.  Digitare il percorso del file del set di regole di criteri di archiviazione nel controllo della versione.  
  
     Il percorso deve essere conforme alla sintassi seguente:  
  
     **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    > [!NOTE]
    >  È possibile copiare il percorso usando una delle seguenti procedure in **Esplora controllo codice sorgente**:  
  
    -   Nel **cartelle** riquadro, fare clic sulla cartella che contiene il file del set di regole. Copiare il percorso della cartella in cui viene visualizzato nel controllo della versione di **origine** , quindi digitare il nome del file del set di regole manualmente.  
  
    -   Nella finestra dei dettagli fare doppio clic su file del set di regole e quindi fare clic su **proprietà**. Nel **generali** scheda, copiare il valore nella **nome Server**.  
  
## <a name="synchronizing-code-projects-to-the-check-in-policy-rule-set"></a>Sincronizzazione dei progetti di codice per il Set di regole dei criteri di archiviazione  
 Specificare una regola di criteri di archiviazione di progetti team impostato come il set di regole di analisi codice di una configurazione di progetto di codice nella finestra di dialogo proprietà del progetto di codice. Se il set di regole si trova nella stessa unità come progetto di codice, un percorso relativo viene utilizzato per specificare set di regole se il percorso è selezionato nella finestra di dialogo file. Strutture di controllo Abilita il percorso relativo le impostazioni delle proprietà del progetto sia portabile in altri computer che usano la versione locale simile.  
  
#### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>Per specificare una regola del progetto team impostata come set di regole di un progetto di codice  
  
1.  Se necessario, recuperare la cartella set di regole dei criteri di archiviazione e i file dal controllo della versione.  
  
     È possibile eseguire questo passaggio **Esplora controllo codice sorgente** facendo clic con il set di regole cartella e quindi scegliendo **Leggi ultima versione**.  
  
2.  Nelle **Esplora soluzioni**, fare clic sul progetto codice e quindi fare clic su **proprietà**.  
  
3.  **Fare clic su analisi del codice**.  
  
4.  Se necessario, selezionare le opzioni appropriate nel **Configuration** e **piattaforma** Elenca.  
  
5.  Per eseguire l'analisi del codice ogni volta che il progetto di codice viene compilato utilizzando la configurazione specificata, selezionare la **Abilita analisi codice su compilazione (definisce la costante CODE_ANALYSIS)** casella di controllo.  
  
6.  Per ignorare i codice nei componenti da altre società, selezionare la **non visualizzare i risultati dal codice generato** casella di controllo.  
  
7.  Nel **eseguire questo set di regole** fare clic su  **\<Sfoglia... >**.  
  
8.  Specificare la versione locale del file del set di regole di criteri di archiviazione.



