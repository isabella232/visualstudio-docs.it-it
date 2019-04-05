---
title: 'CA3004: Esaminare il codice per le vulnerabilità la divulgazione di informazioni'
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
ms.openlocfilehash: 82f763d9a6b1ec27975aa80054456a6bbbaeaa2b
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018524"
---
# <a name="ca3004-review-code-for-information-disclosure-vulnerabilities"></a>CA3004: Esaminare il codice per le vulnerabilità la divulgazione di informazioni

|||
|-|-|
|TypeName|ReviewCodeForInformationDisclosureVulnerabilities|
|CheckId|CA3004|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Messaggio di un'eccezione, analisi dello stack o rappresentazione di stringa raggiunge l'output web.

## <a name="rule-description"></a>Descrizione della regola

Diffusione di informazioni sulle eccezioni offre informazioni dettagliate degli elementi interni dell'applicazione, che consentono agli utenti malintenzionati individuare altre vulnerabilità di sfruttare gli utenti malintenzionati.

Questa regola tenta di individuare un messaggio di eccezione, analisi dello stack o rappresentazione di stringa in fase di output in una risposta HTTP.

> [!NOTE]
> Questa regola non è possibile tenere traccia dei dati tra gli assembly. Ad esempio, se un unico assembly rileva un'eccezione e quindi lo si passa a un altro assembly che genera l'eccezione, questa regola non genera un avviso.

> [!NOTE]
> È previsto un limite configurabile per il livello di profondità questa regola analizza il flusso di dati durante le chiamate di metodo. Visualizzare [configurazione dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) per informazioni su come configurare il limite in `.editorconfig` file.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Non restituire le informazioni sull'eccezione per le risposte HTTP. In alternativa, fornire un messaggio di errore generico. Visualizzare [pagina di gestione degli errori dell'OWASP](https://www.owasp.org/index.php/Error_Handling) per altro materiale sussidiario.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Se si conosce l'output web entro il limite di attendibilità dell'applicazione e mai esposta esternamente, è possibile eliminare l'avviso. Si tratta di una rara. Prendere in considerazione che il limite di attendibilità dell'applicazione e i flussi di dati possono cambiare nel tempo.

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

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