---
title: "Procedura: Impedire a Outlook di visualizzare un'area del modulo"
description: Informazioni su come impedire a Microsoft Office Outlook di visualizzare un'area del modulo per un determinato elemento.
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
ms.openlocfilehash: 1dc9322dd2ad3c3a2111222d7491f9e1a82cd6c4
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825849"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Procedura: Impedire a Outlook di visualizzare un'area del modulo
  È possibile che in alcuni casi non si voglia Microsoft Office Outlook per visualizzare un'area del modulo per un particolare elemento. Ad esempio, se un elemento contatto non contiene un indirizzo aziendale, è possibile impedire la visualizzazione di un'area del modulo che mostra la posizione dell'azienda in una mappa.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Per impedire a Outlook di visualizzare un'area del modulo

1. Aprire il file di codice per l'area del modulo da modificare.

2. Espandere **l'area di codice Form Region Factory.**

3. Aggiungere il codice al `FormRegionInitializing` gestore eventi che imposta la proprietà della classe su <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> **true.**

   In questo esempio, se l'elemento contatto non contiene un indirizzo, la proprietà viene impostata su <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> **true** e l'area del modulo non viene visualizzata.

## <a name="example"></a>Esempio
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::


## <a name="see-also"></a>Vedere anche
- [Creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)
- [Procedura dettagliata: Progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo per Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Procedura dettagliata: Progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Procedura dettagliata: Importare un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
