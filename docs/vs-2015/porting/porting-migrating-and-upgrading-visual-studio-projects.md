---
title: Portabilità, migrazione e aggiornamento dei progetti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
caps.latest.revision: 108
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 0f41abab206362ea60fafa30f2abcbf5eb474ddc
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849920"
---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Trasferire, migrare e aggiornare progetti di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio, vedere [Informazioni di riferimento per la migrazione e l'aggiornamento di un progetto per Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects).

Quando si sta valutando se è necessario passare a una versione più recente di Visual Studio, è possibile usare questo articolo per scoprire quali soluzioni, progetti, file e altre risorse create in Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1 verranno eseguiti senza modifiche in Visual Studio 2013 e Visual Studio 2015. Oppure è possibile che questa pagina sia stata raggiunta se è apparso un messaggio di errore quando si è tentato di aprire un progetto che non è supportato nella versione di Visual Studio in uso o che richiede un SDK o un'estensione, ad esempio Azure SDK per .NET.

Molte risorse molto diffuse hanno lo stesso comportamento in Visual Studio 2015, Visual Studio 2013 e nelle due versioni precedenti. In Visual Studio 2015, ad esempio, è possibile aprire un progetto creato in Visual Studio 2013 o Visual Studio 2012, modificarlo e quindi riaprirlo in Visual Studio 2015. Le modifiche vengono mantenute e il comportamento del progetto è identico a quello della versione precedente. Lo stesso vale per molte risorse create in Visual Studio 2010 SP1.

Per Visual Basic, Visual Studio 2015 non ha introdotto modifiche che impediranno la compilazione di un'app Visual Basic creata in Visual Studio 2013. Il comportamento in fase di esecuzione delle app Visual Basic che vengono ricompilate con Visual Studio 2015 non verrà modificato.

Se si usa Visual Studio 2015 con Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1, è possibile creare e modificare i progetti e i file in una qualsiasi di queste versioni. È possibile trasferire i progetti e i file tra le versioni purché non si aggiungano funzionalità non supportate in una o più versioni.

## <a name="project"></a> Progetti

Nell'elenco seguente viene descritto il supporto in Visual Studio 2015 e Visual Studio 2013 per i progetti creati in Visual Studio 2012 o Visual Studio 2010 SP1. Usare questo elenco per determinare se è possibile aprire un progetto "così com'è" in Visual Studio 2015, Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1 o se è necessario modificarlo per garantire la compatibilità.

|Tipo di progetto|Compatibilità|
|---------------------|-------------------|
|App della piattaforma UWP (Universal Windows Platform)|Per installare gli strumenti per app Windows universali, nel programma di installazione di Visual Studio, selezionare **Personalizzato** o **Modifica**, quindi selezionare **Strumenti di sviluppo di app Windows universali**.<br /><br /> Lo sviluppo di app piattaforma UWP (Universal Windows Platform) (UWP) per Windows 10 è supportato solo in Visual Studio 2015 in Windows 10 o [!INCLUDE[win81](../includes/win81-md.md)].|
|App di Windows Store|Lo sviluppo di app Windows Store, tra cui app universali per Windows 8.1 e Windows Phone 8.1 è supportato in [!INCLUDE[win81](../includes/win81-md.md)] e in Windows 10. È possibile continuare a gestire i progetti [!INCLUDE[win8](../includes/win8-md.md)] esistenti, ma non è possibile creare nuovi progetti [!INCLUDE[win8](../includes/win8-md.md)] . I progetti [!INCLUDE[win81](../includes/win81-md.md)] possono dipendere solo da alcuni tipi di riferimenti. Per altre informazioni, vedere [Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md). **Nota:** non è possibile aprire i progetti[!INCLUDE[win81](../includes/win81-md.md)] creati con visual studio 2015 o Visual Studio 2013 in visual Studio 2012. Ciò è dovuto al fatto che [!INCLUDE[win81](../includes/win81-md.md)] progetti creati con Visual Studio 2015 e Visual Studio 2013 sono destinati a tali versioni e Visual Studio 2012 supporta solo [!INCLUDE[win8](../includes/win8-md.md)] progetti destinati [!INCLUDE[win8](../includes/win8-md.md)].|
|[!INCLUDE[net_v451](../includes/net-v451-md.md)]|È possibile creare e usare questi progetti in Visual Studio 2015 e Visual Studio 2013 dopo aver installato il multitargeting Pack appropriato. Questi progetti non sono supportati in Visual Studio 2010 SP1.|
|[!INCLUDE[net_v45](../includes/net-v45-md.md)]|È possibile creare e aprire questi progetti in Visual Studio 2015, Visual Studio 2013 e Visual Studio 2012, ma non in Visual Studio 2010 SP1.|
|BizTalk|I progetti BizTalk Server non sono compatibili con Visual Studio 2015 o Visual Studio 2013.|
|Libreria di classi o applicazione Silverlight 4 in C#/Visual Basic|Se si consente a Visual Studio di aggiornare automaticamente il progetto, è possibile aprirlo sia in Visual Studio 2013 che in Visual Studio 2012.|
|Windows Form o Webform in C#/Visual Basic|È possibile aprire il progetto in Visual Studio 2013 e Visual Studio 2012.|
|Visual Basic 6 e Visual C++ 6|Visual Studio 2012 e Visual Studio 2013 non supportano il debug di applicazioni compilate con Visual Basic C++ 6 o Visual 6; per eseguire il debug di queste applicazioni, usare le versioni precedenti di Visual Studio.|
|Test codificato dell'interfaccia utente|Se si consente a Visual Studio di aggiornare automaticamente il progetto, è possibile aprirlo in Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1.|
|F#|Se si consente a Visual Studio di aggiornare un progetto creato in Visual Studio 2010 SP1, è possibile aprirlo in Visual Studio 2013 e Visual Studio 2012. Tuttavia, non è possibile aggiornare un progetto Silverlight creato in una versione precedente di Visual Studio per Visual Studio 2013. Al contrario, è necessario creare un progetto Silverlight in Visual Studio 2013, quindi copiarvi il codice. I progetti Silverlight creati in Visual Studio 2013 sono destinati a Silverlight 5.|
|LightSwitch|Se si consente a Visual Studio di aggiornare automaticamente il progetto, è possibile aprirlo solo in Visual Studio 2013.|
|Cache database locale|Il modello della cache del database locale e la finestra di dialogo **Configura sincronizzazione dati** non sono inclusi in Visual Studio 2013. È possibile utilizzare Visual Studio 2013 per aprire ed eseguire progetti creati in [!INCLUDE[vs2010](../includes/vs2010-md.md)] se è installato Microsoft Synchronization Services v 1.0, ma se si desidera aggiornarli in Visual Studio 2013, è necessario apportare manualmente tutte le modifiche nel codice. In alternativa, è possibile continuare a usare [!INCLUDE[vs2010](../includes/vs2010-md.md)] per gestire e aggiornare questi progetti.  Per un nuovo sviluppo, fare riferimento al nuovo modello di sincronizzazione fornito da Microsoft Sync Framework. Per informazioni, vedere il [Centro per sviluppatori di Microsoft Sync Framework](https://msdn.microsoft.com/sync/default)|
|Framework MVC (Model-View-Controller)|Visual Studio 2010 SP1 supporta solo MVC 2 e MVC 3, Visual Studio 2012 supporta solo MVC 3 e MVC 4 e Visual Studio 2013 supporta solo MVC 4. Per informazioni su come eseguire automaticamente l'aggiornamento da MVC 2 a MCV 3, vedere [ASP.NET MVC 3 Application Upgrader](https://aspnet.codeplex.com/releases/view/59008). Per informazioni su come eseguire manualmente l'aggiornamento da MVC 2 a MVC 3, vedere l'articolo sugli [strumenti di aggiornamento da un progetto ASP.NET MVC 2 ad ASP.NET MVC 3](https://aspnet.codeplex.com/releases/view/59008). Per informazioni su come eseguire manualmente l'aggiornamento da MVC 3 a MVC 4, vedere l'articolo sull' [aggiornamento da un progetto ASP.NET MVC 3 ad ASP.NET MVC 4](https://docs.microsoft.com/aspnet/whitepapers/mvc4-release-notes). Se il progetto è destinato a .NET Framework 3.5 SP1, è necessario modificare la destinazione per usarlo in .NET Framework 4.|
|Modellazione|Se si consente a Visual Studio di aggiornare automaticamente il progetto, è possibile aprirlo in Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1.<br /><br /> Quando si crea un progetto di modellazione, Team Foundation tenta di convalidare i livelli nel progetto. In Visual Studio 2013 Team Foundation Build non può convalidare i livelli per un progetto di modellazione creato in Visual Studio 2010 SP1. Tuttavia, in Visual Studio 2010 SP1, Team Foundation Build può convalidare i livelli in un progetto di modellazione creato in Visual Studio 2013.|
|Debugging MPI/cluster|Se la stessa versione di runtime o di strumenti è installata nei computer che eseguono Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1, è possibile aprire il progetto in tutte e tre le versioni.|
|Installazione MSI (con estensione VDPROJ)|Questo progetto non può essere aperto in Visual Studio 2013 perché non supporta tale tipo di progetto. Si consiglia di usare InstallShield Limited Edition per Visual Studio (ISLE), una soluzione a distribuzione libera che supporta direttamente la maggior parte delle piattaforme Windows e dei runtime delle applicazioni. È possibile usare ISLE anche per importare i dati e le impostazioni dai progetti del programma di installazione di Visual Studio. senza subire modifiche.|
|Office 2007 VSTO|Se si aggiorna il progetto a Office 2013 e a .NET Framework 4, è possibile aprire il progetto in Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1.|
|Office 2010 VSTO|Se il progetto è destinato a .NET Framework 4, è possibile aprirlo in Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1. Tutti gli altri progetti richiedono un aggiornamento unidirezionale.|
|Applicazioni Internet avanzate|Se si aggiorna il progetto, è possibile aprirlo in Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1.|
|SharePoint 2007|Questo progetto non può essere aperto in Visual Studio 2013. Tuttavia, se si aggiorna manualmente il progetto a SharePoint 2010, è possibile aprirlo in Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1. Per altre informazioni su come aggiornare SharePoint 2007, vedere [Migrating from SharePoint 2007 to SharePoint 2010 for the IT Pro](https://channel9.msdn.com/Blogs/matthijs/Migrating-from-SharePoint-2007-to-SharePoint-2010-for-the-IT-Pro) (Migrazione da SharePoint 2007 a SharePoint 2010 per professionisti IT) e [SharePoint Enterprise Search Migration Tool for SharePoint Server 2010 (Strumento di migrazione e ricerca di SharePoint Enterprise per SharePoint Server 2010)](https://docs.microsoft.com/previous-versions/office/developer/sharepoint-2010/ee556856(v%3Doffice.14)).|
|SharePoint 2010|È possibile aprire il progetto in Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1.|
|SketchFlow|Se si consente a Visual Studio di aggiornare il progetto a WPF 4.5/Silverlight 5, è possibile aprirlo in Visual Studio 2012 e Visual Studio 2013.|
|Database [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)]|È possibile aprire il progetto in Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1. Se si dispone di un file di database (con estensione MDF) creato in una versione precedente di SQL Server, è necessario aggiornarlo a [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] prima di poterlo usare con SQL Server Express LocalDB, ma il database non sarà più compatibile con le versioni precedenti di SQL Server. Se non si esegue l'aggiornamento, è possibile continuare a utilizzare il database in Visual Studio 2013 installando e utilizzando [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] nello stesso computer. Per altre informazioni, vedere [Aggiornare i file con estensione mdf](../data-tools/upgrade-dot-mdf-files.md).|
|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express|Se [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express è installato nei computer che eseguono Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1, è possibile aprire il progetto in tutte e tre le versioni.|
|Progetto report di SQL Server|È possibile aprire il progetto in Visual Studio 2013 e Visual Studio 2012. Solo per la modalità locale, ovvero quando non si è connessi a SQL Server, non si otterrà la fase di progettazione dei controlli associati al visualizzatore in [!INCLUDE[vs2010](../includes/vs2010-md.md)], ma il progetto funzionerà correttamente in fase di esecuzione. **Attenzione:**  Se si aggiunge una funzionalità specifica di Visual Studio 2013, lo schema del report viene aggiornato automaticamente e non è più possibile aprire il progetto in Visual Studio 2012.|
|Unit test|È possibile utilizzare [!INCLUDE[TCMext](../includes/tcmext-md.md)] in Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1 per aprire i test creati in una qualsiasi di queste versioni.|
|Visual C++|È possibile usare Visual Studio 2013 per aprire un C++ progetto creato in visual Studio 2012 o visual Studio 2010 SP1. Se si vuole usare l'ambiente di compilazione Visual Studio 2013 per compilare un progetto creato in Visual Studio 2012, è necessario che entrambe le versioni di Visual Studio siano installate nello stesso computer. Per altre informazioni, vedere [Procedura: aggiornare i progetti Visual C++ a Visual Studio 2015](../porting/how-to-upgrade-visual-cpp-projects-to-visual-studio-2015.md) e [Guida al porting e aggiornamento in Visual C++](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb).|
|Visual Studio 2010 per il Web|Se si consente a Visual Studio di aggiornare automaticamente il progetto, è possibile aprirlo in Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1.|
|Database Visual Studio 2010 (con estensione DBPROJ)|Se si converte il progetto in un progetto di database di SQL Server Data Tools, è possibile aprirlo Visual Studio 2013. Tuttavia, Visual Studio 2013 non supporta questi elementi:<br /><br /> -   unit test<br />-   piani di generazione dati<br />-   file di confronto dati<br />-   estensioni di regole personalizzate per l'analisi statica del codice<br />-   server.sqlsettings<br />-   file con estensione sqlcmd<br />-   estensioni di distribuzione personalizzate<br />-   progetti parziali (con estensione files)<br /><br /> Se si installa SQL Server Data Tools, è possibile aprire il progetto in Visual Studio 2010 SP1 dopo la conversione. Per altre informazioni, vedere [Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx).|
|Visual Studio 2010 Visual Database Tools|È possibile aprire il progetto in Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1.|
|Visual Studio Lab Management|È possibile utilizzare [!INCLUDE[TCMext](../includes/tcmext-md.md)], Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1 per aprire gli ambienti creati in una qualsiasi di queste versioni. Tuttavia, per creare gli ambienti è necessario che la versione di Microsoft Test Manager corrisponda alla versione di Team Foundation Server.|
|Visual Studio Macro|Questo progetto non può essere aperto in Visual Studio 2013 perché non supporta il tipo di progetto.|
|Visual Studio SDK/VSIX|Dopo aver aggiornato un progetto di Visual Studio SDK a Visual Studio 2013, non è possibile aprirlo in Visual Studio 2012. Per altre informazioni, vedere [Procedura: Eseguire la migrazione di progetti di estendibilità in Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md).|
|Strumenti di Microsoft Azure per Visual Studio|Se si usa strumenti di Microsoft Azure per Visual Studio versione 2,1, è possibile aprire il progetto in Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1. Per i progetti destinati a versioni precedenti, se si consente a Visual Studio di aggiornare il progetto alla versione 2,1, è possibile aprirlo in Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1.|
|Windows Communication Foundation, Windows Presentation Foundation|È possibile aprire il progetto in Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1.|
|Windows Mobile|Questo progetto non può essere aperto in Visual Studio 2013 perché non supporta il tipo di progetto.|
|Windows Phone 7.1|Se si consente a Visual Studio di aggiornare il progetto a Windows Phone 8,0, è possibile aprirlo in Visual Studio 2012 e Visual Studio 2013.|
|Altro|È possibile aprire la maggior parte degli altri tipi di progetti in Visual Studio 2012, Visual Studio 2013 e Visual Studio 2010 SP1.|
|Siti Web di FrontPage|Questo progetto non può essere aperto in Visual Studio 2013 perché non supporta il tipo di progetto.|
|Libreria di classi portabile|Se si consente a Visual Studio di aggiornare automaticamente il progetto, è possibile aprirlo in Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1.<br /><br /> -   I progetti creati per Silverlight 4 saranno destinati a Silverlight 5.<br />-   I progetti creati per Windows Phone 7.0 o Windows Phone 7.5 saranno destinati a Windows Phone 8.<br />-   I progetti creati per Xbox 360 non saranno più destinati a Xbox 360.|
|Progetti di Azure, ad esempio cloud service progetti (con estensione. ccproj) e Gestione risorse di Azure (progetti di distribuzione Cloud) con l'estensione .deployproj|Per aprire questi tipi di progetti, installare innanzitutto [Azure SDK per .NET](https://azure.microsoft.com/downloads/), quindi aprire il progetto.|

## <a name="troubleshooting-project-compatibility-issues"></a>Risoluzione dei problemi di compatibilità del progetto
 Di seguito sono riportate alcune operazioni che è possibile eseguire quando un progetto non viene aperto in Visual Studio 2015 o Visual Studio 2013:

- Se si tenta di aprire un progetto non supportato in Visual Studio 2015 o Visual Studio 2013 e per il quale la versione associata di Visual Studio non è installata, potrebbe essere visualizzato un messaggio che il tipo di progetto non è supportato e il tipo di progetto potrebbe essere elencato nella finestra di dialogo **Controlla modifiche a progetti e soluzioni** in **progetti non supportati**. Per risolvere questo problema, aprire la pagina Programmi e funzionalità nel **Pannello di controllo**di Windows, selezionare **Visual Studio**, quindi scegliere **Cambia**, **Ripristina**. È quindi possibile installare la versione mancante.

- Se si tenta di aprire un progetto per un'app desktop in [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)], si verifica un errore e viene visualizzato uno dei messaggi seguenti: "Questa edizione di Visual Studio supporta solo applicazioni [!INCLUDE[win81](../includes/win81-md.md)]" oppure "Il progetto non è compatibile con la versione attuale di Visual Studio". [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] è limitato allo sviluppo, al test e alla distribuzione di applicazioni Windows Store progettate per Windows 8.1. Per aprire un progetto di un'applicazione desktop, è necessario usare un'edizione di Visual Studio che supporti tale tipo di progetto.

   Per altre informazioni sulle edizioni di Visual Studio, vedere [Prodotti Microsoft Visual Studio](https://visualstudio.microsoft.com/products/)

- Se si tenta di aprire un progetto di applicazioni Windows Store in [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop, si verifica un errore. [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop non può essere usato per compilare le applicazioni Windows Store. Se si vuole compilare le applicazioni Windows Store, è anche possibile installare [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]. In alternativa, per sviluppare applicazioni per tutte le piattaforme Microsoft e il Web, provare Visual Studio Professional 2013.

- Se un progetto richiede funzionalità specifiche di Visual Studio 2013, non è possibile aprirlo in una versione precedente.

- Se si usa Visual Studio 2012 e si vuole aprire un progetto creato in Visual Studio 2013, potrebbe essere possibile personalizzare il sistema del progetto per incorporare le funzionalità di Visual Studio 2013. Per informazioni su questa procedura, vedere [Impostazione del riconoscimento della versione per i progetti personalizzati](../misc/making-custom-projects-version-aware.md).

  Per altre informazioni sulla risoluzione dei problemi, vedere l'articolo della Knowledge Base sulla [compatibilità di Visual Studio 2013](https://support.microsoft.com/help/2863286/roundtrip-issues-for-visual-studio-2012-and-visual-studio-2013-preview) .

## <a name="file"></a> File

L'elenco seguente indica se Visual Studio 2013 supporta ogni tipo di file, se è possibile aprire il file in Visual Studio 2012 e Visual Studio 2010 SP1 e se è necessario modificarlo per garantire la compatibilità.

|Tipo di file|Compatibilità|
|------------------|-------------------|
|AppManifest, Inbrowsersettings, OutOfBrowserSettings (file XML)|È possibile aprire questi file in Visual Studio 2012, Visual Studio 2013 e Visual Studio 2010 SP1.|
|Schemi di file flat BizTalk|È possibile aggiungere questi schemi a un progetto BizTalk 2013 in Visual Studio 2013. Per utilizzare Visual Studio 2013 con progetti BizTalk 2010 con schemi di file flat, installare BizTalk 2013 nel computer in cui è presente Visual Studio 2013. La prima volta che si apre il progetto BizTalk 2010, questo viene aggiornato automaticamente al sistema di progetto BizTalk 2013 o Visual Studio 2013.|
|File di definizione del report (con estensione RDLC)|È possibile aprire questi file in Visual Studio 2013 e lo schema viene automaticamente aggiornato se si aggiungono Visual Studio 2013 funzionalità e i controlli.|
|Set di regole di analisi del codice|È possibile aprire questi file in Visual Studio 2012, Visual Studio 2013 e Visual Studio 2010 SP1.|
|File del pacchetto di applicazione livello dati|È possibile aprire questi file in Visual Studio 2013 se la versione è 2,0 o 2,5.|
|File dump di debugger|È possibile aprire questi file in Visual Studio 2012, Visual Studio 2013 e Visual Studio 2010 SP1.|
|File del diagramma Directed Graph Markup Language (DGML)|È possibile aprire questi file in Visual Studio 2012, Visual Studio 2013 e Visual Studio 2010 SP1 senza modificare il file.|
|File Entity Data Model (EDMX)|In Visual Studio 2013, è possibile aprire un file EDMX destinato al .NET Framework 4,5 o al .NET Framework 4 senza modificare il file.|
|File di report del profiler|È possibile aprire i file di report del profiler (con estensione vsp. vsps,. psess e. vspf) in Visual Studio 2012 e Visual Studio 2013. Non è possibile aprire un file VSPX in Visual Studio 2010 SP1.|
|File di soluzione (con estensione SUO)|È possibile usare Visual Studio 2013 per aprire un file di soluzione creato in Visual Studio 2012 o Visual Studio 2010 SP1|
|SQL Server Compact Edition|Visual Studio 2013 non supporta SQL Server Compact Edition.|
|File SQLX|Per aprire questi file in Visual Studio 2013, è necessario eseguire un aggiornamento unidirezionale, distribuire il file con estensione sqlx nella versione di destinazione di Visual Studio, quindi ricompilare il file nel formato DACPAC.|
|File di log IntelliTrace di [!INCLUDE[vs2010](../includes/vs2010-md.md)]|È possibile aprire questi file in Visual Studio 2012, Visual Studio 2013 e Visual Studio 2010 SP1.|
|File di JavaScript Memory Analyzer (con estensione DIAGSESSION)|I file creati da versioni precedenti di Visual Studio possono essere visualizzati in Visual Studio 2013. Tuttavia, a seconda delle informazioni raccolte, i file creati in Visual Studio 2013 potrebbero non essere aperti in Visual Studio 2012 o Visual Studio 2010 SP1.|

## <a name="integration"></a> Asset di integrazione

Potrebbero verificarsi problemi di compatibilità se si usano client e server di versioni di Visual Studio Team Foundation Server differenti.

|Tipo di integrazione|Compatibilità|
|-------------------------|-------------------|
|Revisione del codice e Lavoro|Le funzionalità Revisione del codice e Lavoro non funzionano se si connette un client di [!INCLUDE[esprfound](../includes/esprfound-md.md)] a [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)].|
|[!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)]|Non è possibile usare un ambiente a 64 bit come MSBuild o [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] per compilare applicazioni [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] create in [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)].|

## <a name="see-also"></a>Vedere anche

- [Impostazione del riconoscimento della versione per i progetti personalizzati](../misc/making-custom-projects-version-aware.md)
