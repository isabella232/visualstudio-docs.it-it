---
title: 'CA3007: Esaminare il codice per le vulnerabilità di reindirizzamento aperti'
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
ms.openlocfilehash: dbafb6c05a3dba72d1614d6a955e20030a50c6ea
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018518"
---
# <a name="ca3007-review-code-for-open-redirect-vulnerabilities"></a>CA3007: Esaminare il codice per le vulnerabilità di reindirizzamento aperti

|||
|-|-|
|TypeName|ReviewCodeForOpenRedirectVulnerabilities|
|CheckId|CA3007|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Input della richiesta HTTP potenzialmente non attendibili raggiunge un reindirizzamento di risposta HTTP.

## <a name="rule-description"></a>Descrizione della regola

Quando si lavora con input non attendibile, tenere presenti le vulnerabilità di reindirizzamento aperti. Un utente malintenzionato può sfruttare una vulnerabilità di reindirizzamento aperti per usare il sito Web per dare l'impressione di un URL valido, ma un visitatore ignaro un phishing o altre pagine Web dannoso di reindirizzamento.

Questa regola cerca di trovare input dalle richieste HTTP raggiungere un URL di reindirizzamento HTTP.

> [!NOTE]
> Questa regola non è possibile tenere traccia dei dati tra gli assembly. Ad esempio, se un unico assembly legge l'input della richiesta HTTP e quindi lo si passa a un altro assembly che risponde con un reindirizzamento HTTP, questa regola non genera un avviso.

> [!NOTE]
> È previsto un limite configurabile per il livello di profondità questa regola analizza il flusso di dati durante le chiamate di metodo. Visualizzare [configurazione dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) per informazioni su come configurare il limite in `.editorconfig` file.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Alcuni approcci per risolvere le vulnerabilità di reindirizzamento aperti includono:

- Non consentire agli utenti di avviare i reindirizzamenti.
- Non consentire agli utenti di specificare qualsiasi parte dell'URL in uno scenario di reindirizzamento.
- Limitare i reindirizzamenti a una predefinita "Consenti l'elenco" degli URL.
- Convalidare gli URL di reindirizzamento.
- Se applicabile, prendere in considerazione l'utilizzo di una pagina di dichiarazione di non responsabilità quando gli utenti in corso il reindirizzamento dal sito.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Se si sa di che aver convalidato l'input per essere limitata agli URL previsto, è possibile eliminare l'avviso.

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

### <a name="violation"></a>Violazione

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["url"];
        this.Response.Redirect(input);
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("url")
        Me.Response.Redirect(input)
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
        if (String.IsNullOrWhiteSpace(input))
        {
            this.Response.Redirect("https://example.org/login.html");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("in")
        If String.IsNullOrWhiteSpace(input) Then
            Me.Response.Redirect("https://example.org/login.html")
        End If
    End Sub
End Class
```
