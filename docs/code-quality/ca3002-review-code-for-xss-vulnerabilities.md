---
title: 'CA3002: Esaminare il codice per le vulnerabilità XSS'
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
ms.openlocfilehash: a10f72297746a1e7bda3c69f8f7daf0efacd20bc
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018669"
---
# <a name="ca3002-review-code-for-xss-vulnerabilities"></a>CA3002: Esaminare il codice per le vulnerabilità XSS

|||
|-|-|
|TypeName|ReviewCodeForXssVulnerabilities|
|CheckId|CA3002|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Input della richiesta HTTP potenzialmente non attendibili raggiunge output HTML non elaborato.

## <a name="rule-description"></a>Descrizione della regola

Quando si lavora con input non attendibile dalle richieste web, tenere conto di attacchi di cross-site scripting (XSS). Un attacco XSS inserisce l'input non attendibile in HTML non elaborato di output, che gli consente di eseguire gli script dannosi o da utenti malintenzionati di modificare il contenuto della pagina web. Inserimento di una tecnica tipica `<script>` gli elementi con codice dannoso nell'input. Per altre informazioni, vedere [XSS dell'OWASP](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)).

Questa regola cerca di trovare input dalle richieste HTTP raggiungere l'output HTML non elaborato.

> [!NOTE]
> Questa regola non è possibile tenere traccia dei dati tra gli assembly. Ad esempio, se un unico assembly legge l'input della richiesta HTTP e quindi lo si passa a un altro assembly che genera un HTML non elaborati, questa regola non genera un avviso.

> [!NOTE]
> È previsto un limite configurabile per il livello di profondità questa regola analizza il flusso di dati durante le chiamate di metodo. Visualizzare [configurazione dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) per informazioni su come configurare il limite in `.editorconfig` file.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Invece l'output HTML non elaborato, usare un metodo o proprietà che prima codifica in HTML input.
- Codifica HTML, i dati non attendibili prima l'output HTML non elaborato.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se:
- Sai che l'input viene convalidato rispetto a un set noto sicuro di caratteri che non contengono HTML.
- Sai che i dati sono codificati in HTML in modo non rilevato da questa regola.

> [!NOTE]
> Questa regola potrebbe segnalare dei falsi positivi per alcuni metodi o proprietà di tale codifica HTML relativo input.

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

### <a name="violation"></a>Violazione

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Response.Write("<HTML>" + input + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")
        Me.Response.Write("<HTML>" + input + "</HTML>")
    End Sub
End Class
```

### <a name="solution"></a>Soluzione

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];

        // Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Response.Write("<HTML>" + Server.HtmlEncode(input) + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")

        ' Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Me.Response.Write("<HTML>" + Me.Server.HtmlEncode(input) + "</HTML>")
    End Sub
End Class
```