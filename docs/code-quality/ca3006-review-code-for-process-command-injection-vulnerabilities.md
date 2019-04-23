---
title: 'CA3006: Esaminare il codice per verificare la presenza di vulnerabilità di tipo process command injection'
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
ms.openlocfilehash: da161e611ca1d802c8da16370907029233bfd785
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60037985"
---
# <a name="ca3006-review-code-for-process-command-injection-vulnerabilities"></a>CA3006: Esaminare il codice per verificare la presenza di vulnerabilità di tipo process command injection

|||
|-|-|
|TypeName|ReviewCodeForProcessCommandInjectionVulnerabilities|
|CheckId|CA3006|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Input della richiesta HTTP potenzialmente non attendibili raggiunge un comando di elaborazione.

## <a name="rule-description"></a>Descrizione della regola

Quando si lavora con input non attendibile, tenere conto di attacchi intrusivi nel codice di comando. Un attacco injection comando può eseguire comandi dannosi nel sistema operativo sottostante, compromettere la sicurezza e l'integrità del server.

Questa regola cerca di trovare input dalle richieste HTTP raggiungere un comando di elaborazione.

> [!NOTE]
> Questa regola non è possibile tenere traccia dei dati tra gli assembly. Ad esempio, se un unico assembly legge l'input della richiesta HTTP e quindi lo si passa a un altro assembly che avvia un processo, questa regola non genera un avviso.

> [!NOTE]
> È previsto un limite configurabile per il livello di profondità questa regola analizza il flusso di dati durante le chiamate di metodo. Visualizzare [configurazione dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) per informazioni su come configurare il limite in `.editorconfig` file.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Evitare se possibile, vengono avviati i processi in base all'input utente.
- Convalidare l'input in base a un set di caratteri e la lunghezza attendibili noto.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Se si conosce l'input è stato convalidato o caratteri di escape per essere sicuri, è possibile eliminare questo avviso.

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

### <a name="violation"></a>Violazione

```csharp
using System;
using System.Diagnostics;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Process p = Process.Start(input);
    }
}
```

```vb
Imports System
Imports System.Diagnostics

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs as EventArgs)
        Dim input As String = Me.Request.Form("in")
        Dim p As Process = Process.Start(input)
    End Sub
End Class
```
