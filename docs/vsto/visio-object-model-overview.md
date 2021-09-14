---
title: Visio panoramica del modello a oggetti
description: Informazioni su come interagire con il modello Visio a oggetti per sviluppare Office soluzioni per Microsoft Visio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e2c82deca11d11d96afce5365b04b68247807789
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710599"
---
# <a name="visio-object-model-overview"></a>Visio panoramica del modello a oggetti
  Per sviluppare soluzioni Office per Microsoft Office Visio è possibile interagire con il modello a oggetti di Visio. Questo modello a oggetti è costituito da classi e interfacce fornite nell'assembly di interoperabilità primario per Visio ed è definito nello spazio dei nomi `Microsoft.Office.Interop.Visio`.

 Questo argomento contiene una breve panoramica del modello a oggetti di Visio. Per informazioni sull'uso del modello a oggetti di Visio per eseguire attività nei progetti di Office, vedere gli argomenti seguenti:

- [Usare documenti Visio](../vsto/working-with-visio-documents.md)

- [Usare le Visio personalizzate](../vsto/working-with-visio-shapes.md)

## <a name="understand-the-visio-object-model"></a>Informazioni sul modello Visio a oggetti
 In Visio sono disponibili numerosi oggetti con cui è possibile interagire. Questi oggetti sono organizzati in una gerarchia che corrisponde strettamente all'interfaccia utente. Il vertice della gerarchia è occupato dall'oggetto [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application) . Questo oggetto rappresenta l'istanza corrente di Visio. `Microsoft.Office.Interop.Visio.Application`L'oggetto contiene gli oggetti e , nonché le raccolte e `Microsoft.Office.Interop.Visio.Document` `Microsoft.Office.Interop.Visio.Page` `Microsoft.Office.Interop.Visio.Documents` `Microsoft.Office.Interop.Visio.Pages` . È possibile modificare e usare ogni oggetto e raccolta con i numerosi metodi e le varie proprietà di cui dispone.

 Per altre informazioni, vedere la documentazione di riferimento di VBA sugli oggetti [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application), [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document)e [Microsoft.Office.Interop.Visio.Page](/office/vba/api/Visio.Page) nonché sulle raccolte [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) e [Microsoft.Office.Interop.Visio.Pages](/office/vba/api/Visio.Pages) .

 Le sezioni riportate di seguito forniscono una breve descrizione degli oggetti di livello superiore e della loro reciproca interazione. Tali oggetti comprendono quelli elencati di seguito:

- Oggetto applicazione

- Oggetto Document

- Oggetto Page

### <a name="application-object"></a>Oggetto applicazione
 The Microsoft. Office. Interoperabilità. Visio. L'oggetto applicazione rappresenta Visio app applicazione ed è l'elemento padre di tutti gli altri oggetti. I membri di tale oggetto in genere vengono applicati a Visio nel suo complesso. È possibile usare le proprietà e i metodi di Microsoft. Office. Interoperabilità. Visio. Applicazione e oggetti `Microsoft.Office.Interop.Visio.ApplicationSettings` per controllare l'Visio ambiente.

 In VSTO di componenti aggiuntivi è possibile accedere a Microsoft. Office. Interoperabilità. Visio. Oggetto applicazione utilizzando il `Application` campo della `ThisAddIn` classe . Per altre informazioni, vedere [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).

### <a name="document-object"></a>Oggetto Document
 The Microsoft. Office. Interoperabilità. Visio. L'oggetto documento è fondamentale per la programmazione Visio. Rappresenta un disegno, uno stencil o un file modello. Quando si apre un Visio o si crea un nuovo documento, si crea un nuovo documento Microsoft. Office. Interoperabilità. Visio. Oggetto documento, aggiunto a Microsoft. Office. Interoperabilità. Visio. Raccolta di documenti di Microsoft. Office. Interoperabilità. Visio. Oggetto applicazione.

 Il documento con lo stato attivo è definito documento attivo. È rappresentato dalla proprietà `Microsoft.Office.Interop.Visio.Application.ActiveDocument` dell'oggetto Microsoft.Office. Interoperabilità. Visio. Oggetto applicazione.

### <a name="page-object"></a>Oggetto Page
 The Microsoft. Office. Interoperabilità. Visio. L'oggetto Page rappresenta l'area di disegno di una pagina in primo piano o di una pagina di sfondo. Per determinare se una pagina è di primo piano o di sfondo è possibile usare la proprietà `Microsoft.Office.Interop.Visio.Page.Background`.

 Per creare forme, è possibile usare metodi che includono i metodi `Microsoft.Office.Interop.Visio.Page.DrawSpline` e `Microsoft.Office.Interop.Visio.Page.DrawOval`. Con il metodo `Microsoft.Office.Interop.Visio.Page.Drop` o `Microsoft.Office.Interop.Visio.Page.DropMany` è anche possibile recuperare master dagli stencil e posizionare le forme in una pagina.

## <a name="use-the-visio-object-model-documentation"></a>Usare la documentazione Visio modello a oggetti
 Per informazioni complete sul modello a oggetti di Visio, vedere la documentazione di riferimento del modello a oggetti di VBA. Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di Visio esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere riferimento [Visio modello a oggetti](/office/vba/api/overview/visio/object-model).

 Tutti gli oggetti e i membri nel riferimento del modello a oggetti di VBA corrispondono a tipi e membri nell'assembly di interoperabilità primario (PIA) di Visio. Ad esempio, `Document` l'oggetto nel riferimento al modello a oggetti VBA corrisponde al file Microsoft.Office. Interoperabilità. Visio. Tipo di documento nell'Visio PIA. Nonostante il riferimento del modello a oggetti di VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA in questo riferimento a Visual Basic o a Visual C# per usarli in un progetto di componente aggiuntivo VSTO di Visio creato con Visual Studio.

> [!NOTE]
> Attualmente non è prevista la documentazione di riferimento per l'assembly di interoperabilità primario di Visio.

 Per esempi di codice correlati e strumenti aggiuntivi per la creazione Visio soluzioni, [vedere Visio Software Development Kit 2010.](https://www.microsoft.com/download/details.aspx?id=12365)

### <a name="additional-types-in-primary-interop-assemblies"></a>Tipi aggiuntivi negli assembly di interoperabilità primari
 È possibile cercare negli assembly di interoperabilità primari tipi che non sono visibili a VBA a causa delle differenze di implementazione. VBA offre una visualizzazione del modello a oggetti di Visio che include solo gli oggetti e i membri che è possibile usare direttamente. Gli assembly di interoperabilità primari espongono lo stesso modello a oggetti, ma includono anche le altre interfacce, classi e membri che traducono gli oggetti del modello a oggetti COM nel codice gestito. Questi elementi aggiuntivi non devono essere usati direttamente nel codice.

 Per altre informazioni, vedere [Panoramica di classi](/previous-versions/office/office-12/ms247299(v=office.12)) e interfacce nel Office assembly di interoperabilità primari e Office assembly di [interoperabilità primari.](../vsto/office-primary-interop-assemblies.md)

## <a name="see-also"></a>Vedi anche
- [Visio soluzioni](../vsto/visio-solutions.md)
- [Usare documenti Visio](../vsto/working-with-visio-documents.md)
- [Usare le Visio personalizzate](../vsto/working-with-visio-shapes.md)
