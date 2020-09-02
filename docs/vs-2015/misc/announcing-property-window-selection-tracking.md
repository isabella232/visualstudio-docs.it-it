---
title: Annuncio del rilevamento della selezione della finestra delle proprietà | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 6296993d3a1f5039024556f09b721daa82ca4f53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002448"
---
# <a name="announcing-property-window-selection-tracking"></a>Specifica della traccia della selezione per la finestra Proprietà
Se si desidera utilizzare la finestra **Proprietà** o le pagine delle **Proprietà** , ad esempio un form, un testo o una selezione per la quale si desidera visualizzare le proprietà, è necessario avere una conoscenza completa della modalità di coordinazione della selezione. È ad esempio necessario sapere se si dispone di una selezione singola o di più selezioni. È quindi necessario annunciare il tipo di selezione (uno o più) all'IDE usando l' <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaccia. Questa interfaccia fornisce le informazioni richieste dalla finestra **Proprietà** .  
  
### <a name="to-announce-selection-to-the-environment"></a>Per annunciare la selezione all'ambiente  
  
1. Chiamare `QueryInterface` per <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> .  
  
    1. A tale scopo, usare il puntatore del sito passato alla visualizzazione al momento della creazione.  
  
    2. Chiamare `QueryService` dalla vista per il `SID_STrackSelection` servizio.  
  
         Viene restituito un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> Metodo ogni volta che la selezione viene modificata e passare un puntatore a un oggetto che implementa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
     L'oggetto contenitore di selezione può utilizzare una o più selezioni e contiene le informazioni di selezione in un `IDispatch` oggetto. La chiamata al <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> metodo notifica alla finestra delle **Proprietà** che la selezione è stata modificata. La finestra **Proprietà** usa quindi gli oggetti in <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> per determinare se si sono verificate una o più selezioni e quali sono le selezioni di oggetti effettive.  
  
     Se si specifica una selezione multipla, la finestra **Proprietà** trova l'intersezione tra le proprietà comuni per gli oggetti. Se si specifica una selezione per singolo oggetto, nella finestra **Proprietà** vengono visualizzate tutte le proprietà per l'unico oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../extensibility/internals/extending-properties.md)   
 [Pagine delle proprietà](../extensibility/internals/property-pages.md)