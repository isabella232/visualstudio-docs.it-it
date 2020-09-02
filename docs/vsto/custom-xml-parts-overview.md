---
title: Cenni preliminari sulle parti XML personalizzate
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b94deacad38f40d76b4c8485186bfd563808d912
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "64784420"
---
# <a name="custom-xml-parts-overview"></a>Cenni preliminari sulle parti XML personalizzate
  È possibile incorporare i dati XML nei documenti per alcune applicazioni di Microsoft Office. Quando si incorporano dati XML in un documento, i dati vengono denominati come una *parte XML personalizzata*.

 È possibile creare e modificare le parti XML personalizzate in un documento usando un componente aggiuntivo VSTO o una soluzione a livello di documento in Visual Studio. Non è necessario avviare l'applicazione di Microsoft Office per creare e modificare le parti XML personalizzate.

 **Si applica a:** Le informazioni contenute in questo argomento sono valide per i progetti a livello di documento e di componente aggiuntivo VSTO per Excel, PowerPoint e Word. Per ulteriori informazioni, vedere [funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Visual Studio consente anche di memorizzare nella cache gli oggetti dati nelle personalizzazioni a livello di documento. Questa funzionalità è diversa dalle parti XML personalizzate, sebbene siano presenti alcune somiglianze. Per ulteriori informazioni, vedere la pagina relativa ai [dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md).

## <a name="understand-custom-xml-parts"></a>Informazioni sulle parti XML personalizzate
 Le parti XML personalizzate sono state introdotte nel sistema Microsoft Office 2007, insieme ai formati Open XML. Questi formati includono nuovi formati di file basati su XML per Excel, PowerPoint e Word (ad esempio *xlsx*, *pptx*e *docx*). I documenti in questi formati sono costituiti da file XML, denominati anche *parti XML*, organizzati in cartelle in un archivio zip. Per la maggior parte, si tratta di parti XML predefinite che consentono di definire la struttura e lo stato del documento. Tuttavia, i documenti possono contenere anche parti XML personalizzate, che è possibile usare per archiviare i dati XML arbitrari nei documenti.

 I formati di file XML consentono alle applicazioni di utilizzare i documenti in modi non possibili con i formati di file binari precedenti, ad esempio *xls*, *PPT*e *doc*. Tutte le applicazioni in grado di leggere gli archivi ZIP possono esaminare e modificare i contenuti dei documenti, anche se Microsoft Office non è installato.

 Per altre informazioni sulla struttura di Open XML e delle parti XML personalizzate, vedere i seguenti articoli:

- [Introduzione ai formati di file Open XML di Office (2007)](/previous-versions/office/developer/office-2007/aa338205(v=office.12))

- [Procedura: modificare documenti in formato XML aperto](/previous-versions/office/developer/office-2007/aa982683(v=office.12))

- [Procedura dettagliata: formato XML di Word 2007](/previous-versions/office/developer/office-2007/bb266220(v=office.12))

- [Compilare documenti Word 2007 usando formati Open XML](/previous-versions/office/developer/office-2007/bb264572(v=office.12))

> [!NOTE]
> Excel, Word e PowerPoint consentono anche di usare parti XML personalizzate nei documenti salvati in formati di file binari. Tuttavia, se un documento viene salvato in un formato binario, non è possibile aggiungere o modificare le parti XML personalizzate senza avviare l'applicazione di Microsoft Office.

## <a name="create-and-modify-custom-xml-parts"></a>Creazione e modifica di parti XML personalizzate
 È possibile creare o modificare le parti XML personalizzate quando il documento è aperto nell'applicazione di Office oppure quando il documento è chiuso, anche se Microsoft Office non è installato.

### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Modificare le parti XML mentre è in esecuzione l'applicazione di Office
 È possibile utilizzare le parti XML personalizzate utilizzando una personalizzazione a livello di documento o un componente aggiuntivo VSTO. Se si una personalizzazione a livello di documento, vengono usate in genere le parti XML personalizzate nel documento personalizzato. Se si usa un componente aggiuntivo VSTO, è possibile creare o modificare le parti XML personalizzate in qualsiasi documento aperto nell'applicazione.

 Per creare una parte XML personalizzata usando Visual Studio, aggiungere un nuovo <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Core.CustomXMLParts> nel documento. Per altre informazioni, vedere gli argomenti seguenti:

- [Procedura: aggiungere parti XML personalizzate a personalizzazioni a livello di documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)

- [Procedura: aggiungere parti XML personalizzate ai documenti usando i componenti aggiuntivi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)

### <a name="modify-xml-parts-without-starting-the-office-application"></a>Modificare le parti XML senza avviare l'applicazione di Office
 È possibile aggiungere o modificare una parte XML personalizzata senza avviare Excel, PowerPoint o Word. Questa funzione è utile per usare i dati XML di un documento in un computer in cui sono installate le applicazioni di Microsoft Office, ad esempio un server.

 Per aggiungere una parte XML personalizzata senza avviare Microsoft Office, usare le classi in Open XML SDK. Queste classi sono progettate per fornire l'accesso ai contenuti Open XML specifici dei documenti di Office. Ad esempio, per aggiungere una parte XML personalizzata a una cartella di lavoro di Excel, è necessario utilizzare il <xref:DocumentFormat.OpenXml.Packaging.OpenXmlPartContainer.AddNewPart%2A> metodo di un <xref:DocumentFormat.OpenXml.Packaging.WorkbookPart> oggetto. Per altre informazioni, vedere [Open XML SDK](/office/open-xml/open-xml-sdk).

## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Associare le parti XML personalizzate ai controlli contenuto di Word
 È possibile associare i controlli contenuto in una soluzione Word agli elementi in una parte XML personalizzata. Quando un controllo contenuto è associato a una parte XML personalizzata, i dati nella parte XML personalizzata vengono visualizzati nell'interfaccia utente del controllo contenuto. Se un utente modifica testo nel controllo, l'elemento XML corrispondente viene automaticamente aggiornato. Analogamente, se si modificano i valori degli elementi nelle parti XML personalizzate, i controlli contenuto associati agli elementi XML visualizzeranno i nuovi dati. Per altre informazioni, vedere [controlli contenuto](../vsto/content-controls.md).

## <a name="see-also"></a>Vedere anche
- [XML Schema e dati nelle personalizzazioni a livello di documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
- [Procedura: aggiungere parti XML personalizzate a personalizzazioni a livello di documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
- [Procedura: aggiungere parti XML personalizzate ai documenti usando i componenti aggiuntivi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
- [Controlli contenuto](../vsto/content-controls.md)
- [Procedura dettagliata: associare controlli contenuto a parti XML personalizzate](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)
