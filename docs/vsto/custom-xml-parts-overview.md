---
title: Panoramica delle parti XML personalizzate
description: Informazioni su come incorporare dati XML nei documenti per alcune Microsoft Office applicazioni. Quando si incorporano i dati XML in un documento, i dati vengono denominati parti XML personalizzate.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: dfa45ffc37ffdbdabbb35d043b43e5005098d0d8b30554e110a724dfba5922fe
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394810"
---
# <a name="custom-xml-parts-overview"></a>Panoramica delle parti XML personalizzate
  È possibile incorporare i dati XML nei documenti per alcune applicazioni di Microsoft Office. Quando si incorporano dati XML in un documento, i dati vengono denominati parte *XML personalizzata*.

 È possibile creare e modificare le parti XML personalizzate in un documento usando un componente aggiuntivo VSTO o una soluzione a livello di documento in Visual Studio. Non è necessario avviare l'applicazione di Microsoft Office per creare e modificare le parti XML personalizzate.

 **Si applica a:** Le informazioni contenute in questo argomento si applicano ai progetti a livello di documento e VSTO di componenti aggiuntivi per Excel, PowerPoint e Word. Per altre informazioni, vedere [Funzionalità disponibili per l'applicazione Office tipo di progetto.](../vsto/features-available-by-office-application-and-project-type.md)

> [!NOTE]
> Visual Studio consente anche di memorizzare nella cache gli oggetti dati nelle personalizzazioni a livello di documento. Questa funzionalità è diversa dalle parti XML personalizzate, sebbene siano presenti alcune somiglianze. Per altre informazioni, vedere [Dati memorizzati nella cache nelle personalizzazioni a livello di documento.](../vsto/cached-data-in-document-level-customizations.md)

## <a name="understand-custom-xml-parts"></a>Informazioni su parti XML personalizzate
 Le parti XML personalizzate sono state introdotte nel sistema Microsoft Office 2007, insieme ai formati Open XML. Questi formati includono nuovi formati di file basati su XML per Excel, PowerPoint e Word (ad esempio *.xlsx*, *.pptx* e *.docx*). I documenti in questi formati sono costituiti da file XML ,denominati anche parti *XML,* organizzati in cartelle in un archivio ZIP. Per la maggior parte, si tratta di parti XML predefinite che consentono di definire la struttura e lo stato del documento. Tuttavia, i documenti possono contenere anche parti XML personalizzate, che è possibile usare per archiviare i dati XML arbitrari nei documenti.

 I formati di file XML consentono alle applicazioni di usare i documenti in modi non possibili con i formati di file binari precedenti, ad esempio *.xls*, *.ppt* e *.doc*. Tutte le applicazioni in grado di leggere gli archivi ZIP possono esaminare e modificare i contenuti dei documenti, anche se Microsoft Office non è installato.

 Per altre informazioni sulla struttura di Open XML e delle parti XML personalizzate, vedere i seguenti articoli:

- [Introduzione ai formati di file Office (2007) Open XML](/previous-versions/office/developer/office-2007/aa338205(v=office.12))

- [Procedura: Modificare documenti in formati Open XML](/previous-versions/office/developer/office-2007/aa982683(v=office.12))

- [Procedura dettagliata: formato XML di Word 2007](/previous-versions/office/developer/office-2007/bb266220(v=office.12))

- [Creare documenti di Word 2007 usando formati Open XML](/previous-versions/office/developer/office-2007/bb264572(v=office.12))

> [!NOTE]
> Excel, Word e PowerPoint consentono anche di usare parti XML personalizzate nei documenti salvati in formati di file binari. Tuttavia, se un documento viene salvato in un formato binario, non è possibile aggiungere o modificare le parti XML personalizzate senza avviare l'applicazione di Microsoft Office.

## <a name="create-and-modify-custom-xml-parts"></a>Creare e modificare parti XML personalizzate
 È possibile creare o modificare le parti XML personalizzate quando il documento è aperto nell'applicazione di Office oppure quando il documento è chiuso, anche se Microsoft Office non è installato.

### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Modificare parti XML mentre l'Office è in esecuzione
 È possibile utilizzare parti XML personalizzate usando una personalizzazione a livello di documento o un VSTO componente aggiuntivo. Se si una personalizzazione a livello di documento, vengono usate in genere le parti XML personalizzate nel documento personalizzato. Se si utilizza un componente VSTO, è possibile creare o modificare parti XML personalizzate in qualsiasi documento aperto nell'applicazione.

 Per creare una parte XML personalizzata usando Visual Studio, aggiungere un nuovo <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Core.CustomXMLParts> nel documento. Per altre informazioni, vedere i seguenti argomenti:

- [Procedura: Aggiungere parti XML personalizzate alle personalizzazioni a livello di documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)

- [Procedura: Aggiungere parti XML personalizzate ai documenti usando VSTO componenti aggiuntivi](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)

### <a name="modify-xml-parts-without-starting-the-office-application"></a>Modificare parti XML senza avviare l Office app Office dati
 È possibile aggiungere o modificare una parte XML personalizzata senza avviare Excel, PowerPoint o Word. Questa funzione è utile per usare i dati XML di un documento in un computer in cui sono installate le applicazioni di Microsoft Office, ad esempio un server.

 Per aggiungere una parte XML personalizzata senza avviare Microsoft Office, usare le classi in Open XML SDK. Queste classi sono progettate per fornire l'accesso ai contenuti Open XML specifici dei documenti di Office. Ad esempio, per aggiungere una parte XML personalizzata a una Excel di lavoro di , usare il <xref:DocumentFormat.OpenXml.Packaging.OpenXmlPartContainer.AddNewPart%2A> metodo di un oggetto <xref:DocumentFormat.OpenXml.Packaging.WorkbookPart> . Per altre informazioni, vedere [Open XML SDK.](/office/open-xml/open-xml-sdk)

## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Associare parti XML personalizzate ai controlli contenuto di Word
 È possibile associare i controlli contenuto in una soluzione Word agli elementi in una parte XML personalizzata. Quando un controllo contenuto è associato a una parte XML personalizzata, i dati nella parte XML personalizzata vengono visualizzati nell'interfaccia utente del controllo contenuto. Se un utente modifica testo nel controllo, l'elemento XML corrispondente viene automaticamente aggiornato. Analogamente, se si modificano i valori degli elementi nelle parti XML personalizzate, i controlli contenuto associati agli elementi XML visualizzeranno i nuovi dati. Per altre informazioni, vedere [Controlli contenuto.](../vsto/content-controls.md)

## <a name="see-also"></a>Vedi anche
- [Xml Schema e dati nelle personalizzazioni a livello di documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
- [Procedura: Aggiungere parti XML personalizzate alle personalizzazioni a livello di documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
- [Procedura: Aggiungere parti XML personalizzate ai documenti usando VSTO componenti aggiuntivi](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
- [Controlli contenuto](../vsto/content-controls.md)
- [Procedura dettagliata: Associare controlli contenuto a parti XML personalizzate](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)
