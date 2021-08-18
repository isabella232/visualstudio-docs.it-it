---
title: Assembly nel runtime Visual Studio Tools per Office runtime
description: Informazioni su Visual Studio automaticamente i riferimenti agli assembly Visual Studio Tools per Office runtime.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a811040f9106666a86778db4a8278d0f5f450855
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083778"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Assembly nel runtime Visual Studio Tools per Office runtime
  Quando si crea un progetto di Office, in Visual Studio vengono automaticamente aggiunti riferimenti agli assembly [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] usati per il tipo di progetto e .NET Framework di destinazione del progetto. Sono disponibili diversi assembly nelle estensioni di Office per .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]e [!INCLUDE[net_v45](includes/net-v45-md.md)]. Per altre informazioni sulle estensioni Office, vedere panoramica Visual Studio Tools per Office [runtime](visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-net_v45"></a>Assembly nelle estensioni Office per .NET Framework 4 e[!INCLUDE[net_v45](includes/net-v45-md.md)]
 Nella tabella seguente sono elencati gli assembly che vengono inclusi nelle estensioni di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e [!INCLUDE[net_v45](includes/net-v45-md.md)]. Per la documentazione sugli spazi dei nomi e sui tipi in questi assembly, vedere Riferimento gestito &#40;Office [sviluppo in Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md).

|Nome assembly|Descrizione|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.dll|Fornisce i seguenti tipi:<br /><br /> : tipi per la creazione di personalizzazioni e smart tag della barra multifunzione. **Nota:**      Gli smart tag sono deprecati in [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />- Tipi per la creazione di riquadri azioni nelle personalizzazioni a livello di documento e riquadri attività personalizzati in VSTO componenti aggiuntivi.|
|Microsoft.Office.Tools.Excel.dll|Fornisce interfacce che rappresentano elementi host e controlli host per i progetti di Excel e tipi di supporto. Per altre informazioni, vedere [Automatizzare Excel tramite oggetti estesi.](automating-excel-by-using-extended-objects.md)|
|Microsoft.Office.Tools.Outlook.dll|Fornisce tipi che è possibile usare per creare aree del modulo personalizzate in componenti aggiuntivi VSTO di Outlook.|
|Microsoft.Office.Tools.Word.dll|Fornisce interfacce che rappresentano elementi host e controlli host per i progetti di Word e tipi di supporto. Per altre informazioni, vedere [Automatizzare Word tramite oggetti estesi.](automating-word-by-using-extended-objects.md)|
|Microsoft.Office.Tools.v4.0.Framework.dll|Fornisce i seguenti tipi:<br /><br /> - Eccezioni che possono essere generate dal runtime Visual Studio Tools per Office runtime.<br />- Attributi che è possibile usare durante la creazione di aree Outlook modulo.|
|Microsoft.Office.Tools.dll|Fornisce i tipi che fanno parte dell'infrastruttura runtime di Visual Studio Tools per Office e che non è previsto vengano usati direttamente dal codice.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Fornisce i seguenti tipi:<br /><br /> - Attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> e <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaccia, che è possibile usare per memorizzare nella cache gli oggetti dati in una personalizzazione a livello di documento. Per altre informazioni, vedere [Memorizzare nella cache i dati](caching-data.md).<br />- Interfaccia che è possibile implementare per eseguire passaggi di installazione aggiuntivi come passaggio finale del programma di installazione ClickOnce <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> per una Office soluzione. Per altre informazioni, vedere [Deploy an Office solution by using ClickOnce](deploying-an-office-solution-by-using-clickonce.md).<br />- Eccezioni che possono essere generate dal runtime Visual Studio Tools per Office runtime.<br />- Altri tipi che fanno parte dell'infrastruttura Visual Studio Tools per Office runtime e non devono essere usati direttamente dal codice.|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Fornisce i seguenti tipi:<br /><br /> - Classe , che è possibile usare per associare assembly di personalizzazione ai documenti <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> e per accedere ai dati memorizzati nella cache nei documenti. Per altre informazioni, vedere [Gestire documenti in un server usando la classe ServerDocument](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />- Diverse classi che rappresentano la gerarchia dei dati memorizzati nella cache in una personalizzazione a livello di documento. Per altre informazioni, vedere [Accedere ai dati nei documenti nel server](accessing-data-in-documents-on-the-server.md).|

 I progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](includes/net-v45-md.md)] fanno riferimento agli assembly seguenti. Questi assembly non fanno parte del [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] ridistribuibile. Sono invece gli assembly dipendenti che devono essere distribuiti con la soluzione. Per impostazione predefinita, vengono copiati nella cartella di output di compilazione del progetto (la proprietà **Copia localmente** di questi assembly è impostata su **True**). Se si distribuisce il progetto tramite ClickOnce, questi assembly vengono inclusi nel pacchetto generato.

|Nome assembly|Descrizione|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Fornisce le classi base per la classe `ThisAddIn` generata nei progetti di componente aggiuntivo VSTO e la classe Ribbon generata in tutti i progetti.|
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Fornisce i seguenti tipi:<br /><br /> - Classi di base per le classi generate e nei progetti a livello di `ThisWorkbook` `Sheet` documento per Excel.<br />- Windows form che è possibile usare nei fogli di lavoro nei Excel progetti.|
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Fornisce le classi di base le classi `ThisAddIn` e le classi dell'area del modulo generate nei progetti di Outlook.|
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Fornisce i seguenti tipi:<br /><br /> - Classi di base per la `ThisDocument` classe generata nei progetti a livello di documento per Word.<br />- Windows form che è possibile usare nei documenti nei progetti word.|

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Assembly nelle estensioni Office per .NET Framework 3.5
 Nella tabella seguente sono elencati gli assembly che vengono inclusi nelle estensioni di Office per .NET Framework 3.5. Per la documentazione sugli spazi dei nomi e le classi in questi assembly, vedere la sezione di riferimento seguente nella documentazione Visual Studio 2008: [http://go.microsoft.com/fwlink/?LinkId=160658](managed-reference-office-development-in-visual-studio.md) .

|Nome assembly|Descrizione|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v9.0.dll|Fornisce i seguenti tipi:<br /><br /> - Microsoft. Office. Classe di base Tools.AddIn per VSTO componenti aggiuntivi.<br />- Classi per la creazione di personalizzazioni e smart tag della barra multifunzione. **Nota:**      Gli smart tag sono deprecati in [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />- Classi per la creazione di riquadri azioni nelle personalizzazioni a livello di documento e riquadri attività personalizzati in VSTO componenti aggiuntivi.|
|Microsoft.Office.Tools.Excel.v9.0.dll|Fornisce gli elementi host e i controlli host per le soluzioni Excel. Per altre informazioni, vedere [Automatizzare Excel tramite oggetti estesi.](automating-excel-by-using-extended-objects.md)|
|Microsoft.Office.Tools.Outlook.v9.0.dll|Fornisce classi che è possibile usare per creare arre del modulo personalizzate in componenti aggiuntivi VSTO di Outlook.|
|Microsoft.Office.Tools.Word.v9.0.dll|Fornisce gli elementi host e i controlli host per le soluzioni Word. Per altre informazioni, vedere [Automatizzare Word tramite oggetti estesi.](automating-word-by-using-extended-objects.md)|
|Microsoft.Office.Tools.v9.0.dll|Fornisce i seguenti tipi:<br /><br /> - Classe [RemoteBindableComponent,](/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) che fornisce le funzionalità data binding per i controlli host nelle personalizzazioni a livello di documento.<br />- Altri tipi che fanno parte dell'infrastruttura Visual Studio Tools per Office runtime e non devono essere usati direttamente dal codice.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Fornisce i seguenti tipi:<br /><br /> - Attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> e <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaccia, che è possibile usare per memorizzare nella cache gli oggetti dati in una personalizzazione a livello di documento. Per altre informazioni, vedere [Memorizzare nella cache i dati](caching-data.md).<br />- Eccezioni che possono essere generate dal runtime Visual Studio Tools per Office runtime.<br />- Altri tipi che fanno parte dell'infrastruttura Visual Studio Tools per Office runtime e non devono essere usati direttamente dal codice.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Fornisce l’interfaccia <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>, che è possibile implementare per eseguire ulteriori passaggi di installazione, come il passaggio finale del programma di installazione ClickOnce per una soluzione Office. Per altre informazioni, vedere [Advanced Office solution deployment](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Fornisce i seguenti tipi:<br /><br /> - Classe , che è possibile usare per associare a livello di codice assembly di personalizzazione ai documenti e <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> per accedere ai dati memorizzati nella cache nei documenti. Per altre informazioni, vedere [Gestire documenti in un server usando la classe ServerDocument](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />- Diverse classi che rappresentano la gerarchia dei dati memorizzati nella cache in una personalizzazione a livello di documento. Per altre informazioni, vedere [Accedere ai dati nei documenti nel server](accessing-data-in-documents-on-the-server.md).|
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Fornisce i seguenti tipi:<br /><br /> - Microsoft.VisualStudio.Tools. Office. Runtime.Security.AddInSecurityEntry e Microsoft.VisualStudio.Tools. Office. Classi Runtime.Security.UserInclusionList, che è possibile usare per creare voci dell'elenco di inclusione utente per concedere l'attendibilità alle soluzioni Office che hanno come destinazione .NET Framework 3.5.<br />- Altri tipi che fanno parte dell'infrastruttura Visual Studio Tools per Office runtime e non devono essere usati direttamente dal codice.|

## <a name="see-also"></a>Vedi anche
- [Visual Studio Tools per Office di runtime](visual-studio-tools-for-office-runtime-overview.md)
- [Visual Studio Tools per Office scenari di installazione di runtime](visual-studio-tools-for-office-runtime-installation-scenarios.md)
