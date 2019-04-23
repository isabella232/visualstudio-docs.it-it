---
title: Annuncio di rilevamento di selezione finestra proprietà | Microsoft Docs
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089263"
---
# <a name="announcing-property-window-selection-tracking"></a>Specifica della traccia della selezione per la finestra Proprietà
Se si desidera utilizzare con il **delle proprietà** finestra o il **proprietà** pagine, ad esempio, un modulo, testo o una selezione per il quale si desidera visualizzare le proprietà, è necessario avere una conoscenza approfondita di come si selezione delle coordinate. Ad esempio, è necessario sapere se si dispone di selezione singola o le selezioni multiple. È quindi necessario annunciare il tipo di selezione (uno o più) per l'IDE usando il <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaccia. Questa interfaccia fornisce le informazioni necessarie per la **proprietà** finestra.  
  
### <a name="to-announce-selection-to-the-environment"></a>Per annunciare selezione all'ambiente  
  
1. Chiamare `QueryInterface` per <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>.  
  
    1. A tale scopo, utilizzare il puntatore sito passato alla visualizzazione al momento della creazione.  
  
    2. Chiamare `QueryService` dalla vista per la `SID_STrackSelection` servizio.  
  
         Restituisce un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> metodo ogni volta che cambia la selezione e passare un puntatore a un oggetto che implementa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
     L'oggetto contenitore di selezione è possibile usare una o più selezioni e contiene le informazioni di selezione in un `IDispatch` oggetto. Chiama il <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> metodo invia una notifica la **proprietà** finestra modificata la selezione. Il **delle proprietà** finestra Usa quindi gli oggetti nelle <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> per determinare se una o più selezioni si sono verificati e quali sono le selezioni per l'oggetto effettivo.  
  
     Se si specifica una selezione multipla, il **proprietà** finestra Trova l'intersezione tra le proprietà comuni per gli oggetti. Se si specifica una selezione di singolo oggetto, il **proprietà** finestra Visualizza tutte le proprietà di un oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../extensibility/internals/extending-properties.md)   
 [Pagine delle proprietà](../extensibility/internals/property-pages.md)