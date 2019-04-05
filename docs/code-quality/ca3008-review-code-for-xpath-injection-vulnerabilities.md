---
title: 'CA3008: Esaminare il codice per vulnerabilità di tipo injection XPath'
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
ms.openlocfilehash: e66b75160df0e8ecf9d33601ee383ec71cd62c4d
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018513"
---
# <a name="ca3008-review-code-for-xpath-injection-vulnerabilities"></a>CA3008: Esaminare il codice per vulnerabilità di tipo injection XPath

|||
|-|-|
|TypeName|ReviewCodeForXPathInjectionVulnerabilities|
|CheckId|CA3008|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Input della richiesta HTTP potenzialmente non attendibili raggiunge una query XPath.

## <a name="rule-description"></a>Descrizione della regola

Quando si lavora con input non attendibile, tenere conto di attacchi intrusivi nel codice di XPath. Costruzione delle query XPath utilizzando l'input non attendibile potrebbe consentire un attacco da utenti malintenzionati di modificare la query per restituire un risultato non intenzionale e possibilmente divulgare il contenuto del XML sottoposti a query. 

Questa regola cerca di trovare input dalle richieste HTTP raggiunge un'espressione XPath.

> [!NOTE]
> Questa regola non è possibile tenere traccia dei dati tra gli assembly. Ad esempio, se un unico assembly legge l'input della richiesta HTTP e quindi lo si passa a un altro assembly che esegue una query XPath, questa regola non genera un avviso.

> [!NOTE]
> È previsto un limite configurabile per il livello di profondità questa regola analizza il flusso di dati durante le chiamate di metodo. Visualizzare [configurazione dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) per informazioni su come configurare il limite in `.editorconfig` file.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Alcuni approcci per la correzione di vulnerabilità di tipo injection XPath includono:

- Non costruire le query XPath dall'input dell'utente.
- Verificare che l'input contiene solo un set di caratteri attendibili.
- Eseguire l'escape di virgolette.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Se si sa di che aver convalidato l'input per essere sicuri, è possibile eliminare l'avviso.

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

### <a name="violation"></a>Violazione

```csharp
using System;
using System.Xml.XPath;

public partial class WebForm : System.Web.UI.Page
{
    public XPathNavigator AuthorizedOperations { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string operation = Request.Form["operation"];

        // If an attacker uses this for input:
        //     ' or 'a' = 'a
        // Then the XPath query will be:
        //     authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        // and it will return any authorizedOperation node.
        XPathNavigator node = AuthorizedOperations.SelectSingleNode(
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']");
    }
}
```

```vb
Imports System
Imports System.Xml.XPath

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Public Property AuthorizedOperations As XPathNavigator

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim operation As String = Me.Request.Form("operation")
        
        ' If an attacker uses this for input:
        '     ' or 'a' = 'a
        ' Then the XPath query will be:
        '      authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        ' and it will return any authorizedOperation node.
        Dim node As XPathNavigator = AuthorizedOperations.SelectSingleNode( _
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']")
    End Sub
End Class
```
