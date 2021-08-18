---
title: Gestire documenti in un server usando la classe ServerDocument
description: Informazioni su come usare la classe ServerDocument nel runtime Visual Studio Tools per Office per gestire diversi aspetti delle personalizzazioni a livello di documento.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 6f07c19f96ef7151a8c08464388e011b371a8827
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032485"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Gestire documenti in un server usando la classe ServerDocument
  È possibile usare la classe in per gestire diversi aspetti delle personalizzazioni a livello di documento, anche se Microsoft Office `ServerDocument` Word e Microsoft Office Excel non sono [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] installati. È possibile eseguire le seguenti attività:

- Accedere ai dati e modificarli nella cache dei dati di un documento o di una cartella di lavoro. Per altre informazioni, vedere [Usare i dati memorizzati nella cache nel documento](#CachedData).

- Gestire l'assembly di personalizzazione associato a un documento. Per altre informazioni, vedere [Gestire la personalizzazione del documento.](#CustomizationInfo)

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="understand-the-serverdocument-class"></a>Informazioni sulla classe ServerDocument
 La classe è progettata per essere usata nei computer in cui non Office `ServerDocument` installati. Di conseguenza, questa classe viene in genere utilizzata nelle applicazioni che non si integrano con Office, ad esempio progetti Console o Windows Forms, anziché Office progetti. Usare la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe nell'assembly *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.*

 La `ServerDocument` classe può essere utilizzata per operare sulle personalizzazioni a livello di documento create tramite [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .

 Per altre informazioni sulle estensioni Visual Studio 2010 Tools for Office Runtime e sulle estensioni Office per .NET Framework, vedere Visual Studio Tools per Office [runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).

> [!NOTE]
> Se si dispone di un'applicazione legacy che usa la classe nel sistema `ServerDocument` `Visual Studio Tools for Office` (versione 3.0 Runtime), il sistema (versione 3.0 runtime) deve essere installato nei computer che eseguono `Visual Studio Tools for Office` l'applicazione. Non `Visual Studio 2010 Tools for Office runtime` è possibile eseguire queste applicazioni.

## <a name="work-with-cached-data-in-the-document"></a><a name="CachedData"></a> Usare i dati memorizzati nella cache nel documento
 La `ServerDocument` classe fornisce membri che è possibile usare per usare la cache dei dati nei documenti personalizzati. Per altre informazioni sui dati memorizzati nella cache, vedere [Memorizzare](../vsto/caching-data.md) nella cache i dati e [Accedere ai dati nei documenti nel server](../vsto/accessing-data-in-documents-on-the-server.md).

 Nella tabella seguente sono elencati i membri che è possibile usare per usare i dati memorizzati nella cache.

|Attività|Membro da usare|
|----------|-------------------|
|Per determinare se un documento dispone di una cache dei dati.|Metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> .|
|Per accedere ai dati memorizzati nella cache in un documento.<br /><br /> Per altre informazioni, vedere [Accedere ai dati nei documenti nel server](../vsto/accessing-data-in-documents-on-the-server.md).|La proprietà <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|

## <a name="manage-the-document-customization"></a><a name="CustomizationInfo"></a> Gestire la personalizzazione del documento
 È possibile usare i membri della `ServerDocument` classe per gestire l'assembly di personalizzazione associato a un documento. Ad esempio, è possibile rimuovere a livello di codice la personalizzazione da un documento in modo che il documento non sia più parte di una personalizzazione.

 Nella tabella seguente sono elencati i membri che è possibile usare per gestire l'assembly di personalizzazione.

|Attività|Membro da usare|
|----------|-------------------|
|Per determinare se un documento fa parte di una personalizzazione a livello di documento.|Metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> .|
|Per associare a livello di codice una personalizzazione a un documento in fase di esecuzione.<br /><br /> Per altre informazioni, vedere [Procedura: Collegare estensioni di codice gestito ai documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Uno dei <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metodi .|
|Per rimuovere a livello di codice una personalizzazione da un documento in fase di esecuzione.<br /><br /> Per altre informazioni, vedere [Procedura: Rimuovere estensioni di codice gestito dai documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> .|
|Per ottenere l'URL del manifesto di distribuzione associato al documento.|La proprietà <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|

## <a name="see-also"></a>Vedi anche
- [Procedura: Collegare estensioni di codice gestito ai documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
- [Procedura: Rimuovere estensioni di codice gestito dai documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Visual Studio Tools per Office di runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Dati cache](../vsto/caching-data.md)
