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
ms.openlocfilehash: 114b44ec566554c81f5caf3b8ac474f9c5a75c07
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806453"
---
# <a name="ca3012-review-code-for-regex-injection-vulnerabilities"></a>CA3012: Esaminare il codice per verificare la presenza di vulnerabilità di tipo regex injection

|||
|-|-|
|TypeName|ReviewCodeForRegexInjectionVulnerabilities|
|CheckId|CA3012|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Input della richiesta HTTP potenzialmente non attendibili raggiunge un'espressione regolare.

## <a name="rule-description"></a>Descrizione della regola

Quando si lavora con input non attendibile, tenere conto di attacchi intrusivi nel codice di espressione regolare. Un utente malintenzionato può utilizzare l'inserimento di espressione regolare da utenti malintenzionati di modificare un'espressione regolare, per rendere l'espressione regolare corrisponde a risultati imprevisti o eseguire l'espressione regolare di utilizzo eccessivo della CPU causando un attacco Denial of Service.

Questa regola cerca di trovare input dalle richieste HTTP raggiunge un'espressione regolare.

> [!NOTE]
> Questa regola non è possibile tenere traccia dei dati tra gli assembly. Ad esempio, se un unico assembly legge l'input della richiesta HTTP e quindi lo si passa a un altro assembly che crea un'espressione regolare, questa regola non genera un avviso.

> [!NOTE]
> È previsto un limite configurabile per il livello di profondità questa regola analizza il flusso di dati durante le chiamate di metodo. Visualizzare [configurazione dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) per informazioni su come configurare il limite in `.editorconfig` file.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Di seguito sono riportate alcune soluzioni di prevenzione contro attacchi di injection di espressione regolare:

- Usare sempre un [corrispondere timeout](/dotnet/standard/base-types/best-practices#use-time-out-values) quando si usano le espressioni regolari.
- Evitare di usare espressioni regolari in base all'input utente.
- Caratteri speciali di escape dall'input dell'utente chiamando <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=fullName> o un altro metodo.
- Consenti caratteri solo non speciali dall'input dell'utente.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Se si conosce si usa un' [corrispondere timeout](/dotnet/standard/base-types/best-practices#use-time-out-values) e l'input dell'utente è libero di caratteri speciali, che è possibile eliminare l'avviso.

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

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
