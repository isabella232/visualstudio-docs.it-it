---
title: "Procedura: Impedire la visualizzazione di un'area del modulo di Outlook"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0aaeafe14f35092be30c982ebb758e40afedb8aa
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647081"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Procedura: Impedire la visualizzazione di un'area del modulo di Outlook
  Potrebbero esserci situazioni in cui si preferisce non Microsoft Office Outlook per visualizzare un'area del modulo per un particolare elemento. Ad esempio, se un elemento di contatto non contiene un indirizzo aziendale, è possibile impedire un'area del modulo che mostra la posizione dell'azienda in una mappa che venga visualizzato.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Per impedire la visualizzazione di un'area del modulo di Outlook  
  
1. Aprire il file di codice per l'area del modulo che si desidera modificare.  
  
2. Espandere la **Factory area del modulo** area di codice.  
  
3. Aggiungere codice per il `FormRegionInitializing` gestore eventi che imposta il <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> proprietà del <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> classe a **true**.  
  
   In questo esempio, se il contatto non contiene un indirizzo, il <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> è impostata su **true**, e non viene visualizzata l'area del modulo.  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procedura dettagliata: Progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Procedura dettagliata: Progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Procedura dettagliata: Importare un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  