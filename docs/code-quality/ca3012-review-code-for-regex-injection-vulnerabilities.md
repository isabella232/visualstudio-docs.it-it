---
title: 'CA3012: Esaminare il codice per verificare la presenza di vulnerabilità di tipo regex injection'
ms.date: 04/03/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 42808b3961b18a23f594800f9d0782c908c9b1ba
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237184"
---
# <a name="ca3012-review-code-for-regex-injection-vulnerabilities"></a>CA3012: Esaminare il codice per verificare la presenza di vulnerabilità di tipo regex injection

|||
|-|-|
|TypeName|ReviewCodeForRegexInjectionVulnerabilities|
|CheckId|CA3012|
|Category|Microsoft.Security|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un input di richiesta HTTP potenzialmente non attendibile raggiunge un'espressione regolare.

## <a name="rule-description"></a>Descrizione della regola

Quando si lavora con un input non attendibile, tenere presente gli attacchi di attacchi Regex. Un utente malintenzionato può utilizzare l'inserimento Regex per modificare in modo dannoso un'espressione regolare, per fare in modo che l'espressione regolare corrisponda a risultati imprevisti oppure per fare in modo che la regex utilizzi una CPU eccessiva con conseguente attacco Denial of Service.

Questa regola tenta di trovare l'input da richieste HTTP che raggiungono un'espressione regolare.

> [!NOTE]
> Questa regola non è in grado di rilevare i dati tra gli assembly. Se, ad esempio, un assembly legge l'input della richiesta HTTP e lo passa a un altro assembly che crea un'espressione regolare, questa regola non genera un avviso.

> [!NOTE]
> Esiste un limite configurabile per il livello di profondità con cui questa regola analizzerà il flusso di dati tra le chiamate al metodo. Per informazioni su come configurare il limite in un file EditorConfig, vedere la pagina relativa alla [configurazione dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Alcune attenuazioni rispetto ai Injection Regex includono:

- Usare sempre un [timeout di corrispondenza](/dotnet/standard/base-types/best-practices#use-time-out-values) quando si usano le espressioni regolari.
- Evitare di usare espressioni regolari basate sull'input dell'utente.
- Consente di evitare l'escape di caratteri speciali <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=fullName> dall'input dell'utente chiamando o un altro metodo.
- Consente solo caratteri non speciali dall'input dell'utente.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Se si è certi che si sta usando un [timeout di corrispondenza](/dotnet/standard/base-types/best-practices#use-time-out-values) e l'input dell'utente è privo di caratteri speciali, è possibile evitare di visualizzare questo avviso.

## <a name="pseudo-code-examples"></a>Esempi di pseudo-codice

### <a name="violation"></a>Violazione

```csharp
using System;
using System.Text.RegularExpressions;

public partial class WebForm : System.Web.UI.Page
{
    public string SearchableText { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string findTerm = Request.Form["findTerm"];
        Match m = Regex.Match(SearchableText, "^term=" + findTerm);
    }
}
```

```vb
Imports System
Imports System.Text.RegularExpressions

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Public Property SearchableText As String

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim findTerm As String = Request.Form("findTerm")
        Dim m As Match = Regex.Match(SearchableText, "^term=" + findTerm)
    End Sub
End Class
```
