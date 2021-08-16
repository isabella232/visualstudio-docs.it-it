---
title: 'Procedura: Creare una SharePoint web part usando una finestra di progettazione | Microsoft Docs'
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
ms.openlocfilehash: ac72b8e2d023fa71e48f01c7ddd9ed662eb89fd50287bd2dd1b854d523090a14
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409663"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Procedura: Creare una SharePoint web part usando una finestra di progettazione

  È possibile creare una web part aggiungendo un **elemento Visual Web Part** a qualsiasi SharePoint progetto. Verrà aperta la finestra di progettazione di Visual Web Developer Visual Studio in cui è possibile aggiungere controlli e codice alla web part. Le web part visive funzionano allo stesso modo delle web part. L'unica differenza è che si progettano web part visive nella finestra di progettazione di Visual Web Developer.

## <a name="to-create-a-project-for-visual-web-parts"></a>Per creare un progetto per web part visive

1. Sulla barra dei menu scegliere **File**  > **nuovo**  >  **Project**.
::: moniker range="=vs-2017"

2. Nella finestra **di dialogo Nuovo Project,** in **Visual C#** o **Visual Basic** espandere il nodo **Office/SharePoint** e quindi scegliere la categoria SharePoint **Solutions.**

3. Nell'elenco dei modelli di progetto **scegliere SharePoint 2013 - Web part visiva** e quindi scegliere **OK.**

     Verrà **SharePoint personalizzazione guidata.**
::: moniker-end
::: moniker range=">=vs-2019"
2. Nella finestra **di dialogo Create a New Project** selezionare SharePoint Visual Web *Part** per la versione specifica SharePoint installata. Ad esempio, se è stata SharePoint 2019, selezionare il **modello SharePoint 2019 - Web part** visiva.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Modificare il nome del progetto, se necessario, e quindi scegliere il **pulsante** Crea.

::: moniker-end
4. Nella pagina **Specificare il sito** e il livello di sicurezza per il debug specificare l'URL di un sito di SharePoint nel computer locale e quindi scegliere il **pulsante** Fine.

     In **Esplora soluzioni** viene visualizzata una web part. Dopo aver progettato la web part nella finestra di progettazione di Visual Web Developer, la si testerà nel sito specificato.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Per aggiungere una web part visiva a un progetto SharePoint progetto

1. Sulla barra dei menu **scegliere** Project Aggiungi nuovo  >  **elemento**.

2. Nella finestra **di dialogo Aggiungi nuovo** elemento scegliere il nodo **Office/SharePoint.**

3. Nell'elenco dei modelli di progetto scegliere **Visual Web Part,** assegnare un nome e quindi scegliere **il pulsante** Aggiungi.

     In **Esplora soluzioni** viene visualizzata la web part. Dopo aver progettato la web part nella finestra di progettazione di Visual Web Developer, la si testerà nel sito specificato.

## <a name="see-also"></a>Vedi anche

- [Creare web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Procedura: Creare una SharePoint web part](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Procedura dettagliata: Creare una web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Procedura dettagliata: Creare una web part per SharePoint usando una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
