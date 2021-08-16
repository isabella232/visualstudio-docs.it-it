---
title: "Procedura: Impedire Outlook visualizzare un'area del modulo"
description: Informazioni su come impedire Microsoft Office Outlook visualizzare un'area del modulo per un determinato elemento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 331667013d5591f57d96b9f1bfa5f7542042ecc072c2eb650bf2ae5bbd0292a0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408799"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Procedura: Impedire Outlook visualizzare un'area del modulo
  In alcune situazioni potrebbe non essere necessario Microsoft Office Outlook visualizzare un'area del modulo per un particolare elemento. Ad esempio, se un elemento contatto non contiene un indirizzo aziendale, è possibile impedire la visualizzazione di un'area del modulo che mostra la posizione dell'azienda in una mappa.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Per impedire Outlook visualizzare un'area del modulo

1. Aprire il file di codice per l'area del modulo da modificare.

2. Espandere **l'area del codice factory dell'area** del modulo.

3. Aggiungere al gestore `FormRegionInitializing` eventi il codice che imposta la proprietà della classe su <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> **true.**

   In questo esempio, se l'elemento contatto non contiene un indirizzo, la proprietà viene impostata <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> su **true** e l'area del modulo non viene visualizzata.

## <a name="example"></a>Esempio
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::


## <a name="see-also"></a>Vedere anche
- [Creare aree Outlook modulo](../vsto/creating-outlook-form-regions.md)
- [Procedura dettagliata: Progettare un'Outlook del modulo](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Procedura: Aggiungere un'area del modulo a Outlook progetto di componente aggiuntivo](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Procedura dettagliata: Progettare un'Outlook del modulo](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Procedura dettagliata: Importare un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
