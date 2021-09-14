---
title: 'Procedura: Creare una pagina applicazione | Microsoft Docs'
description: Creare una ASP.NET web di distribuzione (nota anche come pagina dell'applicazione) in Visual Studio per uno o più SharePoint web.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 211bba75c6acee1a820a2b8b4adaefb508818a04
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711439"
---
# <a name="how-to-create-an-application-page"></a>Procedura: Creare una pagina dell'applicazione
  È possibile creare una pagina Web ASP.NET per uno o più siti di SharePoint. In SharePoint queste pagine sono denominate pagine dell'applicazione. A differenza di una pagina del sito, una pagina dell'applicazione contiene codice che viene eseguito dietro la pagina. Per altre informazioni, vedere [Creare pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

### <a name="to-create-an-application-page"></a>Per creare una pagina dell'applicazione

1. In Visual Studio aprire o creare un progetto SharePoint.

     Per altre informazioni, vedere Modelli [SharePoint progetto e di elemento di progetto.](../sharepoint/sharepoint-project-and-project-item-templates.md)

2. Scegliere il nodo di progetto in **Esplora soluzioni**.

3. Nella barra dei menu scegliere **Project**  >  **Aggiungi nuovo elemento**.

4. Nella finestra **di dialogo Aggiungi** nuovo elemento espandere il **SharePoint** e quindi scegliere l'elemento **2010.**

5. Nell'elenco dei modelli SharePoint scegliere **Pagina applicazione.**

6. Nella casella **Nome** specificare un nome per la pagina dell'applicazione e quindi scegliere il **pulsante** Aggiungi.

     Visual Studio aggiunge diverse cartelle e file al progetto. Per altre informazioni su questi file, vedere [Creare pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

     Nella visualizzazione **Origine** della finestra di progettazione di Visual Web Developer viene visualizzato ASP.NET file di pagina. È possibile progettare la pagina aggiungendo controlli dalla casella degli **strumenti** e inserendoli nei segnaposto del contenuto. Per altre informazioni, vedere [Visualizzazione origine, Progettazione pagine Web.](/previous-versions/aspnet/ms178154\(v\=vs.100\))

7. Se si desidera gestire gli eventi di controllo, aggiungere il codice al file di codice per la pagina applicazione.

     Il file di codice viene visualizzato se si espande il nodo per il file di pagine ASP.NET e ha estensione *cs* o *vb,* a seconda del linguaggio del progetto. Per un esempio end-to-end di come creare una pagina dell'applicazione, vedere Procedura dettagliata: Creare una SharePoint [pagina dell'applicazione](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).

## <a name="see-also"></a>Vedi anche
- [Creare pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Procedura dettagliata: Creare una pagina SharePoint'applicazione](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
