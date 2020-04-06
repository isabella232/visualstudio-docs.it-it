---
title: Elenco oggetti della finestra Proprietà - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffe11ae6ebb4e692686c884b663a4f93d1466535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706141"
---
# <a name="properties-window-object-list"></a>Elenco di oggetti della finestra Proprietà
L'elenco di oggetti nella finestra **Proprietà** è un elenco a discesa che consente di modificare la selezione in altri oggetti disponibili all'interno di una o più finestre selezionate. La selezione di un oggetto diverso dall'interno di questo elenco attiva una chiamata per <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> informare l'ambiente che è stato selezionato un nuovo oggetto. Le informazioni visualizzate nella finestra **Proprietà** vengono quindi modificate per visualizzare le proprietà associate all'oggetto appena selezionato.

## <a name="the-object-list"></a>Elenco oggetti
 L'elenco di oggetti è costituito da due campi: il nome dell'oggetto (visualizzato in grassetto) e il tipo di oggetto.

 Il nome dell'oggetto visualizzato a sinistra del tipo di oggetto `Name` in grassetto <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> viene recuperato dall'oggetto stesso utilizzando la proprietà fornita dall'interfaccia . <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, l'unico <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>metodo <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> su , restituisce per la coclasse dell'interfaccia. La **Properties** finestra <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> Proprietà consente di ottenere il nome della coclasse, che viene visualizzato come nome dell'oggetto nell'elenco a discesa.

 Se l'oggetto non `Name` dispone di una proprietà, non viene visualizzato un nome nell'area Nome dell'elenco oggetti. È possibile aggiungere una proprietà Name all'oggetto se si desidera che il nome venga visualizzato nell'elenco degli oggetti.

 Se l'oggetto COM <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>non implementa , nella finestra **Proprietà** viene visualizzato il nome dell'interfaccia al posto del nome dell'oggetto sul lato sinistro dell'elenco.

## <a name="see-also"></a>Vedere anche
- [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
