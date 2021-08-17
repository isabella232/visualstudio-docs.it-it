---
title: Modifiche di progettazione ai Office di destinazione .NET Framework
description: Informazioni sulle modifiche introdotte in Visual Studio alla progettazione di Office che hanno come destinazione .NET Framework 4 o versioni successive.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio 2010, what's new
- what's new [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: fc2fcd7c48ab90432839642b02d1b147db48c31041353b6c4c4df425a3c150c1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352273"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Modifiche alla progettazione di Office progetti che hanno come destinazione .NET Framework 4 o .NET Framework 4.5
  A partire da [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], Visual Studio ha introdotto alcune modifiche nella creazione di progetti di Office destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva. Se si ha familiarità con i progetti di Office delle versioni precedenti di Visual Studio, è necessario tenere presenti queste modifiche prima di sviluppare progetti di Office destinati a tali versioni di .NET Framework 4.0 o versione successiva. Per impostazione predefinita, tutti i progetti creati con Visual Studio 2013 o versione successiva sono destinati a .NET Framework 4.0 o versione successiva.

 Nelle sezioni seguenti vengono descritte le modifiche apportate alla creazione di progetti di Office.

## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Comprendere la progettazione basata sull'interfaccia degli strumenti Visual Studio 2010 per Office runtime
 Quando si sviluppa un progetto Office destinato a o versioni successive, la maggior parte dei tipi che si usano [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] in Visual Studio 2010 Tools for Office Runtime sono interfacce. Si tratta di una modifica importante rispetto alle versioni precedenti di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], in cui questi tipi sono classi. Ad esempio, quando si usa [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, i tipi <xref:Microsoft.Office.Tools.Excel.Worksheet> e <xref:Microsoft.Office.Tools.Word.Document> sono interfacce anziché classi. Per altre informazioni, vedere panoramica [Visual Studio Tools per Office runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

 Per i tipi di cui è possibile creare un'istanza direttamente nelle versioni precedenti di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], è ora possibile usare i metodi dell'oggetto `Globals.Factory` per ottenere le istanze di questi tipi. Ad esempio, per ottenere un oggetto che implementa l'interfaccia <xref:Microsoft.Office.Tools.Excel.SmartTag>, usare il metodo `Globals.Factory.CreateSmartTag`. Per altre informazioni, vedere i seguenti argomenti:

- [Aggiornare Excel e i progetti word di cui si esegue la migrazione al .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Aggiornare le personalizzazioni della barra multifunzione Office progetti di cui si esegue la migrazione al .NET Framework 4 o .NET Framework 4.5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Aggiornare le aree del modulo Outlook progetti di cui si esegue la migrazione al .NET Framework 4 o .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

### <a name="new-base-classes-in-office-projects"></a>Nuove classi di base nei Office progetto
 La nuova progettazione basata su interfaccia di Visual Studio 2010 Tools for Office runtime influisce sulle classi generate nei progetti Office, ad esempio `ThisDocument` , `ThisWorkbook` e `ThisAddIn` . Nei progetti di Office destinati a .NET Framework 3.5 e versioni precedenti del framework, queste classi generate derivano dalle classi in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] come `Microsoft.Office.Tools.Word.Document`, `Microsoft.Office.Tools.Excel.Worksheet` e `Microsoft.Office.Tools.AddIn`. Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva, queste classi [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sono interfacce. Pertanto, l'implementazione delle classi generate nei progetti di Office non può più derivare da tali classi. Al contrario, le classi generate derivano dalle nuove classi di base come <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase>e <xref:Microsoft.Office.Tools.AddInBase>. Per altre informazioni, vedere [Programma VSTO componenti aggiuntivi e](../vsto/programming-vsto-add-ins.md) [Personalizzazioni a livello di documento del programma](../vsto/programming-document-level-customizations.md).

 Le classi di base non fanno parte del componente ridistribuibile [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Al contrario, vengono definite negli assembly delle utilità inclusi in Visual Studio. Questi assembly vengono copiati nella cartella di output quando si compilano progetti di Office ed è necessario distribuirli con la soluzione. Per altre informazioni sugli assembly di utilità, vedere [Assembly nel runtime Visual Studio Tools per Office.](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)

## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>Modifiche di rilievo Office progetti che vengono ridestinati al .NET Framework 4
 Nella tabella seguente sono elencate le modifiche principali che è possibile riscontrare nei progetti di Office ridestinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva. Per altre informazioni, vedere [Eseguire la migrazione Office soluzioni .NET Framework 4 o versioni successive.](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)

|Modifica|Conseguenza|
|---------------------|-----------------|
|L'attributo <xref:System.Security.SecurityTransparentAttribute> non è più usato o supportato nei progetti di Office.|È necessario rimuovere questo attributo dal file di codice AssemblyInfo nei progetti di Office di cui si esegue l'aggiornamento da Visual Studio 2008. Per altre informazioni, vedere Modifiche necessarie per eseguire Office di cui si esegue la migrazione al .NET Framework 4 o [.NET Framework 4.5.](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)|
|**ExcelLocale1033Attribute** non viene più usato o supportato nei Excel progetto.|È necessario rimuovere questo attributo dal file *di codice AssemblyInfo* nei Excel progetto. Per altre informazioni, vedere Aggiornare Excel e i progetti word di cui si esegue la migrazione al .NET Framework 4 o [.NET Framework 4.5.](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)|
|Il modello di programmazione degli elementi di progetto di **Barra multifunzione (finestra di progettazione visiva)** è stato modificato.|È necessario modificare il file code-behind per tutti gli elementi della barra multifunzione nel progetto. È inoltre necessario modificare qualsiasi codice che crea un'istanza dei controlli della barra multifunzione in fase di esecuzione, gestisce gli eventi della barra multifunzione o imposta la posizione di un componente della barra multifunzione a livello di codice. Per altre informazioni, vedere Aggiornare le personalizzazioni della barra multifunzione nei progetti Office di cui si esegue la migrazione al .NET Framework 4 o [.NET Framework 4.5.](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)|
|Il modello di programmazione delle aree del modulo di Outlook è stato modificato.|È necessario modificare il file code-behind per le aree del modulo nel progetto e qualsiasi codice che crea un'istanza di determinate classi di aree del modulo in fase di esecuzione. Per altre informazioni, vedere [Update form regions in Outlook projects that you migrate to the .NET Framework 4 or the .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Il modello di programmazione per smart tag nei progetti di Excel e Word è stato modificato. Gli smart tag sono deprecati in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Se la soluzione usa smart tag, si verificheranno degli errori quando si compila il progetto. Poiché gli smart tag sono deprecati in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)], è necessario rimuovere i tag prima di eseguire il test e il debug della soluzione in [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] o versione successiva.|
|La sintassi dei metodi `GetVstoObject` e `HasVstoObject` è stata modificata|È necessario passare l'oggetto `Globals.Factory` a questi metodi quando vi si accede sugli oggetti nativi dagli assembly di interoperabilità primari (PIA). In alternativa, è possibile accedere a questi metodi sull'oggetto restituito dalla proprietà `Globals.Factory` nel progetto. Per altre informazioni, vedere Aggiornare Excel e i progetti word di cui si esegue la migrazione al .NET Framework 4 o [.NET Framework 4.5.](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)|
|Gli eventi dei controlli contenuto di Word sono associati a nuovi delegati.|È necessario modificare qualsiasi codice che gestisce gli eventi dei controlli contenuto di Word per specificare i nuovi delegati. Per altre informazioni, vedere Aggiornare Excel e i progetti word di cui si esegue la migrazione al .NET Framework 4 o [.NET Framework 4.5.](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)|
|Le classi `OLEObject` e `OLEControl` sono state rinominate.|È necessario modificare qualsiasi codice che usa le istanze di queste classi per usare gli oggetti <xref:Microsoft.Office.Tools.Excel.ControlSite> o <xref:Microsoft.Office.Tools.Word.ControlSite> . Per altre informazioni, vedere Aggiornare Excel e i progetti word di cui si esegue la migrazione al .NET Framework 4 o [.NET Framework 4.5.](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)|
|Le classi di elementi host, ad esempio , n , e , non forniscono più `ThisWorkbook` un metodo di cui è possibile eseguire `Sheet`  `ThisDocument` `ThisAddIn` `Dispose` l'override.|È necessario trasferire qualsiasi codice nell'override del metodo `Dispose` nel gestore eventi `Shutdown` nella classe degli elementi host, ad esempio `ThisAddIn_Shutdown`, e rimuovere l'override del metodo `Dispose` dalla classe degli elementi host.|

## <a name="see-also"></a>Vedi anche
- [Eseguire Office le soluzioni .NET Framework 4 o versioni successive](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Novità dello sviluppo Office](/previous-versions/86bkz018(v=vs.110))
- [Visual Studio Tools per Office di runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)