---
title: 'CA3002: Esaminare il codice per verificare la presenza di vulnerabilità di tipo XSS'
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
ms.openlocfilehash: 6bcf32401abdeae499097bc5187d11154e7dfc6e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237411"
---
# <a name="ca3002-review-code-for-xss-vulnerabilities"></a>CA3002: Esaminare il codice per verificare la presenza di vulnerabilità di tipo XSS

|||
|-|-|
|TypeName|ReviewCodeForXssVulnerabilities|
|CheckId|CA3002|
|Category|Microsoft.Security|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un input di richiesta HTTP potenzialmente non attendibile raggiunge l'output HTML non elaborato.

## <a name="rule-description"></a>Descrizione della regola

Quando si utilizza un input non attendibile da richieste Web, tenere presente gli attacchi XSS (cross-site scripting). Un attacco XSS inserisce input non attendibile nell'output HTML non elaborato, consentendo all'autore dell'attacco di eseguire script dannosi o modificare il contenuto nella pagina Web. Una tecnica tipica prevede `<script>` l'inserimento di elementi con codice dannoso nell'input. Per ulteriori informazioni, vedere [XSS di OWASP](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)).

Questa regola tenta di trovare l'input da richieste HTTP che raggiungono l'output HTML non elaborato.

> [!NOTE]
> Questa regola non è in grado di rilevare i dati tra gli assembly. Se, ad esempio, un assembly legge l'input della richiesta HTTP e lo passa a un altro assembly che restituisce codice HTML non elaborato, questa regola non genera un avviso.

> [!NOTE]
> Esiste un limite configurabile per il livello di profondità con cui questa regola analizzerà il flusso di dati tra le chiamate al metodo. Per informazioni su come configurare il limite in un file EditorConfig, vedere la pagina relativa alla [configurazione dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Anziché inserire codice HTML non elaborato, usare un metodo o una proprietà che prima codifica in HTML l'input.
- Codificare in HTML i dati non attendibili prima dell'output HTML non elaborato.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola se:
- Si sa che l'input viene convalidato in base a un set di caratteri Safe noto che non contiene codice HTML.
- Si sa che i dati sono codificati in HTML in modo che non vengano rilevati da questa regola.

> [!NOTE]
> Questa regola può segnalare falsi positivi per alcuni metodi o proprietà che codificano l'input in HTML.

## <a name="pseudo-code-examples"></a>Esempi di pseudo-codice

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