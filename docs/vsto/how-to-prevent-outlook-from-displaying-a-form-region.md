---
title: "Procedura: impedire la visualizzazione di un'area del modulo in Outlook"
description: Informazioni su come impedire a Microsoft Office Outlook di visualizzare un'area del modulo per un particolare elemento.
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
ms.workload:
- office
ms.openlocfilehash: f6e6b00e8e26d261aac18dd48af1d912bd6ffad1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899550"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Procedura: impedire la visualizzazione di un'area del modulo in Outlook
  Potrebbero essere presenti situazioni in cui non si desidera che Microsoft Office Outlook visualizzi un'area del modulo per un particolare elemento. Se, ad esempio, un elemento di contatto non contiene un indirizzo aziendale, è possibile impedire la visualizzazione di un'area del modulo che mostra la posizione dell'azienda in una mappa.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Per impedire a Outlook di visualizzare un'area del modulo

1. Aprire il file di codice per l'area del modulo che si desidera modificare.

2. Espandere l'area del codice **Factory dell'area del modulo** .

3. Aggiungere il codice al `FormRegionInitializing` gestore eventi che imposta la <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> proprietà della <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> classe su **true**.

   In questo esempio, se l'elemento contatto non contiene un indirizzo, la <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> proprietà viene impostata su **true** e l'area del modulo non viene visualizzata.

## <a name="example"></a>Esempio
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

## <a name="see-also"></a>Vedere anche
- [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)
- [Procedura dettagliata: progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Procedura dettagliata: progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Procedura dettagliata: importare un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
