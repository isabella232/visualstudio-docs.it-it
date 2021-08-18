---
title: 'Procedura: Creare una web part SharePoint usando una finestra di progettazione | Microsoft Docs'
titleSuffix: ''
description: Creare una web part aggiungendo un elemento web part visivo a un progetto SharePoint, che apre la finestra di progettazione di Visual Web Developer in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 5f1c22bd8f7ea1c48d9b5f84f2c63cc82c3f27b5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131027"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Procedura: Creare una SharePoint web part usando una finestra di progettazione

  È possibile creare una web part aggiungendo un **elemento Web part visuale** a qualsiasi SharePoint progetto. Verrà aperta la finestra di progettazione di Visual Web Developer Visual Studio in cui è possibile aggiungere controlli e codice alla web part. Le web part visive funzionano allo stesso modo delle web part. L'unica differenza è che si progettano web part visive nella finestra di progettazione di Visual Web Developer.

## <a name="to-create-a-project-for-visual-web-parts"></a>Per creare un progetto per web part visive

1. Sulla barra dei menu scegliere **File**  > **Nuovo**  >  **Project**.
::: moniker range="=vs-2017"

2. Nella finestra **di dialogo Nuovo Project,** in **Visual C#** o **Visual Basic** espandere il nodo **Office/SharePoint** e quindi scegliere la categoria SharePoint **Soluzioni.**

3. Nell'elenco dei modelli di progetto **scegliere SharePoint 2013 - Web part** visiva e quindi scegliere il pulsante **OK.**

     Verrà **visualizzata SharePoint personalizzazione** guidata.
::: moniker-end
::: moniker range=">=vs-2019"
2. Nella finestra **di dialogo Create a New Project** selezionare la SharePoint Visual Web *Part** per la versione specifica SharePoint installata. Ad esempio, se è stata SharePoint 2019, **selezionare il modello SharePoint 2019 - Web part** visuale.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Se si vuole, modificare il nome del progetto e quindi scegliere **il pulsante** Crea.

::: moniker-end
4. Nella pagina **Specificare** il sito e il livello di sicurezza per il debug specificare l'URL di un sito di SharePoint nel computer locale e quindi scegliere il **pulsante** Fine.

     In **Esplora soluzioni** viene visualizzata una web part. Dopo aver progettato la web part nella finestra di progettazione di Visual Web Developer, la si testerà nel sito specificato.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Per aggiungere una web part visiva a un progetto SharePoint esistente

1. Nella barra dei menu scegliere **Project**  >  **Aggiungi nuovo elemento**.

2. Nella finestra **di dialogo Aggiungi nuovo** elemento scegliere il **Office/SharePoint** nodo.

3. Nell'elenco dei modelli di progetto scegliere **Web part visiva,** assegnare un nome e quindi scegliere il **pulsante** Aggiungi.

     In **Esplora soluzioni** viene visualizzata la web part. Dopo aver progettato la web part nella finestra di progettazione di Visual Web Developer, la si testerà nel sito specificato.

## <a name="see-also"></a>Vedi anche

- [Creare web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Procedura: Creare una SharePoint web part](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Procedura dettagliata: Creare una web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Procedura dettagliata: Creare una web part per SharePoint usando una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
