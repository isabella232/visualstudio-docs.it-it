---
title: Assembly nel Strumenti di Visual Studio per Office Runtime
description: Informazioni su come Visual Studio aggiunge automaticamente i riferimenti alla Strumenti di Visual Studio per gli assembly di Office Runtime.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 86c3c2b77b6bbea1e609bbea092b44bd1dee1dd4
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848300"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Assembly nel Strumenti di Visual Studio per Office Runtime
  Quando si crea un progetto di Office, in Visual Studio vengono automaticamente aggiunti riferimenti agli assembly [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] usati per il tipo di progetto e .NET Framework di destinazione del progetto. Sono disponibili diversi assembly nelle estensioni di Office per .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]e [!INCLUDE[net_v45](includes/net-v45-md.md)]. Per altre informazioni sulle estensioni di Office, vedere [Panoramica di strumenti di Visual Studio per Office Runtime](visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-net_v45"></a>Assembly nelle estensioni di Office per il .NET Framework 4 e [!INCLUDE[net_v45](includes/net-v45-md.md)]
 Nella tabella seguente sono elencati gli assembly che vengono inclusi nelle estensioni di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e [!INCLUDE[net_v45](includes/net-v45-md.md)]. Per la documentazione sugli spazi dei nomi e sui tipi di questi assembly, vedere informazioni di [riferimento gestite &#40;sviluppo di Office in Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md).

|Nome assembly|Descrizione|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.dll|Fornisce i seguenti tipi:<br /><br /> -Tipi per la creazione di personalizzazioni della barra multifunzione e smart tag. **Nota:**      Gli smart tag sono deprecati in [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />-Tipi per la creazione di riquadri azioni nelle personalizzazioni a livello di documento e nei riquadri attività personalizzati nei componenti aggiuntivi VSTO.|
|Microsoft.Office.Tools.Excel.dll|Fornisce interfacce che rappresentano elementi host e controlli host per i progetti di Excel e tipi di supporto. Per altre informazioni, vedere [automatizzare Excel usando oggetti estesi](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.dll|Fornisce tipi che è possibile usare per creare aree del modulo personalizzate in componenti aggiuntivi VSTO di Outlook.|
|Microsoft.Office.Tools.Word.dll|Fornisce interfacce che rappresentano elementi host e controlli host per i progetti di Word e tipi di supporto. Per altre informazioni, vedere [automatizzare Word usando oggetti estesi](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v4.0.Framework.dll|Fornisce i seguenti tipi:<br /><br /> : Eccezioni che possono essere generate dal Strumenti di Visual Studio per Office Runtime.<br />-Attributi che è possibile usare per la creazione di aree del modulo di Outlook.|
|Microsoft.Office.Tools.dll|Fornisce i tipi che fanno parte dell'infrastruttura runtime di Visual Studio Tools per Office e che non è previsto vengano usati direttamente dal codice.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Fornisce i seguenti tipi:<br /><br /> : L' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo e l' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaccia, che è possibile usare per memorizzare nella cache gli oggetti dati in una personalizzazione a livello di documento. Per altre informazioni, vedere [memorizzare i dati nella cache](caching-data.md).<br />- <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> Interfaccia, che è possibile implementare per eseguire ulteriori passaggi di installazione come passaggio finale del programma di installazione ClickOnce per una soluzione Office. Per altre informazioni, vedere [distribuire una soluzione Office tramite ClickOnce](deploying-an-office-solution-by-using-clickonce.md).<br />: Eccezioni che possono essere generate dal Strumenti di Visual Studio per Office Runtime.<br />-Altri tipi che fanno parte dell'infrastruttura di Strumenti di Visual Studio per Office Runtime e che non sono destinati a essere usati direttamente dal codice.|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Fornisce i seguenti tipi:<br /><br /> : La <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe, che è possibile usare per alleghi gli assembly di personalizzazione ai documenti e per accedere ai dati memorizzati nella cache nei documenti. Per altre informazioni, vedere [Manage Documents on a server by using the ServerDocument Class](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Varie classi che rappresentano la gerarchia dei dati memorizzati nella cache in una personalizzazione a livello di documento. Per ulteriori informazioni, vedere [accedere ai dati nei documenti sul server](accessing-data-in-documents-on-the-server.md).|

 I progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](includes/net-v45-md.md)] fanno riferimento agli assembly seguenti. Questi assembly non fanno parte del [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] ridistribuibile. Sono invece gli assembly dipendenti che devono essere distribuiti con la soluzione. Per impostazione predefinita, vengono copiati nella cartella di output di compilazione del progetto (la proprietà **Copia localmente** di questi assembly è impostata su **True**). Se si distribuisce il progetto tramite ClickOnce, questi assembly vengono inclusi nel pacchetto generato.

|Nome assembly|Descrizione|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Fornisce le classi base per la classe `ThisAddIn` generata nei progetti di componente aggiuntivo VSTO e la classe Ribbon generata in tutti i progetti.|
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Fornisce i seguenti tipi:<br /><br /> -Classi di base per le `ThisWorkbook` classi e generate `Sheet` nei progetti a livello di documento per Excel.<br />-Windows Forms i controlli che è possibile usare nei fogli di lavoro nei progetti di Excel.|
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Fornisce le classi di base le classi `ThisAddIn` e le classi dell'area del modulo generate nei progetti di Outlook.|
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Fornisce i seguenti tipi:<br /><br /> -Classi base per la `ThisDocument` classe generata nei progetti a livello di documento per Word.<br />-Windows Forms i controlli che è possibile usare nei documenti in progetti Word.|

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Assembly nelle estensioni di Office per il .NET Framework 3,5
 Nella tabella seguente sono elencati gli assembly che vengono inclusi nelle estensioni di Office per .NET Framework 3.5. Per la documentazione sugli spazi dei nomi e le classi in questi assembly, vedere la sezione di riferimento seguente nella documentazione di Visual Studio 2008: [http://go.microsoft.com/fwlink/?LinkId=160658](managed-reference-office-development-in-visual-studio.md) .

|Nome assembly|Descrizione|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v9.0.dll|Fornisce i seguenti tipi:<br /><br /> -La classe di base Microsoft. Office. Tools. AddIn per i componenti aggiuntivi VSTO.<br />-Classi per la creazione di personalizzazioni della barra multifunzione e smart tag. **Nota:**      Gli smart tag sono deprecati in [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />-Classi per la creazione di riquadri azioni nelle personalizzazioni a livello di documento e nei riquadri attività personalizzati nei componenti aggiuntivi VSTO.|
|Microsoft.Office.Tools.Excel.v9.0.dll|Fornisce gli elementi host e i controlli host per le soluzioni Excel. Per altre informazioni, vedere [automatizzare Excel usando oggetti estesi](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.v9.0.dll|Fornisce classi che è possibile usare per creare arre del modulo personalizzate in componenti aggiuntivi VSTO di Outlook.|
|Microsoft.Office.Tools.Word.v9.0.dll|Fornisce gli elementi host e i controlli host per le soluzioni Word. Per altre informazioni, vedere [automatizzare Word usando oggetti estesi](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v9.0.dll|Fornisce i seguenti tipi:<br /><br /> : La classe [RemoteBindableComponent](/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) , che fornisce le funzionalità data binding per i controlli host nelle personalizzazioni a livello di documento.<br />-Altri tipi che fanno parte dell'infrastruttura di Strumenti di Visual Studio per Office Runtime e che non sono destinati a essere usati direttamente dal codice.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Fornisce i seguenti tipi:<br /><br /> : L' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo e l' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaccia, che è possibile usare per memorizzare nella cache gli oggetti dati in una personalizzazione a livello di documento. Per altre informazioni, vedere [memorizzare i dati nella cache](caching-data.md).<br />: Eccezioni che possono essere generate dal Strumenti di Visual Studio per Office Runtime.<br />-Altri tipi che fanno parte dell'infrastruttura di Strumenti di Visual Studio per Office Runtime e che non sono destinati a essere usati direttamente dal codice.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Fornisce l’interfaccia <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>, che è possibile implementare per eseguire ulteriori passaggi di installazione, come il passaggio finale del programma di installazione ClickOnce per una soluzione Office. Per altre informazioni, vedere [distribuzione avanzata di soluzioni Office](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Fornisce i seguenti tipi:<br /><br /> : La <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe, che è possibile usare per alleghi a livello di codice gli assembly di personalizzazione ai documenti e per accedere ai dati memorizzati nella cache nei documenti. Per altre informazioni, vedere [Manage Documents on a server by using the ServerDocument Class](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Varie classi che rappresentano la gerarchia dei dati memorizzati nella cache in una personalizzazione a livello di documento. Per ulteriori informazioni, vedere [accedere ai dati nei documenti sul server](accessing-data-in-documents-on-the-server.md).|
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Fornisce i seguenti tipi:<br /><br /> -Le classi Microsoft. VisualStudio. Tools. Office. Runtime. Security. AddInSecurityEntry e Microsoft. VisualStudio. Tools. Office. Runtime. Security. UserInclusionList, che è possibile usare per creare voci dell'elenco di inclusione utente per concedere l'attendibilità alle soluzioni Office destinate al .NET Framework 3,5.<br />-Altri tipi che fanno parte dell'infrastruttura di Strumenti di Visual Studio per Office Runtime e che non sono destinati a essere usati direttamente dal codice.|

## <a name="see-also"></a>Vedi anche
- [Panoramica di Strumenti di Visual Studio per Office Runtime](visual-studio-tools-for-office-runtime-overview.md)
- [Scenari di installazione di Strumenti di Visual Studio per Office Runtime](visual-studio-tools-for-office-runtime-installation-scenarios.md)
