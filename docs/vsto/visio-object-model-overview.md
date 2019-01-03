---
title: Panoramica del modello a oggetti Visio
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 040144b1e18e216ef8ceadbd218cd42ccf7c40f1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848467"
---
# <a name="visio-object-model-overview"></a>Panoramica del modello a oggetti Visio
  Per sviluppare soluzioni Office per Microsoft Office Visio è possibile interagire con il modello a oggetti di Visio. Questo modello a oggetti è costituito da classi e interfacce fornite nell'assembly di interoperabilità primario per Visio ed è definito nello spazio dei nomi `Microsoft.Office.Interop.Visio`.  
  
 Questo argomento contiene una breve panoramica del modello a oggetti di Visio. Per informazioni sull'uso del modello a oggetti di Visio per eseguire attività nei progetti di Office, vedere gli argomenti seguenti:  
  
-   [Lavorare con i documenti di Visio](../vsto/working-with-visio-documents.md)  
  
-   [Lavorare con le forme di Visio](../vsto/working-with-visio-shapes.md)  
  
## <a name="understand-the-visio-object-model"></a>Comprendere il modello a oggetti Visio  
 In Visio sono disponibili numerosi oggetti con cui è possibile interagire. Questi oggetti sono organizzati in una gerarchia che corrisponde strettamente all'interfaccia utente. Il vertice della gerarchia è occupato dall'oggetto [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application) . Questo oggetto rappresenta l'istanza corrente di Visio. Il `Microsoft.Office.Interop.Visio.Application` oggetto contiene il `Microsoft.Office.Interop.Visio.Document` e `Microsoft.Office.Interop.Visio.Page` oggetti, nonché `Microsoft.Office.Interop.Visio.Documents` e `Microsoft.Office.Interop.Visio.Pages` raccolte. È possibile modificare e usare ogni oggetto e raccolta con i numerosi metodi e le varie proprietà di cui dispone.  
  
 Per altre informazioni, vedere la documentazione di riferimento di VBA sugli oggetti [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application), [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document)e [Microsoft.Office.Interop.Visio.Page](/office/vba/api/Visio.Page) nonché sulle raccolte [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) e [Microsoft.Office.Interop.Visio.Pages](/office/vba/api/Visio.Pages) .  
  
 Le sezioni riportate di seguito forniscono una breve descrizione degli oggetti di livello superiore e della loro reciproca interazione. Tali oggetti comprendono quelli elencati di seguito:  
  
-   Oggetto Application  
  
-   Oggetto Document  
  
-   Oggetto Page  
  
### <a name="application-object"></a>Oggetto Application  
 L'oggetto Interop rappresenta l'applicazione Visio ed è l'elemento padre di tutti gli altri oggetti. I membri di tale oggetto in genere vengono applicati a Visio nel suo complesso. È possibile usare le proprietà e metodi di Interop e `Microsoft.Office.Interop.Visio.ApplicationSettings` oggetti per controllare l'ambiente di Visio.  
  
 Nei progetti di componente aggiuntivo VSTO, è possibile accedere all'oggetto Interop usando il `Application` campo il `ThisAddIn` classe. Per altre informazioni, vedere [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
### <a name="document-object"></a>Oggetto Document  
 L'oggetto di Microsoft è centrale della programmazione di Visio. Rappresenta un disegno, uno stencil o un file modello. Quando si apre un documento di Visio o creare un nuovo documento, si crea un nuovo oggetto di Microsoft, che viene aggiunto alla raccolta Documents dell'oggetto Interop .  
  
 Il documento con lo stato attivo è definito documento attivo. È rappresentato dal `Microsoft.Office.Interop.Visio.Application.ActiveDocument` proprietà dell'oggetto Interop.  
  
### <a name="page-object"></a>Oggetto Page  
 L'oggetto Microsoft.Office.Interop.Visio.Page rappresenta l'area di disegno di una pagina di primo piano o in background. Per determinare se una pagina è di primo piano o di sfondo è possibile usare la proprietà `Microsoft.Office.Interop.Visio.Page.Background`.  
  
 Per creare forme, è possibile usare metodi che includono i metodi `Microsoft.Office.Interop.Visio.Page.DrawSpline` e `Microsoft.Office.Interop.Visio.Page.DrawOval`. Con il metodo `Microsoft.Office.Interop.Visio.Page.Drop` o `Microsoft.Office.Interop.Visio.Page.DropMany` è anche possibile recuperare master dagli stencil e posizionare le forme in una pagina.  
  
## <a name="use-the-visio-object-model-documentation"></a>Usare la documentazione del modello a oggetti Visio  
 Per informazioni complete sul modello a oggetti di Visio, vedere la documentazione di riferimento del modello a oggetti di VBA. Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di Visio esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere [riferimento del modello a oggetti Visio 2010](http://go.microsoft.com/fwlink/?LinkId=199775).  
  
 Tutti gli oggetti e i membri nel riferimento del modello a oggetti di VBA corrispondono a tipi e membri nell'assembly di interoperabilità primario (PIA) di Visio. Ad esempio, il `Document` oggetto nel riferimento del modello a oggetti VBA corrisponde al tipo di Microsoft nell'assembly di interoperabilità primario di Visio. Nonostante il riferimento del modello a oggetti di VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA in questo riferimento a Visual Basic o a Visual C# per usarli in un progetto di componente aggiuntivo VSTO di Visio creato con Visual Studio.  
  
> [!NOTE]  
>  Attualmente non è prevista la documentazione di riferimento per l'assembly di interoperabilità primario di Visio.  
  
 Per esempi di codice correlati e strumenti aggiuntivi per la creazione di soluzioni di Visio, vedere [Visio 2010 software development kit di](http://go.microsoft.com/fwlink/?LinkId=196501).  
  
### <a name="additional-types-in-primary-interop-assemblies"></a>Tipi aggiuntivi negli assembly di interoperabilità primari  
 È possibile cercare negli assembly di interoperabilità primari tipi che non sono visibili a VBA a causa delle differenze di implementazione. VBA offre una visualizzazione del modello a oggetti di Visio che include solo gli oggetti e i membri che è possibile usare direttamente. Gli assembly di interoperabilità primari espongono lo stesso modello a oggetti, ma includono anche le altre interfacce, classi e membri che traducono gli oggetti del modello a oggetti COM nel codice gestito. Questi elementi aggiuntivi non devono essere usati direttamente nel codice.  
  
 Per altre informazioni, vedere [Panoramica di classi e interfacce negli assembly di interoperabilità primari di Office](http://go.microsoft.com/fwlink/?LinkId=189592) e [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Lavorare con i documenti di Visio](../vsto/working-with-visio-documents.md)   
 [Lavorare con le forme di Visio](../vsto/working-with-visio-shapes.md)  
