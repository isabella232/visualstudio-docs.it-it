---
title: 'CA3010: Esaminare il codice per verificare la presenza di vulnerabilità di tipo XAML injection'
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
ms.openlocfilehash: ea53f5e0cddf1dc6c6caf4c7fcfb79af52ce354e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806524"
---
# <a name="ca3010-review-code-for-xaml-injection-vulnerabilities"></a>CA3010: Esaminare il codice per verificare la presenza di vulnerabilità di tipo XAML injection

|||
|-|-|
|TypeName|ReviewCodeForXamlInjectionVulnerabilities|
|CheckId|CA3010|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Richiesta HTTP potenzialmente non attendibile di input raggiunge un <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> metodo Load.

## <a name="rule-description"></a>Descrizione della regola

Quando si lavora con input non attendibile, tenere conto di attacchi intrusivi nel codice XAML. XAML è un linguaggio di markup che rappresenta direttamente la creazione di istanze di oggetti e la relativa esecuzione. Ciò significa che gli elementi creati in XAML possono interagire con le risorse di sistema (ad esempio, rete access e file di sistema i/o). Se un utente malintenzionato può controllare l'input per un <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> caricamento chiamata al metodo, quindi l'autore dell'attacco può eseguire codice.

Questa regola tenta di trovare input dalle richieste HTTP che raggiunge un <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> metodo Load.

> [!NOTE]
> Questa regola non è possibile tenere traccia dei dati tra gli assembly. Ad esempio, se un unico assembly legge l'input della richiesta HTTP e quindi lo si passa a un altro assembly che esegue il caricamento di XAML, questa regola non genera un avviso.

> [!NOTE]
> È previsto un limite configurabile per il livello di profondità questa regola analizza il flusso di dati durante le chiamate di metodo. Visualizzare [configurazione dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) per informazioni su come configurare il limite in `.editorconfig` file.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Non vengono caricati XAML non attendibili.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non eliminare gli avvisi da questa regola.

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

### <a name="violation"></a>Violazione

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] bytes = Convert.FromBase64String(input);
        MemoryStream ms = new MemoryStream(bytes);
        System.Windows.Markup.XamlReader.Load(ms);
    }
}
```

```vb
Imports System
Imports System.IO

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim bytes As Byte() = Convert.FromBase64String(input)
        Dim ms As MemoryStream = New MemoryStream(bytes)
        System.Windows.Markup.XamlReader.Load(ms)
    End Sub
End Class
```
