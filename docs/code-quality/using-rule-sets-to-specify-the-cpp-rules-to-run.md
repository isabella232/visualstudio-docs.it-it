---
title: Utilizzo di set di regole per specificare le regole C++ da eseguire
ms.date: 04/28/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: d4d7dfc1f010b860653edbe14fa7af9050bddba4
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2019
ms.locfileid: "57323653"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Usare set di regole per specificare le regole C++ da eseguire

In Visual Studio, è possibile creare e modificare un oggetto personalizzato *set di regole* per soddisfare specifiche esigenze del progetto associate con l'analisi del codice. Il set di regole predefinite vengono archiviati in `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`.

**Visual Studio 2017 versione 15.7 e successive** è possibile creare set di regole personalizzate utilizzando il testo dell'editor e applicarli nelle compilazioni della riga di comando indipendentemente da cosa compilare sistema in uso. Per altre informazioni, vedere [/analyze: ruleset](/cpp/build/reference/analyze-code-analysis).

Per creare una regola personalizzata di C++ imposta in Visual Studio, un progetto C/C++ deve essere aperto nell'IDE di Visual Studio. Quindi aprire un set di regole standard in editor set di regole e quindi aggiungere o rimuovere regole specifiche e, facoltativamente, modificare l'azione che si verifica quando l'analisi del codice determina che è stata violata una regola.

Per creare una nuova regola personalizzata impostata, è necessario salvarlo con un nuovo nome file. Il set di regole personalizzato viene assegnato automaticamente al progetto.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Per creare una regola personalizzata da un singolo set di regole esistente

1. In Esplora soluzioni aprire il menu di scelta rapida per il progetto e quindi scegliere **proprietà**.

2. Nel **delle proprietà** scheda, scegliere **analisi del codice**.

3. Nel **del Set di regole** riepilogo, effettuare una delle operazioni seguenti:

   - Scegliere il set di regole che si desidera personalizzare.

     \- oppure -

   - Scegli  **\<Sfoglia >** per specificare set di una regola esistente non incluso nell'elenco.

4. Scegli **aperto** per visualizzare le regole nell'editor set di regole.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Per modificare una regola impostata nell'editor set di regole

- Per modificare il nome visualizzato del set di regole, scegliere il **View** menu, scegliere **finestra proprietà**. Immettere il nome visualizzato nei **nome** casella. Si noti che il nome visualizzato può essere diverso dal nome del file.

- Per aggiungere tutte le regole del gruppo a un set di regole personalizzate, selezionare la casella di controllo del gruppo. Per rimuovere tutte le regole del gruppo, deselezionare la casella di controllo.

- Per aggiungere una regola specifica per il set di regole personalizzate, selezionare la casella di controllo della regola. Per rimuovere la regola dal set di regole, deselezionare la casella di controllo.

- Per modificare l'azione eseguita quando viene violata una regola in un'analisi del codice, scegliere il **azione** campo per la regola e quindi scegliere uno dei valori seguenti:

     **Avvisa** -genera un avviso.

     **Errore** -verrà generato un errore.

     **Nessuno** -disabilita la regola. Questa azione è quello utilizzato per la rimozione della regola dal set di regole.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Per raggruppare, filtrare o modificare i campi nell'editor set di regole utilizzando la barra degli strumenti editor set di regole

- Per espandere le regole in tutti i gruppi, scegliere **Espandi tutto**.

- Per comprimere le regole in tutti i gruppi, scegliere **Comprimi tutto**.

- Per modificare il campo che le regole vengono raggruppate, scegliere il campo dal **Group By** elenco. Per visualizzare le regole separate, scegli  **\<None >**.

- Per aggiungere o rimuovere i campi nelle colonne della regola, scegliere **opzioni di colonna**.

- Per nascondere le regole che non si applicano alla soluzione corrente, scegliere **nascondere le regole che non si applicano alla soluzione corrente**.

- Per passare da visualizzare e nascondere le regole che vengono assegnate l'azione di errore, scegliere **Mostra regole che possono generare errori di analisi codice**.

- Per passare da visualizzare e nascondere le regole di cui sono assegnate l'azione di avviso, scegliere **Mostra regole che possono generare avvisi di analisi codice**.

- Per alternare mostrando e nascondendo le regole che vengono assegnate le **None** azione, scegliere **Mostra regole che non sono abilitate**.

- Per aggiungere o rimuovere set di regole predefinito per il set di regole corrente di Microsoft, scegli **Aggiungi o Rimuovi set di regole figlio**.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>Per creare una set di regole in un editor di testo

È possibile creare un set di regole personalizzate in un testo dell'editor, archiviarlo in qualsiasi posizione con un `.ruleset` estensione e applicare con il [/analyze: ruleset](/cpp/build/reference/analyze-code-analysis) opzione del compilatore.

L'esempio seguente illustra che una regola di base Imposta file che è possibile usare come punto di partenza:

::: moniker range="vs-2017"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end
