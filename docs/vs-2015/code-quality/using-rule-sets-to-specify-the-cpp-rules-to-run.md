---
title: Utilizzo di set di regole per specificare le regole C++ da eseguire | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: ff105af1d817613b324e1158130457eb906c753f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277860"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>Utilizzo di set di regole per specificare le regole C++ da eseguire
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] e [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] è possibile creare e modificare un set di *regole* personalizzato per soddisfare esigenze specifiche del progetto associate all'analisi del codice. Per creare un set di regole C++ personalizzato, è necessario aprire un progetto C/C++ nell'IDE di Visual Studio. Si apre quindi un set di regole standard nell'editor del set di regole e quindi si aggiungono o rimuovono regole specifiche e, facoltativamente, si modifica l'azione che si verifica quando l'analisi del codice determina che una regola è stata violata.  
  
 Per creare un nuovo set di regole personalizzate, salvarlo con un nuovo nome file. Il set di regole personalizzate viene assegnato automaticamente al progetto.  
  
## <a name="opening-the-rule-set-editor"></a>Apertura dell'editor set di regole  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Per creare una regola personalizzata da un singolo set di regole esistente  
  
1. In Esplora soluzioni aprire il menu di scelta rapida per il progetto, quindi scegliere **Proprietà**.  
  
2. Nella scheda **Proprietà** scegliere **analisi codice**.  
  
3. Nell'elenco a discesa **set di regole** effettuare una delle operazioni seguenti:  
  
   - Scegliere il set di regole che si desidera personalizzare.  
  
     \- - oppure -  
  
   - Scegliere **\<Browse...>** di specificare un set di regole esistente non presente nell'elenco.  
  
4. Scegliere **Apri** per visualizzare le regole nell'Editor set di regole.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Per modificare un set di regole nell'Editor set di regole  
  
- Per modificare il nome visualizzato del set di regole, scegliere **finestra Proprietà**dal menu **Visualizza** . Immettere il nome visualizzato nella casella **nome** . Si noti che il nome visualizzato può essere diverso dal nome del file.  
  
- Per aggiungere tutte le regole del gruppo a un set di regole personalizzate, selezionare la casella di controllo del gruppo. Per rimuovere tutte le regole del gruppo, deselezionare la casella di controllo.  
  
- Per aggiungere una regola specifica al set di regole personalizzate, selezionare la casella di controllo relativa alla regola. Per rimuovere la regola dal set di regole, deselezionare la casella di controllo.  
  
- Per modificare l'azione eseguita quando una regola viene violata in un'analisi del codice, scegliere il campo **azione** per la regola, quindi scegliere uno dei valori seguenti:  
  
     **Warn** : genera un avviso.  
  
     **Errore** : genera un errore.  
  
     **None** : Disabilita la regola. Questa azione equivale a rimuovere la regola dal set di regole.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Per raggruppare, filtrare o modificare i campi nell'editor del set di regole tramite la barra degli strumenti Editor set di regole  
  
- Per espandere le regole in tutti i gruppi, scegliere **Espandi tutto**.  
  
- Per comprimere le regole in tutti i gruppi, scegliere **Comprimi tutto**.  
  
- Per modificare il campo in base al quale vengono raggruppate le regole, scegliere il campo dall'elenco **Raggruppa per** . Per visualizzare le regole non raggruppate, scegliere **\<None>** .  
  
- Per aggiungere o rimuovere campi nelle colonne della regola, scegliere **Opzioni colonne**.  
  
- Per nascondere le regole che non si applicano alla soluzione corrente, scegliere **Nascondi regole che non si applicano alla soluzione corrente**.  
  
- Per passare tra le regole di visualizzazione e di occultamento a cui è stata assegnata l'azione di errore, scegliere **Mostra regole che possono generare errori di analisi del codice**.  
  
- Per passare tra le regole di visualizzazione e di occultamento a cui è stata assegnata l'azione di avviso, scegliere **Mostra regole che possono generare avvisi di analisi del codice**.  
  
- Per passare tra le regole di visualizzazione e di occultamento a cui è stata assegnata l'azione **Nessuna** , scegliere **Mostra regole non abilitate**.  
  
- Per aggiungere o rimuovere set di regole predefinite di Microsoft sul set di regole corrente, scegliere **Aggiungi o Rimuovi set di regole figlio**.
