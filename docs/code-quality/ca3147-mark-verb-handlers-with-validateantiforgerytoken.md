---
title: 'CA3147: Contrassegnare i gestori di verbo con ValidateAntiForgeryToken'
ms.date: 08/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 4b4369cfd310be9322d17b8bdbfe79880f2aa579
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008703"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147: Contrassegnare i gestori di verbo con ValidateAntiForgeryToken

|||
|-|-|
|TypeName|MarkVerbHandlersWithValidateAntiForgeryToken|
|CheckId|CA3147|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un metodo di azione del controller ASP.NET MVC non è contrassegnato con <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute?displayProperty=fullName>, o un attributo che specifica il verbo HTTP, ad esempio <xref:Microsoft.AspNetCore.Mvc.HttpGetAttribute?displayProperty=fullName> o <xref:Microsoft.AspNetCore.Mvc.AcceptVerbsAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola

Quando si progetta un controller MVC ASP.NET, tenere conto di attacchi di richiesta intersito falsa. Un attacco di tipo richiesta intersito falsa può inviare richieste dannose da un utente autenticato al controller ASP.NET MVC. Per altre informazioni, vedere [prevenzione di XSRF/CSRF in ASP.NET MVC e pagine web](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages).

Questa regola consente di controllare tale controller ASP.NET MVC i metodi di azione entrambi:

- Dispone il <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute> e specificare i verbi HTTP consentiti, senza includere HTTP GET.

- Specificare HTTP GET come un verbo consentito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Per azioni del controller ASP.NET MVC che gestiscono le richieste HTTP GET e non hanno conseguenze potenzialmente dannose, aggiungere un <xref:Microsoft.AspNetCore.Mvc.HttpGetAttribute> al metodo.

   Se si dispone di MVC ASP.NET le richieste di azione del controller che gestisce HTTP GET e ha effetti collaterali potenzialmente dannosi, ad esempio la modifica dei dati sensibili, l'applicazione è vulnerabile agli attacchi di richiesta intersito falsa intersito.  È necessario riprogettare l'applicazione in modo che solo le richieste HTTP POST, PUT o DELETE effettuare operazioni sensibili.

- Per azioni del controller ASP.NET MVC che gestiscono HTTP POST, PUT o DELETE richiede, aggiungere <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute> e gli attributi che specificano i verbi HTTP consentiti (<xref:Microsoft.AspNetCore.Mvc.AcceptVerbsAttribute>, <xref:Microsoft.AspNetCore.Mvc.HttpPostAttribute>, <xref:Microsoft.AspNetCore.Mvc.HttpPutAttribute>, o <xref:Microsoft.AspNetCore.Mvc.HttpDeleteAttribute>). Inoltre, è necessario chiamare <xref:Microsoft.AspNetCore.Mvc.ViewFeatures.HtmlHelper.AntiForgeryToken%2A?displayProperty=nameWithType> dalla visualizzazione MVC o pagina web di Razor. Per un esempio, vedere [esaminando i metodi di modifica e visualizzazione di modifica](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view).

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se:

- L'azione del controller ASP.NET MVC ha effetti collaterali dannosi.

- L'applicazione convalida il token anti falsificazione in modo diverso.

## <a name="validateantiforgerytoken-attribute-example"></a>Esempio di attributo ValidateAntiForgeryToken

### <a name="violation"></a>Violazione

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            // You don't want an attacker to specify to who and how much money to transfer.

            return null;
        }
    }
}
```

### <a name="solution"></a>Soluzione

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            return null;
        }
    }
}
```

## <a name="httpget-attribute-example"></a>Esempio di attributo HttpGet

### <a name="violation"></a>Violazione

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult Help(int topicId)
        {
            // This Help method is an example of a read-only operation with no harmful side effects.
            return null;
        }
    }
}
```

### <a name="solution"></a>Soluzione

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpGet]
        public ActionResult Help(int topicId)
        {
            return null;
        }
    }
}
```
