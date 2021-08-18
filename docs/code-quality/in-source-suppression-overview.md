---
title: Rimuovere le violazioni dell'analisi del codice
ms.date: 05/10/2021
description: Informazioni su come eliminare le violazioni dell'analisi del codice in Visual Studio. Informazioni su come usare l'attributo SuppressMessageAttribute per l'eliminazione nel codice sorgente.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 224de248715a75a3291869f4bc588384f662643f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122067347"
---
# <a name="suppress-code-analysis-violations"></a>Rimuovere le violazioni dell'analisi del codice

Spesso è utile indicare che un avviso non è applicabile. Ciò indica ai membri del team che il codice è stato esaminato e che l'avviso può essere eliminato. Questo articolo descrive i diversi modi per eliminare le violazioni dell'analisi del codice usando l Visual Studio IDE.

::: moniker range=">=vs-2019"

## <a name="suppress-violations-using-the-editorconfig-file"></a>Eliminare le violazioni usando il file EditorConfig

In un **file EditorConfig** impostare la gravità su `none` , ad esempio `dotnet_diagnostic.CA1822.severity = none` . Per aggiungere un file EditorConfig, vedere [Aggiungere un file EditorConfig a un progetto.](../ide/create-portable-custom-editor-options.md#add-and-remove-editorconfig-files)

::: moniker-end

## <a name="suppress-violations-in-source-code"></a>Eliminare le violazioni nel codice sorgente

È possibile eliminare le violazioni nel codice usando una direttiva del preprocessore, la direttiva [#pragma warning (C#)](/dotnet/csharp/language-reference/preprocessor-directives.md#pragma-warning) o [Disable (Visual Basic)](/dotnet/visual-basic/language-reference/directives/disable-enable.md) per eliminare l'avviso solo per una riga di codice specifica. In caso contrario, è possibile usare [l'attributo SuppressMessage](#in-source-suppression-and-the-suppressmessage-attribute).

- **Dall'editor di codice**

  Posizionare il cursore nella riga di codice con la violazione e premere **CTRL** + **PUNTO (.)** per aprire il menu **Azioni** rapide. Selezionare **Suppress CAXXXX (Elimina CAXXXX)** e quindi **scegliere in Source (Origine)** **o In Source (attribute) (Origine - attributo).**

  Se si sceglie **in Origine**, viene visualizzata un'anteprima della direttiva per il preprocessore che verrà aggiunta al codice.

  ::: moniker range="vs-2017"
  :::image type="content" source="media/suppress-diagnostic-from-editor.png" alt-text="Eliminare la diagnostica dal menu Azioni rapide":::
  ::: moniker-end
  ::: moniker range=">=vs-2019"
  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor.png" alt-text="Eliminare la diagnostica dal menu Azioni rapide":::

  Se si sceglie **origine (attributo),** viene visualizzata un'anteprima dell'attributo [SuppressMessage](#in-source-suppression-and-the-suppressmessage-attribute) che verrà aggiunto al codice.

  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor-attribute.png" alt-text="Eliminare la diagnostica dal menu Azioni rapide usando l'attributo":::
  ::: moniker-end

- **Dall'Elenco errori**

  Selezionare le regole da eliminare, quindi fare clic con il pulsante destro del mouse e **scegliere Elimina**  >  **nell'origine.**

  - Se si elimina Nell'origine **,** viene visualizzata la finestra di dialogo Anteprima modifiche [](/dotnet/visual-basic/language-reference/directives/directives) che mostra un'anteprima dell'avviso #pragma C# o della direttiva di avviso  [#Disable](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) Visual Basic aggiunta al codice sorgente.

    ![Anteprima dell'aggiunta #pragma avviso nel file di codice](media/pragma-warning-preview.png)

  Nella finestra **di dialogo Anteprima** modifiche selezionare **Applica.**

  > [!NOTE]
  > Se non viene visualizzata l'opzione di **menu** **Elimina** in Esplora soluzioni , è probabile che la violazione proviene dalla compilazione e non dall'analisi in tempo reale. **L'Elenco errori** visualizza la diagnostica, o violazioni delle regole, sia dall'analisi del codice in tempo reale che dalla compilazione. Poiché la diagnostica di compilazione può essere obsoleta, ad esempio se è stato modificato il codice per correggere la violazione ma non è stato ricompilato, non è possibile eliminare la diagnostica dall'Elenco **errori**. La diagnostica dall'analisi in tempo reale, o IntelliSense, è sempre aggiornata con le origini correnti e può essere eliminata **dall'Elenco errori**. Per escludere *la diagnostica* di  compilazione dalla selezione, impostare il filtro origine Elenco errori da Compilazione **+ IntelliSense** a Solo **IntelliSense.** Selezionare quindi la diagnostica che si vuole eliminare e procedere come descritto in precedenza.
  >
  > ![Filtro di origine elenco errori in Visual Studio](media/error-list-filter.png)

## <a name="suppress-violations-using-a-global-suppression-file"></a>Eliminare le violazioni usando un file di eliminazione globale

Il [file di eliminazione globale](#global-level-suppressions) usa l'attributo [SuppressMessage](#in-source-suppression-and-the-suppressmessage-attribute).

- In **Elenco errori selezionare** le regole da eliminare, quindi fare clic con il pulsante destro del mouse e scegliere Elimina in File  >  **di eliminazione**. Verrà **visualizzata la finestra** di dialogo Anteprima modifiche che mostra <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> un'anteprima dell'attributo aggiunto al file delle eliminazioni globali.

  ![Anteprima dell'aggiunta dell'attributo SuppressMessage al file di eliminazione](media/preview-changes-in-suppression-file.png)

- **Nell'editor** di codice posizionare il cursore nella riga di codice con la violazione e premere Azioni rapide e **refactoring** (o premere **CTRL** + **PUNTO (.)**) per aprire il menu Azioni rapide.  Selezionare **Suppress CAXXXX (Elimina CAXXXX)** e quindi **scegliere in Suppression File (File di eliminazione).** Verrà visualizzata un'anteprima del [file di eliminazione](#global-level-suppressions) globale che verrà creato o modificato.

::: moniker range=">=vs-2019"

- Dal menu **Analizza** selezionare **Analizza** compilazione ed Elimina problemi attivi sulla barra dei menu per eliminare tutte le violazioni  >   correnti. Questa operazione viene talvolta definita "baselining".

::: moniker-end
::: moniker range="vs-2017"

- Dal menu **Analizza** selezionare Analizza Esegui **Code Analysis** elimina problemi attivi sulla barra dei menu per eliminare  >   tutte le violazioni correnti. Questa operazione viene talvolta definita "baselining".
::: moniker-end

## <a name="suppress-violations-using-project-settings"></a>Eliminare le violazioni usando le impostazioni del progetto

Da **Esplora soluzioni** aprire le proprietà per il progetto **(fare** clic con il pulsante destro del mouse sul progetto e scegliere Proprietà (o **premere ALT+INVIO)** e usare la scheda Code Analysis **per** configurare le opzioni. Ad esempio, è possibile disabilitare l'analisi del codice in tempo reale o disabilitare gli analizzatori .NET.

## <a name="suppress-violations-using-a-rule-set"></a>Eliminare le violazioni usando un set di regole

**Nell'editor del set di** regole deselezionare la casella di controllo accanto al nome o impostare **Azione** **su Nessuno.**

## <a name="in-source-suppression-and-the-suppressmessage-attribute"></a>Eliminazione nel codice sorgente e attributo SuppressMessage

L'eliminazione nel codice sorgente (ISS) usa <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> l'attributo per eliminare un avviso. L'attributo può essere posizionato vicino al segmento di codice che ha generato l'avviso. È possibile aggiungere l'attributo al file di origine digitandolo oppure usare il menu di scelta rapida in un avviso in Elenco errori <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> per aggiungerlo  automaticamente.

L'attributo è un attributo condizionale, incluso nei metadati IL dell'assembly di codice gestito, solo se il simbolo di compilazione CODE_ANALYSIS è definito <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> in fase di compilazione.

In C++/CLI usare le macro CA SUPPRESS MESSAGE o CA GLOBAL SUPPRESS_MESSAGE nel file di intestazione \_ \_ per aggiungere \_ \_ l'attributo .

> [!NOTE]
> È consigliabile non usare le eliminazioni nel codice sorgente nelle build di rilascio, per impedire la spedizione accidentale dei metadati di eliminazione nel codice sorgente. Inoltre, a causa del costo di elaborazione dell'eliminazione nel codice sorgente, le prestazioni dell'applicazione possono risultare ridotte.

::: moniker range="vs-2017"

> [!NOTE]
> Se si esegue la migrazione di un progetto Visual Studio 2017, si potrebbero improvvisamente verificare numerosi avvisi di analisi del codice. Se non si è pronti per correggere gli avvisi, è possibile sopprimerli tutti selezionando Analizza e Code Analysis  >  **elimina problemi attivi.**
>
> ![Eseguire l'analisi del codice ed eliminare i problemi Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Se si esegue la migrazione di un progetto Visual Studio 2019, si potrebbero improvvisamente verificare numerosi avvisi di analisi del codice. Se non si è pronti per correggere gli avvisi, è possibile sopprimerli tutti selezionando **Analizza** compilazione  >  **ed Elimina problemi attivi.**

::: moniker-end

### <a name="suppressmessage-attribute"></a>SuppressMessage (attributo)

Quando si  seleziona Elimina dal menu di scelta rapida o si fa clic con il pulsante destro del mouse su un avviso di analisi del codice nell'Elenco errori **,** viene aggiunto un attributo nel codice o nel file di eliminazione globale <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> del progetto.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>L'attributo ha il formato seguente:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Le proprietà dell'attributo includono:

- **Categoria:** categoria in cui è definita la regola. Per altre informazioni sulle categorie di regole di analisi del codice, vedere [Avvisi del codice gestito.](/dotnet/fundamentals/code-analysis/quality-rules/index)

- **CheckId:** identificatore della regola. Il supporto include sia un nome breve che un nome lungo per l'identificatore della regola. Il nome breve è CAXXXX. il nome lungo è CAXXXX:FriendlyTypeName.

- **Giustificazione:** testo usato per documentare il motivo dell'eliminazione del messaggio.

- **MessageId:** identificatore univoco di un problema per ogni messaggio.

- **Ambito:** la destinazione in cui viene eliminato l'avviso. Se la destinazione non è specificata, viene impostata sulla destinazione dell'attributo . Gli [ambiti supportati](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) includono:

  - [`module`](#module-suppression-scope) - Questo ambito elimina gli avvisi relativi a un assembly. Si tratta di un'eliminazione globale che si applica all'intero progetto.

  - `resource` -[(solo FxCop legacy)](../code-quality/static-code-analysis-for-managed-code-overview.md) Questo ambito elimina gli avvisi nelle informazioni di diagnostica scritte nei file di risorse che fanno parte del modulo (assembly). Questo ambito non viene letto/rispettato nei compilatori C#/VB per la diagnostica dell'analizzatore Roslyn, che analizza solo i file di origine.

  - `type` - Questo ambito elimina gli avvisi relativi a un tipo.

  - `member` - Questo ambito elimina gli avvisi relativi a un membro.

  - `namespace` - Questo ambito elimina gli avvisi per lo spazio dei nomi stesso. Non elimina gli avvisi relativi ai tipi all'interno dello spazio dei nomi .

  - `namespaceanddescendants`- (Richiede la versione 3.x o successiva del compilatore e Visual Studio 2019) Questo ambito elimina gli avvisi in uno spazio dei nomi e in tutti i relativi simboli discendenti. Il `namespaceanddescendants` valore viene ignorato dall'analisi legacy.

- **Destinazione:** identificatore usato per specificare la destinazione in cui viene eliminato l'avviso. Deve contenere un nome di elemento completo.

Quando vengono visualizzati avvisi in Visual Studio, è possibile visualizzare esempi di aggiungendo un'eliminazione `SuppressMessage` al file di eliminazione [globale](../code-quality/use-roslyn-analyzers.md#suppress-violations). L'attributo di eliminazione e le relative proprietà obbligatorie vengono visualizzati in una finestra di anteprima.

### <a name="suppressmessage-usage"></a>Utilizzo di SuppressMessage

Code Analysis avvisi vengono eliminati al livello a cui viene <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> applicato l'attributo. Ad esempio, l'attributo può essere applicato a livello di assembly, modulo, tipo, membro o parametro. Lo scopo di questa operazione è quello di accoppiare strettamente le informazioni di eliminazione al codice in cui si verifica la violazione.

La forma generale di eliminazione include la categoria della regola e un identificatore di regola, che contiene una rappresentazione leggibile facoltativa del nome della regola. Esempio:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Se esistono rigidi motivi di prestazioni per ridurre al minimo i metadati di eliminazione nell'origine, il nome della regola può essere omesso. La categoria di regole e il relativo ID regola insieme costituiscono un identificatore di regola sufficientemente univoco. Esempio:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Per motivi di manutenibilità, non è consigliabile omettere il nome della regola.

### <a name="suppress-selective-violations-within-a-method-body"></a>Eliminare le violazioni selettive all'interno del corpo di un metodo

Gli attributi di eliminazione possono essere applicati a un metodo, ma non possono essere incorporati all'interno di un corpo del metodo. Ciò significa che tutte le violazioni di una determinata regola vengono soppresse se si aggiunge <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> l'attributo al metodo .

In alcuni casi può essere necessario eliminare una particolare istanza della violazione, ad esempio in modo che il codice futuro non sia automaticamente esente dalla regola di analisi del codice. Alcune regole di analisi del codice consentono di eseguire questa operazione usando la `MessageId` proprietà <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> dell'attributo . In generale, le regole legacy per le violazioni su un simbolo specifico (una variabile locale o un parametro) rispettano la `MessageId` proprietà . [CA1500:VariableNamesShouldNotMatchFieldNames è](../code-quality/ca1500.md) un esempio di tale regola. Tuttavia, le regole legacy per le violazioni nel codice eseguibile (non simbolo) non rispettano la `MessageId` proprietà . Inoltre, .NET Compiler Platform analizzatori ("Roslyn") non rispettano la `MessageId` proprietà .

Per eliminare una particolare violazione del simbolo di una regola, specificare il nome del simbolo per `MessageId` la proprietà <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> dell'attributo. L'esempio seguente illustra il codice con due violazioni di [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md)uno per la variabile e &mdash; uno per la variabile `name` `age` . Viene eliminata solo la `age` violazione per il simbolo.

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

### <a name="global-level-suppressions"></a>Eliminazioni a livello globale

Lo strumento di analisi del codice gestito esamina gli attributi applicati a livello di `SuppressMessage` assembly, modulo, tipo, membro o parametro. Inoltre, genera violazioni alle risorse e allo spazio dei nomi. Queste violazioni devono essere applicate a livello globale e sono con ambito e destinazione. Ad esempio, il messaggio seguente elimina una violazione dello spazio dei nomi:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Quando si elimina un avviso con ambito, l'avviso viene eliminato `namespace` sullo spazio dei nomi stesso. Non elimina l'avviso per i tipi all'interno dello spazio dei nomi .

Qualsiasi eliminazione può essere espressa specificando un ambito esplicito. Queste eliminazioni devono essere live a livello globale. Non è possibile specificare l'eliminazione a livello di membro decorando un tipo.

Le eliminazioni a livello globale sono l'unico modo per eliminare i messaggi che fanno riferimento a codice generato dal compilatore che non esegue il mapping all'origine utente specificata in modo esplicito. Ad esempio, il codice seguente elimina una violazione rispetto a un costruttore generato dal compilatore:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` contiene sempre il nome completo dell'elemento.

#### <a name="global-suppression-file"></a>File di eliminazione globale

Il file di eliminazione globale mantiene le eliminazioni che sono eliminazioni a livello globale o eliminazioni che non specificano una destinazione. Ad esempio, le soppressioni per le violazioni a livello di assembly vengono archiviate in questo file. Inoltre, alcune ASP.NET vengono archiviate in questo file perché le impostazioni a livello di progetto non sono disponibili per il code-behind di un modulo. Un file di eliminazione globale viene creato e aggiunto al progetto la prima volta che  si seleziona l'opzione In **Project Suppression File** del comando Elimina nella finestra **Elenco** errori.

#### <a name="module-suppression-scope"></a>Ambito di eliminazione dei moduli

È possibile eliminare le violazioni della qualità del codice per l'intero assembly usando **l'ambito del** modulo.

Ad esempio, l'attributo seguente nel file di progetto _GlobalSuppressions_ elimina la violazione ConfigureAwait per un ASP.NET Core progetto:

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

### <a name="generated-code"></a>Codice generato

I compilatori di codice gestito e alcuni strumenti di terze parti generano codice per facilitare lo sviluppo rapido del codice. Il codice generato dal compilatore visualizzato nei file di origine è in genere contrassegnato con `GeneratedCodeAttribute` l'attributo .

Per l'analisi del codice sorgente, è possibile eliminare i messaggi nel codice generato in un `.editorconfig` file. Per altre informazioni, vedere [Escludere il codice generato.](/dotnet/fundamentals/code-analysis/configuration-options#exclude-generated-code)

Per l'analisi del codice legacy, è possibile scegliere se eliminare gli avvisi e gli errori di analisi del codice generato. Per informazioni su come eliminare tali avvisi ed errori, vedere [Procedura: Eliminare avvisi per il codice generato](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> L'analisi del `GeneratedCodeAttribute` codice viene ignorata quando viene applicata a un intero assembly o a un singolo parametro.

## <a name="see-also"></a>Vedi anche

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Usare gli analizzatori del codice](../code-quality/use-roslyn-analyzers.md)
