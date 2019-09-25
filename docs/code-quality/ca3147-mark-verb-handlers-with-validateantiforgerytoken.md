---
title: 'CA3147: Contrassegnare i gestori di verbi con ValidateAntiForgeryToken'
ms.date: 08/08/2018
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 01b290a4e4656aef079b27ce3abb2a66d7adeb75
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236988"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147: Contrassegnare i gestori di verbi con ValidateAntiForgeryToken

|||
|-|-|
|TypeName|MarkVerbHandlersWithValidateAntiForgeryToken|
|CheckId|CA3147|
|Category|Microsoft.Security|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un metodo di azione del controller MVC ASP.NET non è contrassegnato con [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/dd492108(v=vs.118))o un attributo che specifica il verbo HTTP, ad esempio [HttpGetAttribute](/previous-versions/aspnet/ee470993(v%3dvs.118)) o [AcceptVerbsAttribute](/previous-versions/aspnet/dd470553%28v%3dvs.118%29).

## <a name="rule-description"></a>Descrizione della regola

Quando si progetta un controller MVC ASP.NET, tenere presenti gli attacchi di richiesta intersito falsa. Un attacco di richiesta intersito falsificazione può inviare richieste dannose da un utente autenticato al controller MVC ASP.NET. Per ulteriori informazioni, vedere la pagina relativa alla [prevenzione di XSRF/CSRF in ASP.NET MVC e pagine Web](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages).

Questa regola controlla che i metodi di azione del controller MVC ASP.NET siano:

- Disporre di [ValidateAntiforgeryTokenAttribute](/previous-versions/aspnet/dd492108%28v%3dvs.118%29) e specificare i verbi HTTP consentiti, escluso http Get.

- Specificare HTTP GET come verbo consentito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Per le azioni del controller MVC ASP.NET che gestiscono le richieste HTTP GET e non hanno effetti collaterali potenzialmente dannosi, aggiungere un [HttpGetAttribute](/previous-versions/aspnet/ee470993%28v%3dvs.118%29) al metodo.

   Se si ha un'azione del controller MVC ASP.NET che gestisce le richieste HTTP GET e presenta effetti collaterali potenzialmente dannosi, ad esempio la modifica dei dati sensibili, l'applicazione è vulnerabile agli attacchi di richiesta intersito falsa.  È necessario riprogettare l'applicazione in modo che solo le richieste HTTP POST, PUT o DELETE eseguano operazioni riservate.

- Per le azioni del controller MVC ASP.NET che gestiscono le richieste HTTP POST, PUT o DELETE, aggiungere [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/dd492108(v=vs.118)) e attributi che specificano i verbi HTTP consentiti ([AcceptVerbsAttribute](/previous-versions/aspnet/dd470553%28v%3dvs.118%29), [HttpPostAttribute](/previous-versions/aspnet/ee264023%28v%3dvs.118%29), [ HttpPutAttribute](/previous-versions/aspnet/ee470909%28v%3dvs.118%29)o [HttpDeleteAttribute](/previous-versions/aspnet/ee470917%28v%3dvs.118%29)). Inoltre, è necessario chiamare il metodo [HtmlHelper. AntiForgeryToken ()](/previous-versions/aspnet/dd504812%28v%3dvs.118%29) dalla visualizzazione MVC o dalla pagina Web Razor. Per un esempio, vedere [analisi dei metodi di modifica e della visualizzazione di modifica](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view).

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola se:

- L'azione del controller MVC ASP.NET non ha effetti collaterali dannosi.

- L'applicazione convalida il token antifalsificazione in modo diverso.

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
