---
title: Elenco oggetti finestra Proprietà | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e50b3fe46edb8d14cad9a03a45bc8650cb9713ab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725191"
---
# <a name="properties-window-object-list"></a>Elenco di oggetti della finestra Proprietà
L'elenco di oggetti nella finestra **Proprietà** è un elenco a discesa che consente di modificare la selezione in altri oggetti disponibili all'interno di una o più finestre selezionate. Se si seleziona un oggetto diverso dall'interno di questo elenco, viene attivata una chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> per informare l'ambiente che è stato selezionato un nuovo oggetto. Le informazioni visualizzate nella finestra **Proprietà** vengono quindi modificate per visualizzare le proprietà associate all'oggetto appena selezionato.

## <a name="the-object-list"></a>Elenco oggetti
 L'elenco di oggetti è costituito da due campi: il nome dell'oggetto (visualizzato in grassetto) e il tipo di oggetto.

 Il nome dell'oggetto visualizzato a sinistra del tipo di oggetto in grassetto viene recuperato dall'oggetto stesso utilizzando la proprietà `Name` fornita dall'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, l'unico metodo su <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, restituisce <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> per la coclasse di tale interfaccia. La finestra **Proprietà** USA <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> per ottenere il nome della coclasse, visualizzata come nome dell'oggetto nell'elenco a discesa.

 Se l'oggetto non dispone di una proprietà `Name`, non viene visualizzato alcun nome nell'area nome dell'elenco di oggetti. È possibile aggiungere una proprietà Name all'oggetto se si desidera che il nome venga visualizzato nell'elenco di oggetti.

 Se l'oggetto COM non implementa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, nella finestra **Proprietà** viene visualizzato il nome dell'interfaccia al posto del nome dell'oggetto sul lato sinistro dell'elenco.

## <a name="see-also"></a>Vedere anche
- [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)