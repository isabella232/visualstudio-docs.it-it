---
title: 'CA3004: Esaminare il codice per verificare la presenza di vulnerabilità di tipo diffusione di informazioni'
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
ms.openlocfilehash: 4965c9df3c2256511b8e44de8d388a9155d0d8f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237383"
---
# <a name="ca3004-review-code-for-information-disclosure-vulnerabilities"></a>CA3004: Esaminare il codice per verificare la presenza di vulnerabilità di tipo diffusione di informazioni

|||
|-|-|
|TypeName|ReviewCodeForInformationDisclosureVulnerabilities|
|CheckId|CA3004|
|Category|Microsoft.Security|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Il messaggio, la traccia dello stack o la rappresentazione di stringa di un'eccezione raggiunge l'output Web.

## <a name="rule-description"></a>Descrizione della regola

La divulgazione delle informazioni sulle eccezioni consente agli utenti malintenzionati di comprendere le caratteristiche interne dell'applicazione, che possono aiutare gli utenti malintenzionati a trovare altre vulnerabilità da sfruttare.

Questa regola tenta di trovare un messaggio di eccezione, una traccia dello stack o una rappresentazione di stringa che viene restituita a una risposta HTTP.

> [!NOTE]
> Questa regola non è in grado di rilevare i dati tra gli assembly. Se, ad esempio, un assembly rileva un'eccezione e la passa a un altro assembly che restituisce l'eccezione, questa regola non genera un avviso.

> [!NOTE]
> Esiste un limite configurabile per il livello di profondità con cui questa regola analizzerà il flusso di dati tra le chiamate al metodo. Per informazioni su come configurare il limite in un file EditorConfig, vedere la pagina relativa alla [configurazione dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Non restituire informazioni sulle eccezioni alle risposte HTTP. Fornire invece un messaggio di errore generico. Per ulteriori informazioni, vedere [la pagina relativa alla gestione degli errori di OWASP](https://www.owasp.org/index.php/Error_Handling) .

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Se si è certi che l'output Web si trovi all'interno del limite di attendibilità dell'applicazione e non viene mai esposto all'esterno, è possibile ignorare questo avviso. Si tratta di una situazione rara. Si prenda in considerazione che i flussi di dati e i limiti di attendibilità dell'applicazione possono cambiare nel tempo.

## <a name="pseudo-code-examples"></a>Esempi di pseudo-codice

### <a name="violation"></a>Violazione

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write(e.ToString());
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write(e.ToString())
        End Try
    End Sub
End Class
```

### <a name="solution"></a>Soluzione

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write("An error occurred. Please try again later.");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write("An error occurred. Please try again later.")
        End Try
    End Sub
End Class
```