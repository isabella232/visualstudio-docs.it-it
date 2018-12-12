---
title: Assembly in Visual Studio Tools per Office runtime
titleSuffix: ''
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 66ee95d4f102ac4206a9ed55a1fc97fc251c4f9c
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248112"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Assembly in Visual Studio Tools per Office runtime
  Quando si crea un progetto di Office, in Visual Studio vengono automaticamente aggiunti riferimenti agli assembly [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usati per il tipo di progetto e .NET Framework di destinazione del progetto. Sono disponibili diversi assembly nelle estensioni di Office per .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]e [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Per altre informazioni sulle estensioni di Office, vedere [Visual Studio Tools per Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>Gli assembly nelle estensioni Office per .NET Framework 4 e [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 Nella tabella seguente sono elencati gli assembly che vengono inclusi nelle estensioni di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Per la documentazione sugli spazi dei nomi e sui tipi in questi assembly, vedere [riferimenti gestiti di &#40;sviluppo per Office in Visual Studio&#41;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Nome assembly|Descrizione|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|Fornisce i seguenti tipi:<br /><br /> -Tipi per la creazione di personalizzazioni della barra multifunzione e smart tag. **Nota:**      Gli smart tag sono deprecati in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Tipi per la creazione dei riquadri azioni nelle personalizzazioni a livello di documento e riquadri attività personalizzati nei componenti aggiuntivi VSTO.|  
|Microsoft.Office.Tools.Excel.dll|Fornisce interfacce che rappresentano elementi host e controlli host per i progetti di Excel e tipi di supporto. Per altre informazioni, vedere [automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Fornisce tipi che è possibile usare per creare aree del modulo personalizzate in componenti aggiuntivi VSTO di Outlook.|  
|Microsoft.Office.Tools.Word.dll|Fornisce interfacce che rappresentano elementi host e controlli host per i progetti di Word e tipi di supporto. Per altre informazioni, vedere [automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Fornisce i seguenti tipi:<br /><br /> -Le eccezioni che possono essere generate da Visual Studio Tools per Office runtime.<br />-Attributi che durante la creazione di Outlook, è possibile usare aree del modulo.|  
|Microsoft.Office.Tools.dll|Fornisce i tipi che fanno parte dell'infrastruttura runtime di Visual Studio Tools per Office e che non è previsto vengano usati direttamente dal codice.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Fornisce i seguenti tipi:<br /><br /> -il <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo e <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaccia, che è possibile usare per memorizzare gli oggetti dati in una personalizzazione a livello di documento. Per altre informazioni, vedere [memorizzare nella Cache dati](../vsto/caching-data.md).<br />-La <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interfaccia, che è possibile implementare per eseguire ulteriori passaggi di installazione come passaggio finale del programma di installazione ClickOnce per una soluzione Office. Per altre informazioni, vedere [distribuire una soluzione Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-Le eccezioni che possono essere generate da Visual Studio Tools per Office runtime.<br />-Altri tipi che fanno parte di Visual Studio Tools per l'infrastruttura di runtime di Office e non deve essere usato direttamente dal codice.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Fornisce i seguenti tipi:<br /><br /> -La <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> (classe), che è possibile usare per collegare gli assembly di personalizzazione ai documenti e accedere ai dati memorizzati nella cache nei documenti. Per altre informazioni, vedere [gestire documenti in un server usando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Diverse classi che rappresentano la gerarchia dei dati in una personalizzazione a livello di documento memorizzati nella cache. Per altre informazioni, vedere [accedere ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 I progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] fanno riferimento agli assembly seguenti. Questi assembly non fanno parte del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ridistribuibile. Sono invece gli assembly dipendenti che devono essere distribuiti con la soluzione. Per impostazione predefinita, vengono copiati nella cartella di output di compilazione del progetto (la proprietà **Copia localmente** di questi assembly è impostata su **True**). Se si distribuisce il progetto tramite ClickOnce, questi assembly vengono inclusi nel pacchetto generato.  
  
|Nome assembly|Descrizione|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Fornisce le classi base per la classe `ThisAddIn` generata nei progetti di componente aggiuntivo VSTO e la classe Ribbon generata in tutti i progetti.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Fornisce i seguenti tipi:<br /><br /> -Classi di base generato `ThisWorkbook` e `Sheet` classi in a livello di documento i progetti di Excel.<br />-Controlli Windows Form che è possibile usare nei fogli di lavoro nei progetti di Excel.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Fornisce le classi di base le classi `ThisAddIn` e le classi dell'area del modulo generate nei progetti di Outlook.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Fornisce i seguenti tipi:<br /><br /> -Classi di base generato `ThisDocument` classi nei progetti a livello di documento per Word.<br />-Controlli Windows Form che è possibile usare nei documenti dei progetti di Word.|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Assembly nelle estensioni Office per .NET Framework 3.5  
 Nella tabella seguente sono elencati gli assembly che vengono inclusi nelle estensioni di Office per .NET Framework 3.5. Per la documentazione sugli spazi dei nomi e classi in questi assembly, vedere la sezione di riferimento seguente nella documentazione di Visual Studio 2008: [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Nome assembly|Descrizione|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Fornisce i seguenti tipi:<br /><br /> -La classe di base Microsoft.Office.Tools.AddIn per componenti aggiuntivi VSTO.<br />-Le classi per la creazione di personalizzazioni della barra multifunzione e smart tag. **Nota:**      Gli smart tag sono deprecati in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Le classi per la creazione di riquadri azioni nelle personalizzazioni a livello di documento e riquadri attività personalizzati nei componenti aggiuntivi VSTO.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Fornisce gli elementi host e i controlli host per le soluzioni Excel. Per altre informazioni, vedere [automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Fornisce classi che è possibile usare per creare arre del modulo personalizzate in componenti aggiuntivi VSTO di Outlook.|  
|Microsoft.Office.Tools.Word.v9.0.dll|Fornisce gli elementi host e i controlli host per le soluzioni Word. Per altre informazioni, vedere [automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v9.0.dll|Fornisce i seguenti tipi:<br /><br /> -il [RemoteBindableComponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) (classe), che fornisce la funzionalità di data binding per le personalizzazioni a livello di documento i controlli host in.<br />-Altri tipi che fanno parte di Visual Studio Tools per l'infrastruttura di runtime di Office e non deve essere usato direttamente dal codice.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Fornisce i seguenti tipi:<br /><br /> -il <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo e <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaccia, che è possibile usare per memorizzare gli oggetti dati in una personalizzazione a livello di documento. Per altre informazioni, vedere [memorizzare nella Cache dati](../vsto/caching-data.md).<br />-Le eccezioni che possono essere generate da Visual Studio Tools per Office runtime.<br />-Altri tipi che fanno parte di Visual Studio Tools per l'infrastruttura di runtime di Office e non deve essere usato direttamente dal codice.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Fornisce l'interfaccia <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>, che è possibile implementare per eseguire ulteriori passaggi di installazione, come il passaggio finale del programma di installazione ClickOnce per una soluzione Office. Per altre informazioni, vedere [distribuzione di soluzioni Office Advanced](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Fornisce i seguenti tipi:<br /><br /> -La <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> (classe), che è possibile usare a livello di programmazione collegare gli assembly di personalizzazione ai documenti e accedere ai dati memorizzati nella cache nei documenti. Per altre informazioni, vedere [gestire documenti in un server usando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Diverse classi che rappresentano la gerarchia dei dati in una personalizzazione a livello di documento memorizzati nella cache. Per altre informazioni, vedere [accedere ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Fornisce i seguenti tipi:<br /><br /> -Le classi AddInSecurityEntry e Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList, che è possibile usare per creare le voci dell'elenco per concedere l'attendibilità a Office inclusione dell'utente soluzioni destinate a .NET Framework 3.5.<br />-Altri tipi che fanno parte di Visual Studio Tools per l'infrastruttura di runtime di Office e non deve essere usato direttamente dal codice.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Tools per Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Visual Studio Tools per scenari di installazione di Office runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  