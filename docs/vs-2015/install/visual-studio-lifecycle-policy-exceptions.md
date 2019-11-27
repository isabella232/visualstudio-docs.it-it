---
title: Eccezioni dei criteri del ciclo di vita di Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
ms.assetid: c238489d-6181-42c6-aa60-f75d0889dc68
caps.latest.revision: 3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 6db11d583818f1ea63c490cd8f588cb005b50a8d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295925"
---
# <a name="visual-studio-lifecycle-policy-exceptions"></a>Eccezioni dei criteri relativi al ciclo di vita di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio include una raccolta di compilatori, linguaggi, runtime, ambienti e altre risorse che consentono lo sviluppo per molte piattaforme Microsoft. Per una maggior praticità dei clienti di Visual Studio, è possibile installare SDK e altri componenti Microsoft che fanno riferimento e supportano tali piattaforme Microsoft. Questi componenti possono essere concessi in licenza e supportati in base a termini e condizioni specifici.  
  
## <a name="external-components-that-follow-a-lifecycle-policy-other-than-the-visual-studio-policy"></a>Componenti esterni che seguono criteri relativi al ciclo di vita diversi da quelli di Visual Studio  
 La tabella seguente elenca i componenti delle piattaforme Microsoft che possono essere inclusi in Visual Studio (a seconda dell'edizione specifica del software Visual Studio) e che sono soggetti a tempistiche e criteri di supporto specifici.  
  
|FAMIGLIA DI PRODOTTI|EXTERNAL NAME|  
|--------------------|-------------------|  
|[.NET 3.5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%203.5&Filter=FilterNO)|.NET 3.5 SDK<br /><br /> Windows Identity Foundation|  
|[.NET 4.5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%204.5&Filter=FilterNO)|.NET 4.5 SDK|  
|[.NET 4.5.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=.NET%20Framework%204.5.1&Filter=FilterNO)|.NET 4.5.1 MT Pack (Classic)<br /><br /> .NET 4.5.1 Multi-targeting Pack (Store)<br /><br /> .NET 4.5.1 OOB MSU<br /><br /> .NET 4.5.1 Redist<br /><br /> .NET 4.5.1 Redist Language Packs<br /><br /> .NET 4.5.1 SDK|  
|[ASP.NET Web Stack](https://go.microsoft.com/fwlink/?LinkId=328918)|ASP.NET MVC 4<br /><br /> ASP.NET MVC 5<br /><br /> ASP.NET Web API<br /><br /> ASP.NET Web API 2<br /><br /> Pagine Web ASP.NET 2<br /><br /> Pagine Web ASP.NET 3|  
|[Entity Framework 6](https://go.microsoft.com/fwlink/?LinkId=328950)|Entity Framework 6|  
|[Exchange 2013](https://go.microsoft.com/fwlink/?LinkId=328950)|Servizi Web Exchange|  
|[Microsoft OWIN](https://go.microsoft.com/fwlink/?LinkId=328951)|Microsoft OWIN|  
|[Microsoft Web Developer Tools 2013](https://go.microsoft.com/fwlink/?LinkId=328952)|Microsoft Web Developer Tools 2013|  
|Gli aggiornamenti di questi componenti vengono distribuiti tramite NuGet e non seguono i criteri relativi al ciclo di vita standard di Microsoft.  Per altre informazioni, vedere [http://docs.nuget.org/](https://docs.microsoft.com/nuget/).|Gestore dei token Web JSON per Microsoft .NET Framework 4.5<br /><br /> NuGet 2.7<br /><br /> SignalR<br /><br /> Framework di ottimizzazione Web<br /><br /> WebGrease|  
|[ODataLib](https://go.microsoft.com/fwlink/?LinkId=328954)|ODataLib|  
|[Office 2013](https://support.microsoft.com/lifecycle/search/?p1=16674)|Open XML SDK|  
|[Criteri di Online Services](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy)|Microsoft Ads SDK|  
|[SharePoint 2013](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=sharepoint%20server%202013&Filter=FilterNO)|Componente client di SharePoint<br /><br /> SharePoint Foundation 2013<br /><br /> Estensioni di Windows Identity Foundation|  
|[Silverlight 5](https://support.microsoft.com/lifecycle/search/?p1=16278)<br /><br /> <br />> Vedere anche: [http://support.microsoft.com/gp/lifean45](https://support.microsoft.com/gp/lifean45)|Silverlight 5 Runtime<br /><br /> Silverlight 5 SDK|  
|[SQL Server 2008 R2](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202008%20R2&Filter=FilterNO)|Tipi CLR di sistema SQL (SQL Server 2008 R2)|  
|[SQL Server 2012](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202012&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> SQL Command Line Utilities<br /><br /> Servizio di linguaggio SQL - IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2012 SP1<br /><br /> Tipi CLR di sistema SQL (SQL Server 2012)<br /><br /> SQLDOM|  
|[SQL Server 2014](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202014&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> SQL Command Line Utilities<br /><br /> Servizio di linguaggio SQL - IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2014<br /><br /> Tipi CLR di sistema SQL (SQL Server 2014)<br /><br /> SQLDOM|  
|[SQL Server Compact Edition 4.0](https://support.microsoft.com/lifecycle/search/?p1=16106)|SQL Server Compact Edition 4.0|  
|[WCF RIA Services v1.0 SP2](https://go.microsoft.com/fwlink/?LinkId=328955)|WCF RIA Services v1.0 SP2|  
|[Windows Server 2008](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=Windows%20Server%202008&Filter=FilterNO)|Servizi Web Windows (WWS) per Windows Server 2008|  
|[Windows 7](https://support.microsoft.com/lifecycle/search/?c2=14019)|Windows 7 SDK|  
|[Windows 8](https://support.microsoft.com/lifecycle/search/?c2=16796)|Windows 8 SDK|  
|[Windows 8.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=windows%208.1&Filter=FilterNO)|Windows 8.1 SDK<br /><br /> Libreria Windows per JavaScript (WinJS)|  
|[Microsoft Azure](https://support.microsoft.com/help/18486/lifecycle-faq-azure)<br /><br /> <br />> Vedere anche: [criteri del ciclo](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy) di vita online|SDK di Servizi mobili di Microsoft Azure<br /><br /> Strumenti di Servizi mobili di Microsoft Azure|