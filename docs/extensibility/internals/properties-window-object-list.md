---
title: Elenco oggetti finestra Proprietà | Microsoft Docs
description: Informazioni sulle interfacce usate per interagire con l'elenco di oggetti nel Finestra Proprietà nell'IDE di Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 92fcce4dc62cdc84d15ca6dc51420791d4460340
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875427"
---
# <a name="properties-window-object-list"></a>Elenco di oggetti della finestra Proprietà
L'elenco di oggetti nella finestra **Proprietà** è un elenco a discesa che consente di modificare la selezione in altri oggetti disponibili all'interno di una o più finestre selezionate. Se si seleziona un oggetto diverso dall'interno di questo elenco, viene attivata una chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> per informare l'ambiente che è stato selezionato un nuovo oggetto. Le informazioni visualizzate nella finestra **Proprietà** vengono quindi modificate per visualizzare le proprietà associate all'oggetto appena selezionato.

## <a name="the-object-list"></a>Elenco oggetti
 L'elenco di oggetti è costituito da due campi: il nome dell'oggetto (visualizzato in grassetto) e il tipo di oggetto.

 Il nome dell'oggetto visualizzato a sinistra del tipo di oggetto in grassetto viene recuperato dall'oggetto stesso utilizzando la `Name` proprietà fornita dall' <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> interfaccia. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, l'unico metodo su <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , restituisce <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> per la coclasse di tale interfaccia. La finestra **Proprietà** USA <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> per ottenere il nome della coclasse, che viene visualizzata come nome dell'oggetto nell'elenco a discesa.

 Se l'oggetto non dispone di una `Name` proprietà, non viene visualizzato alcun nome nell'area nome dell'elenco di oggetti. È possibile aggiungere una proprietà Name all'oggetto se si desidera che il nome venga visualizzato nell'elenco di oggetti.

 Se l'oggetto COM non implementa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , nella finestra **Proprietà** viene visualizzato il nome dell'interfaccia al posto del nome dell'oggetto sul lato sinistro dell'elenco.

## <a name="see-also"></a>Vedi anche
- [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
