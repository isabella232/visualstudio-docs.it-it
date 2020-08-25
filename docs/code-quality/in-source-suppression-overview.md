---
title: Non visualizzare gli avvisi di analisi codice
ms.date: 12/01/2018
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: f1cc2fd460a2087eaaac40abbb1ba04c8126a9aa
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800853"
---
# <a name="suppress-code-analysis-warnings"></a>Non visualizzare gli avvisi di analisi codice

Spesso è utile indicare che un avviso non è applicabile. Ciò indica ai membri del team che il codice è stato esaminato e che l'avviso può essere eliminato. L'eliminazione nell'origine (ISS) usa l' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo per non visualizzare un avviso. L'attributo può essere inserito vicino al segmento di codice che ha generato l'avviso. È possibile aggiungere l' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo al file di origine digitando l'attributo oppure è possibile utilizzare il menu di scelta rapida di un avviso nel **Elenco errori** per aggiungerlo automaticamente.

L' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo è un attributo condizionale, incluso nei metadati il dell'assembly del codice gestito, solo se il CODE_ANALYSIS simbolo di compilazione viene definito in fase di compilazione.

In C++/CLI, usare la CA macro non \_ visualizzare \_ messaggi o ca \_ globale \_ SUPPRESS_MESSAGE nel file di intestazione per aggiungere l'attributo.

> [!NOTE]
> Non è consigliabile usare le eliminazioni in origine nelle build di rilascio, per impedire che vengano inviati accidentalmente i metadati di eliminazione nell'origine. Inoltre, a causa del costo di elaborazione dell'eliminazione nell'origine, le prestazioni dell'applicazione possono risultare ridotte.

::: moniker range="vs-2017"

> [!NOTE]
> Se si esegue la migrazione di un progetto a Visual Studio 2017, è possibile che si facciano improvvisamente molti avvisi di analisi del codice. Se non si è pronti per correggere gli avvisi, è possibile eliminarli tutti selezionando **analizza**  >  **Esegui analisi codice ed elimina problemi attivi**.
>
> ![Eseguire l'analisi del codice ed escludere i problemi in Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Se si esegue la migrazione di un progetto a Visual Studio 2019, è possibile che si facciano improvvisamente molti avvisi di analisi del codice. Se non si è pronti per correggere gli avvisi, è possibile eliminarli tutti selezionando **analizza**  >  **compilazione ed elimina problemi attivi**.

::: moniker-end

## <a name="suppressmessage-attribute"></a>SuppressMessage (attributo)

Quando si seleziona **Elimina** dal menu di scelta rapida o si fa clic con il pulsante destro del mouse o si seleziona e si tiene presente un messaggio di avviso di analisi del codice nella **Elenco errori**, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> viene aggiunto un attributo nel codice o nel file di eliminazione globale del progetto.

Il <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> formato dell'attributo è il seguente:

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

- **Category** : la categoria in cui è definita la regola. Per ulteriori informazioni sulle categorie di regole di analisi del codice, vedere [avvisi del codice gestito](../code-quality/code-analysis-for-managed-code-warnings.md).

- **CheckId** : identificatore della regola. Il supporto include un nome breve e lungo per l'identificatore della regola. Il nome breve è CAXXXX; il nome lungo è CAXXXX: FriendlyTypeName.

- **Giustificazione** : testo utilizzato per documentare il motivo dell'eliminazione del messaggio.

- **MessageID** : identificatore univoco di un problema per ogni messaggio.

- **Ambito** : destinazione in cui viene eliminato l'avviso. Se la destinazione non è specificata, viene impostata sulla destinazione dell'attributo. Gli [ambiti](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) supportati sono i seguenti:

  - [`module`](#module-suppression-scope) -Questo ambito evita gli avvisi rispetto a un assembly. Si tratta di un'eliminazione globale che si applica all'intero progetto.

  - `resource` -(solo[FxCop legacy](../code-quality/static-code-analysis-for-managed-code-overview.md) ) questo ambito evita gli avvisi nelle informazioni di diagnostica scritte nei file di risorse che fanno parte del modulo (assembly). Questo ambito non è leggibile/rispettabile nei compilatori C#/VB per la diagnostica di Roslyn Analyzer, che analizza solo i file di origine.

  - `type` -Questo ambito evita gli avvisi rispetto a un tipo.

  - `member` -Questo ambito evita gli avvisi rispetto a un membro.

  - `namespace` -Questo ambito evita gli avvisi rispetto allo spazio dei nomi stesso. Non elimina gli avvisi rispetto ai tipi all'interno dello spazio dei nomi.

  - `namespaceanddescendants` -(Richiede il compilatore versione 3. x o successiva e Visual Studio 2019) questo ambito evita gli avvisi in uno spazio dei nomi e tutti i relativi simboli discendenti. Il `namespaceanddescendants` valore viene ignorato dall'analisi legacy.

- **Target** : identificatore utilizzato per specificare la destinazione in cui l'avviso viene eliminato. Deve contenere un nome di elemento completo.

Quando vengono visualizzati avvisi in Visual Studio, è possibile visualizzare esempi di `SuppressMessage` aggiungendo [un'eliminazione al file di eliminazione globale](../code-quality/use-roslyn-analyzers.md#suppress-violations). L'attributo di eliminazione e le relative proprietà obbligatorie vengono visualizzati in una finestra di anteprima.

## <a name="suppressmessage-usage"></a>Utilizzo di SuppressMessage

Gli avvisi di analisi del codice vengono eliminati a livello del quale <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> viene applicato l'attributo. Ad esempio, l'attributo può essere applicato a livello di assembly, modulo, tipo, membro o parametro. Lo scopo è quello di associare strettamente le informazioni di eliminazione al codice in cui si verifica la violazione.

Il tipo di eliminazione generale include la categoria Rule e un identificatore della regola, che contiene una rappresentazione facoltativa leggibile del nome della regola. Ad esempio:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Se sono presenti motivi di prestazioni rigorosi per ridurre al minimo i metadati di eliminazione in origine, il nome della regola può essere omesso. La categoria Rule e l'ID della regola costituiscono insieme un identificatore di regola sufficientemente univoco. Ad esempio:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Per motivi di gestibilità, non è consigliabile omettere il nome della regola.

## <a name="suppress-selective-violations-within-a-method-body"></a>Non visualizzare le violazioni selettive all'interno del corpo di un metodo

Gli attributi di eliminazione possono essere applicati a un metodo, ma non possono essere incorporati all'interno di un corpo del metodo. Ciò significa che tutte le violazioni di una determinata regola vengono eliminate se si aggiunge l' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo al metodo.

In alcuni casi, potrebbe essere necessario eliminare una particolare istanza della violazione, ad esempio in modo che il codice futuro non venga esentato automaticamente dalla regola di analisi del codice. Alcune regole di analisi del codice consentono di eseguire questa operazione utilizzando la `MessageId` proprietà dell' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo. In generale, le regole legacy per le violazioni su un particolare simbolo (una variabile locale o un parametro) rispettano la `MessageId` Proprietà. [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) è un esempio di tale regola. Tuttavia, le regole legacy per le violazioni sul codice eseguibile (non simbolo) non rispettano la `MessageId` Proprietà. Inoltre, gli analizzatori .NET Compiler Platform ("Roslyn") non rispettano la `MessageId` Proprietà.

Per eliminare una particolare violazione di un simbolo di una regola, specificare il nome del simbolo per la `MessageId` proprietà dell' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo. Nell'esempio seguente viene illustrato il codice con due violazioni di [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) &mdash; uno per la `name` variabile e uno per la `age` variabile. Viene evitata solo la violazione del `age` simbolo.

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

## <a name="global-level-suppressions"></a>Eliminazione a livello globale

Lo strumento di analisi del codice gestito esamina `SuppressMessage` gli attributi applicati a livello di assembly, modulo, tipo, membro o parametro. Genera inoltre le violazioni rispetto a risorse e spazi dei nomi. Queste violazioni devono essere applicate a livello globale e sono definite a livello di ambito e di destinazione. Il messaggio seguente, ad esempio, disattiva una violazione dello spazio dei nomi:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Quando si elimina un avviso con `namespace` ambito, l'avviso viene eliminato rispetto allo spazio dei nomi stesso. Non elimina l'avviso rispetto ai tipi all'interno dello spazio dei nomi.

Qualsiasi eliminazione può essere espressa specificando un ambito esplicito. Queste evitazioni devono risiedere a livello globale. Non è possibile specificare l'eliminazione a livello di membro decorando un tipo.

Le evitazioni a livello globale sono l'unico modo per non visualizzare i messaggi che fanno riferimento a codice generato dal compilatore che non esegue il mapping a un'origine utente fornita in modo esplicito. Il codice seguente, ad esempio, evita la violazione di un costruttore emesso dal compilatore:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` contiene sempre il nome completo dell'elemento.

### <a name="global-suppression-file"></a>File di eliminazione globale

Il file di eliminazione globale mantiene le eliminazioni che sono eliminazioni a livello globale o eliminazioni che non specificano alcuna destinazione. Ad esempio, le evitazioni per le violazioni a livello di assembly vengono archiviate in questo file. Inoltre, alcune ASP.NET vengono archiviate in questo file perché le impostazioni a livello di progetto non sono disponibili per il code-behind di un form. Un file di eliminazione globale viene creato e aggiunto al progetto la prima volta che si seleziona l'opzione **nel file di eliminazione** del progetto **del comando di eliminazione nella** finestra di **Elenco errori** .

### <a name="module-suppression-scope"></a>Ambito di eliminazione del modulo

È possibile disattivare le violazioni della qualità del codice per l'intero assembly usando l'ambito del **modulo** .

L'attributo seguente nel file di progetto _GlobalSuppressions_ , ad esempio, eliminerà la violazione ConfigureAwait per un progetto ASP.NET Core:

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

## <a name="generated-code"></a>Codice generato

I compilatori di codice gestito e alcuni strumenti di terze parti generano codice per facilitare lo sviluppo rapido di codice. Il codice generato dal compilatore che viene visualizzato nei file di origine è in genere contrassegnato con l' `GeneratedCodeAttribute` attributo.

Per l'analisi del codice sorgente, è possibile disattivare i messaggi nel codice generato usando il file con [estensione EditorConfig](../code-quality/configure-fxcop-analyzers.md) nella radice del progetto o della soluzione. Usare un modello di file per trovare la corrispondenza con il codice generato. Ad esempio, per escludere gli avvisi CS1591 nei file **. designer.cs* , usare questo nel file di configurazione.

``` cmd
[*.designer.cs]
dotnet_diagnostic.CS1591.severity = none
```

Per l'analisi del codice legacy, è possibile scegliere se escludere gli avvisi e gli errori di analisi codice per il codice generato. Per informazioni sull'eliminazione di tali avvisi ed errori, vedere [procedura: non visualizzare avvisi per il codice generato](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> L'analisi del codice ignora `GeneratedCodeAttribute` quando viene applicata a un intero assembly o a un singolo parametro.

## <a name="see-also"></a>Vedere anche

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Usare gli analizzatori di codice](../code-quality/use-roslyn-analyzers.md)
