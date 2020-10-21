---
title: Gestire i documenti in un server usando la classe ServerDocument
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e91653734b804693584808478e44443563cdb823
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2020
ms.locfileid: "92298279"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Gestire i documenti in un server usando la classe ServerDocument
  È possibile utilizzare la `ServerDocument` classe in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] per gestire diversi aspetti delle personalizzazioni a livello di documento, anche se Microsoft Office Word e Microsoft Office Excel non sono installati. È possibile eseguire le seguenti attività:

- Accedere e modificare i dati nella cache dei dati di un documento o di una cartella di lavoro. Per ulteriori informazioni, vedere la pagina relativa all' [utilizzo dei dati memorizzati nella cache nel documento](#CachedData).

- Gestire l'assembly di personalizzazione associato a un documento. Per altre informazioni, vedere [gestire la personalizzazione del documento](#CustomizationInfo).

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="understand-the-serverdocument-class"></a>Comprendere la classe ServerDocument
 La `ServerDocument` classe è progettata per essere usata in computer in cui non è installato Office. Pertanto, in genere si utilizza questa classe in applicazioni che non si integrano con Office, ad esempio progetti console o progetti Windows Forms, anziché progetti di Office. Utilizzare la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe nell'assembly *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* .

 La `ServerDocument` classe può essere utilizzata per operare sulle personalizzazioni a livello di documento create tramite [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .

 Per ulteriori informazioni su Visual Studio 2010 Tools per Office Runtime e le estensioni di Office per la .NET Framework, vedere la pagina relativa alla [Panoramica di strumenti di Visual Studio per Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

> [!NOTE]
> Se si dispone di un'applicazione legacy che usa la `ServerDocument` classe nel `Visual Studio Tools for Office` sistema (versione 3,0 Runtime), il `Visual Studio Tools for Office` sistema (versione 3,0 Runtime) deve essere installato nei computer che eseguono l'applicazione. `Visual Studio 2010 Tools for Office runtime`Non è in grado di eseguire queste applicazioni.

## <a name="work-with-cached-data-in-the-document"></a><a name="CachedData"></a> Usare i dati memorizzati nella cache nel documento
 La `ServerDocument` classe fornisce i membri che è possibile usare per lavorare con la cache di dati in documenti personalizzati. Per altre informazioni sui dati memorizzati nella cache, vedere [memorizzare nella cache](../vsto/caching-data.md) i dati e [accedere ai dati nei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).

 La tabella seguente elenca i membri che è possibile usare per lavorare con i dati memorizzati nella cache.

|Attività|Membro da usare|
|----------|-------------------|
|Per determinare se un documento dispone di una cache di dati.|Metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> .|
|Per accedere ai dati memorizzati nella cache in un documento.<br /><br /> Per ulteriori informazioni, vedere [accedere ai dati nei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).|La proprietà <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|

## <a name="manage-the-document-customization"></a><a name="CustomizationInfo"></a> Gestire la personalizzazione del documento
 È possibile utilizzare i membri della `ServerDocument` classe per gestire l'assembly di personalizzazione associato a un documento. Ad esempio, è possibile rimuovere a livello di codice la personalizzazione da un documento in modo che il documento non faccia più parte di una personalizzazione.

 Nella tabella seguente sono elencati i membri che è possibile utilizzare per gestire l'assembly di personalizzazione.

|Attività|Membro da usare|
|----------|-------------------|
|Per determinare se un documento fa parte di una personalizzazione a livello di documento.|Metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> .|
|Per alleghi a livello di codice una personalizzazione a un documento in fase di esecuzione.<br /><br /> Per altre informazioni, vedere [procedura: aggiungere estensioni di codice gestito a documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Uno dei <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metodi.|
|Per rimuovere a livello di codice una personalizzazione da un documento in fase di esecuzione.<br /><br /> Per altre informazioni, vedere [procedura: rimuovere estensioni di codice gestito da documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> .|
|Per ottenere l'URL del manifesto di distribuzione associato al documento.|La proprietà <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|

## <a name="see-also"></a>Vedere anche
- [Procedura: associazione di estensioni di codice gestito a documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
- [Procedura: rimuovere estensioni di codice gestito da documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Panoramica di Strumenti di Visual Studio per Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Dati cache](../vsto/caching-data.md)
