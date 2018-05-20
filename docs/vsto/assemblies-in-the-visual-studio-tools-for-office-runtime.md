---
title: Assembly in Visual Studio Tools per Office runtime
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8ff32d472d0e2005b22acb8d751e03c6aa3f61ef
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Assembly in Visual Studio Tools per Office runtime
  Quando si crea un progetto di Office, in Visual Studio vengono automaticamente aggiunti riferimenti agli assembly [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usati per il tipo di progetto e .NET Framework di destinazione del progetto. Sono disponibili diversi assembly nelle estensioni di Office per .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]e [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Per ulteriori informazioni sulle estensioni di Office, vedere [Visual Studio Tools per Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>Assembly nelle estensioni di Office per .NET Framework 4 e [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 Nella tabella seguente sono elencati gli assembly che vengono inclusi nelle estensioni di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Per la documentazione sugli spazi dei nomi e tipi di questi assembly, vedere [riferimenti gestiti &#40;sviluppo per Office in Visual Studio&#41;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Nome assembly|Descrizione|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|Fornisce i seguenti tipi:<br /><br /> -Tipi per la creazione di personalizzazioni della barra multifunzione e smart tag. **Nota:** Smart tag sono deprecati in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Tipi per la creazione di riquadri azioni nelle personalizzazioni a livello di documento e di riquadri attività personalizzati nei componenti aggiuntivi VSTO.|  
|Microsoft.Office.Tools.Excel.dll|Fornisce interfacce che rappresentano elementi host e controlli host per i progetti di Excel e tipi di supporto. Per altre informazioni, vedere [automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Fornisce tipi che è possibile usare per creare aree del modulo personalizzate in componenti aggiuntivi VSTO di Outlook.|  
|Microsoft.Office.Tools.Word.dll|Fornisce interfacce che rappresentano elementi host e controlli host per i progetti di Word e tipi di supporto. Per altre informazioni, vedere [automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Fornisce i seguenti tipi:<br /><br /> -Le eccezioni che possono essere generate da Visual Studio Tools per Office runtime.<br />-Aree del modulo attributi da utilizzare durante la creazione di Outlook.|  
|Microsoft.Office.Tools.dll|Fornisce i tipi che fanno parte dell'infrastruttura runtime di Visual Studio Tools per Office e che non è previsto vengano usati direttamente dal codice.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Fornisce i seguenti tipi:<br /><br /> -La <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo e <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaccia, è possibile utilizzare per memorizzare gli oggetti dati in una personalizzazione a livello di documento. Per altre informazioni, vedere [memorizzare nella Cache dati](../vsto/caching-data.md).<br />-La <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interfaccia, è possibile implementare per eseguire ulteriori passaggi di installazione come passaggio finale del programma di installazione ClickOnce per una soluzione Office. Per altre informazioni, vedere [distribuire una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-Le eccezioni che possono essere generate da Visual Studio Tools per Office runtime.<br />-Gli altri tipi che fanno parte di Visual Studio Tools per infrastruttura di runtime di Office e non deve essere utilizzato direttamente dal codice.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Fornisce i seguenti tipi:<br /><br /> -La <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> (classe), che è possibile utilizzare per collegare gli assembly di personalizzazione ai documenti e accedere ai dati memorizzati nella cache dei documenti. Per altre informazioni, vedere [gestire documenti in un server utilizzando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Diverse classi che rappresentano la gerarchia dei dati memorizzati nella cache una personalizzazione a livello di documento. Per altre informazioni, vedere [l'accesso ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 I progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] fanno riferimento agli assembly seguenti. Questi assembly non fanno parte del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ridistribuibile. Sono invece gli assembly dipendenti che devono essere distribuiti con la soluzione. Per impostazione predefinita, vengono copiati nella cartella di output di compilazione del progetto (la proprietà **Copia localmente** di questi assembly è impostata su **True**). Se si distribuisce il progetto tramite ClickOnce, questi assembly vengono inclusi nel pacchetto generato.  
  
|Nome assembly|Descrizione|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Fornisce le classi base per la classe `ThisAddIn` generata nei progetti di componente aggiuntivo VSTO e la classe Ribbon generata in tutti i progetti.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Fornisce i seguenti tipi:<br /><br /> -Classi di base generate `ThisWorkbook` e `Sheet` classi a livello di documento progetti per Excel.<br />-Windows Form che è possibile utilizzare nei fogli di lavoro nei progetti di Excel.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Fornisce le classi di base le classi `ThisAddIn` e le classi dell'area del modulo generate nei progetti di Outlook.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Fornisce i seguenti tipi:<br /><br /> -Classi di base generate `ThisDocument` classe nei progetti a livello di documento per Word.<br />-Windows Form che è possibile utilizzare nei documenti dei progetti di Word.|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Assembly nelle estensioni di Office per .NET Framework 3.5  
 Nella tabella seguente sono elencati gli assembly che vengono inclusi nelle estensioni di Office per .NET Framework 3.5. Per la documentazione sugli spazi dei nomi e le classi in questi assembly, vedere la sezione di riferimento seguente nella documentazione di Visual Studio 2008: [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Nome assembly|Descrizione|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Fornisce i seguenti tipi:<br /><br /> -Microsoft.Office.Tools.AddIn classe di base per i componenti aggiuntivi VSTO.<br />-Classi per la creazione di personalizzazioni della barra multifunzione e smart tag. **Nota:** Smart tag sono deprecati in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Classi per la creazione di riquadri azioni nelle personalizzazioni a livello di documento e di riquadri attività personalizzati nei componenti aggiuntivi VSTO.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Fornisce gli elementi host e i controlli host per le soluzioni Excel. Per altre informazioni, vedere [automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Fornisce classi che è possibile usare per creare arre del modulo personalizzate in componenti aggiuntivi VSTO di Outlook.|  
|Microsoft.Office.Tools.Word.v9.0.dll|Fornisce gli elementi host e i controlli host per le soluzioni Word. Per altre informazioni, vedere [automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v9.0.dll|Fornisce i seguenti tipi:<br /><br /> -La [RemoteBindableComponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) (classe), che fornisce le funzionalità di associazione dati per le personalizzazioni a livello di documento i controlli host nelle.<br />-Gli altri tipi che fanno parte di Visual Studio Tools per infrastruttura di runtime di Office e non deve essere utilizzato direttamente dal codice.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Fornisce i seguenti tipi:<br /><br /> -La <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo e <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaccia, è possibile utilizzare per memorizzare gli oggetti dati in una personalizzazione a livello di documento. Per altre informazioni, vedere [memorizzare nella Cache dati](../vsto/caching-data.md).<br />-Le eccezioni che possono essere generate da Visual Studio Tools per Office runtime.<br />-Gli altri tipi che fanno parte di Visual Studio Tools per infrastruttura di runtime di Office e non deve essere utilizzato direttamente dal codice.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Fornisce l’interfaccia <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>, che è possibile implementare per eseguire ulteriori passaggi di installazione, come il passaggio finale del programma di installazione ClickOnce per una soluzione Office. Per altre informazioni, vedere [distribuzione di soluzioni Office avanzate](http://msdn.microsoft.com/en-us/9147b6f6-849f-4cb1-b2c5-e22658d74b02).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Fornisce i seguenti tipi:<br /><br /> -La <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> (classe), che è possibile utilizzare a livello di codice per collegare gli assembly di personalizzazione ai documenti e accedere ai dati memorizzati nella cache nei documenti. Per altre informazioni, vedere [gestire documenti in un server utilizzando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Diverse classi che rappresentano la gerarchia dei dati memorizzati nella cache una personalizzazione a livello di documento. Per altre informazioni, vedere [l'accesso ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Fornisce i seguenti tipi:<br /><br /> -Le classi AddInSecurityEntry e Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList, che è possibile utilizzare per creare le voci dell'elenco per concedere l'attendibilità a Office di inclusione dell'utente nelle soluzioni destinate a .NET Framework 3.5.<br />-Gli altri tipi che fanno parte di Visual Studio Tools per infrastruttura di runtime di Office e non deve essere utilizzato direttamente dal codice.|  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Tools per Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Visual Studio Tools per scenari di installazione di Office runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  