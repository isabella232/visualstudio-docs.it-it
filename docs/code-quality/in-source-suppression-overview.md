---
title: Non visualizzare gli avvisi dell'analisi codice
ms.date: 12/01/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 7fd2d8323a249771357ca0b32dc3106f11d8aa1b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036186"
---
# <a name="suppress-code-analysis-warnings"></a>Non visualizzare gli avvisi dell'analisi codice

Spesso è utile indicare che un messaggio di avviso non è applicabile. Ciò indica ai membri del team che è stato esaminato il codice e che l'avviso può essere eliminato. Eliminazione (ISS) viene utilizzato in origine la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo per eliminare un avviso. L'attributo può essere posizionato vicino al segmento di codice che ha generato l'avviso. È possibile aggiungere il <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> dell'attributo del file di origine digitando, oppure è possibile usare il menu di scelta rapida in un avviso nel **elenco errori** per aggiungerlo automaticamente.

Il <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo è un attributo di tipo condizionale, che è incluso nei metadati dell'assembly del codice gestito, solo se il simbolo di compilazione CODE_ANALYSIS è definito in fase di compilazione.

In C + + c++ /CLI CLI, utilizzare le macro autorità di certificazione\_SUPPRESS\_messaggio o autorità di certificazione\_GLOBAL\_SUPPRESS_MESSAGE nel file di intestazione per aggiungere l'attributo.

> [!NOTE]
> Non utilizzare le eliminazioni nell'origine nelle build di rilascio, per evitare che i metadati di eliminazione nell'origine di spedizione accidentalmente. Inoltre, a causa del costo di elaborazione di eliminazione nell'origine, è possono peggiorare le prestazioni dell'applicazione.

> [!NOTE]
> Se si esegue la migrazione di un progetto di Visual Studio 2017, possono incontrare improvvisamente con un numero elevato di avvisi dell'analisi codice. Questi avvisi provengono [analizzatori di Roslyn](roslyn-analyzers-overview.md). Se non si è pronti per risolvere gli avvisi, è possibile eliminare tutti gli elementi scegliendo **Analyze** > **Esegui analisi del codice ed Elimina problemi attivi**.
>
> ![Esegui analisi del codice ed eliminare i problemi in Visual Studio](media/suppress-active-issues.png)

## <a name="suppressmessage-attribute"></a>SuppressMessage (attributo)

Quando si sceglie **Suppress** dal menu di scelta rapida di un avviso di analisi del codice nelle **elenco errori**, un <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo viene aggiunto nel codice o di eliminazione globale del progetto file.

Il <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo presenta il formato seguente:

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

- **Categoria** -la categoria in cui è definita la regola. Per altre informazioni sulle categorie di regole di analisi del codice, vedere [gli avvisi del codice gestito](../code-quality/code-analysis-for-managed-code-warnings.md).

- **CheckId** -l'identificatore della regola. Il supporto include sia un nome breve e a lungo per l'identificatore della regola. Il nome breve è CAXXXX; il nome lungo è CAXXXX:FriendlyTypeName.

- **Giustificazione** -il testo che consente di documentare il motivo dell'eliminazione del messaggio.

- **MessageId** -identificatore univoco di un problema per ogni messaggio.

- **Ambito** -la destinazione in cui è stato eliminato l'avviso. Se la destinazione non è specificato, cui è impostata la destinazione dell'attributo. È supportato [ambiti](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) includono quanto segue:

   - `module`

   - `resource`

   - `type`

   - `member`

   - `namespace` -L'ambito deve eliminare gli avvisi per lo spazio dei nomi stesso. Non elimina gli avvisi per i tipi nello spazio dei nomi.

   - `namespaceanddescendants` -(Novità di Visual Studio 2019) questo ambito Elimina gli avvisi in uno spazio dei nomi e tutti i simboli relativi discendenti. Il `namespaceanddescendants` valore è valido solo per gli analizzatori di Roslyn e viene ignorato dall'analisi statica binario, in base al FxCop.

- **Destinazione** : un identificatore che consente di specificare la destinazione in cui è stato eliminato l'avviso. Deve contenere un nome di elemento completo.

## <a name="suppressmessage-usage"></a>Utilizzo SuppressMessage

Avvisi dell'analisi codice vengono soppressi a livello di a cui il <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> viene applicato l'attributo. Ad esempio, l'attributo può essere applicato all'assembly, modulo, tipo, membro o a livello di parametro. Lo scopo di questo è uno stretto accoppiamento le informazioni di eliminazione per il codice in cui si verifica la violazione.

Il formato generale dell'eliminazione include la categoria della regola e un identificatore di regola, che contiene una rappresentazione leggibile facoltativa del nome della regola. Ad esempio:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Se esistono motivi di prestazioni strict per ridurre al minimo i metadati di eliminazione nell'origine, è possibile omettere il nome della regola. La categoria della regola e il relativo ID regola insieme costituiscono un identificatore di regola sufficientemente univoco. Ad esempio:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Per ragioni di manutenibilità, omettendo il nome della regola non è consigliabile.

## <a name="suppress-selective-violations-within-a-method-body"></a>Non visualizzare le violazioni selettive all'interno di un corpo del metodo

Eliminazione degli attributi possono essere applicati a un metodo, ma non possono essere incorporati all'interno di un corpo del metodo. Ciò significa che tutte le violazioni di una particolare regola vengono soppressi se si aggiunge il <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> al metodo.

In alcuni casi, si potrebbe voler eliminare una particolare istanza della violazione, ad esempio, in modo che codice futuro non è automaticamente esente dalla regola di analisi codice. Alcune regole di analisi del codice consentono di eseguire questa operazione usando il `MessageId` proprietà del <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo. In generale, le regole di legacy per le violazioni in proposito un simbolo specifico (una variabile locale o un parametro) di `MessageId` proprietà. [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) è riportato un esempio di tale regola. Tuttavia, non rispettano le regole precedenti per le violazioni sul codice eseguibile (non-symbol) il `MessageId` proprietà. Inoltre, gli analizzatori .NET Compiler Platform ("Roslyn") non rispettano la `MessageId` proprietà.

Per eliminare una violazione di un simbolo specifico di una regola, specificare il nome del simbolo per il `MessageId` proprietà del <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attributo. L'esempio seguente mostra il codice con due violazioni della [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;uno per il `name` variabile e uno per il `age` variabile. Solo la violazione per il `age` simbolo viene eliminato.

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

## <a name="generated-code"></a>Codice generato

I compilatori di codice gestito e alcuni strumenti di terze parti generano codice per facilitare lo sviluppo rapido di codice. Il codice generato dal compilatore che viene visualizzato nel file di origine in genere è contrassegnato con il `GeneratedCodeAttribute` attributo.

È possibile scegliere se eliminare gli avvisi dell'analisi codice e gli errori per il codice generato. Per informazioni su come eliminare questi avvisi ed errori, vedere [come: Non visualizzare avvisi per il codice generato](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Analisi del codice ignora `GeneratedCodeAttribute` quando viene applicata a un intero assembly o un singolo parametro.

## <a name="global-level-suppressions"></a>Eliminazioni a livello globale

Lo strumento di analisi codice gestito viene esaminato `SuppressMessage` gli attributi applicati a livello di assembly, modulo, tipo, membro o parametro. Viene inoltre generato violazioni contro le risorse e gli spazi dei nomi. Tali violazioni deve essere applicati a livello globale e sono con ambiti e di destinazione. Ad esempio, il messaggio seguente elimina una violazione dello spazio dei nomi:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Quando si elimina un avviso con `namespace` ambito, viene eliminato l'avviso per lo spazio dei nomi stesso. Non elimina l'avviso in base a tipi nello spazio dei nomi.

Qualsiasi eliminazione può essere espresse specificando un ambito esplicito. È necessario in tempo reale di queste eliminazioni a livello globale. È possibile specificare l'eliminazione a livello di membro tramite la decorazione di un tipo.

Eliminazioni a livello globale sono l'unico modo per eliminare i messaggi che fanno riferimento al codice generato dal compilatore che non esegue il mapping a un'origine utente specificato in modo esplicito. Ad esempio, il codice seguente elimina una violazione in base a un costruttore emesso dal compilatore:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` contiene sempre il nome dell'elemento completo.

## <a name="global-suppression-file"></a>File eliminazione globale

Il file di eliminazione globale conserva le eliminazioni a livello globale o le eliminazioni che non si specificano una destinazione. Ad esempio, in questo file vengono archiviate le eliminazioni a livello di assembly violazioni. Inoltre, alcune eliminazioni ASP.NET vengono archiviate in questo file perché le impostazioni a livello di progetto non sono disponibili per un modello code-behind. Viene creato e aggiunto al progetto la prima volta che si seleziona un file di eliminazione globale i **nel File di eliminazione di progetto** opzione del **Suppress** comando il **elenco errori**finestra.

## <a name="see-also"></a>Vedere anche

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Usare gli analizzatori di Roslyn](../code-quality/use-roslyn-analyzers.md)