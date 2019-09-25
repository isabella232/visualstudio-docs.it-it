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
ms.openlocfilehash: 986607d7f42f49c99396bbb021c48bad549930c9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237288"
---
# <a name="ca3006-review-code-for-process-command-injection-vulnerabilities"></a>CA3006: Esaminare il codice per verificare la presenza di vulnerabilità di tipo process command injection

|||
|-|-|
|TypeName|ReviewCodeForProcessCommandInjectionVulnerabilities|
|CheckId|CA3006|
|Category|Microsoft.Security|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un input di richiesta HTTP potenzialmente non attendibile raggiunge un comando di elaborazione.

## <a name="rule-description"></a>Descrizione della regola

Quando si lavora con un input non attendibile, tenere presente gli attacchi di inserimento dei comandi. Un attacco injection comando può eseguire comandi dannosi sul sistema operativo sottostante, compromettendo la sicurezza e l'integrità del server.

Questa regola tenta di trovare l'input da richieste HTTP che raggiungono un comando di elaborazione.

> [!NOTE]
> Questa regola non è in grado di rilevare i dati tra gli assembly. Se, ad esempio, un assembly legge l'input della richiesta HTTP e lo passa a un altro assembly che avvia un processo, questa regola non genera un avviso.

> [!NOTE]
> Esiste un limite configurabile per il livello di profondità con cui questa regola analizzerà il flusso di dati tra le chiamate al metodo. Per informazioni su come configurare il limite in un file EditorConfig, vedere la pagina relativa alla [configurazione dell'analizzatore](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Se possibile, evitare di avviare i processi in base all'input dell'utente.
- Convalidare l'input rispetto a un set di caratteri sicuro e di lunghezza noti.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Se si sa che l'input è stato convalidato o è stato preceduto da un carattere di escape sicuro, è possibile che l'avviso non venga eliminato.

## <a name="pseudo-code-examples"></a>Esempi di pseudo-codice

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
