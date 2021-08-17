---
title: Elenco oggetti della finestra Proprietà | Microsoft Docs
description: Informazioni sulle interfacce usate per interagire con l'elenco di oggetti nel Finestra Proprietà nell'IDE Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7ce39d335d48335408eea192c23bd5a091900a48055dcad0d65671b158b7b6e5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275398"
---
# <a name="properties-window-object-list"></a>Elenco di oggetti della finestra Proprietà
L'elenco di oggetti nella finestra **Proprietà** è un elenco a discesa che consente di modificare la selezione in altri oggetti disponibili all'interno di una o più finestre selezionate. La selezione di un oggetto diverso da questo elenco attiva una chiamata a per informare l'ambiente che è stato selezionato <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> un nuovo oggetto. Le informazioni visualizzate nella finestra **Proprietà** vengono quindi modificate per visualizzare le proprietà associate all'oggetto appena selezionato.

## <a name="the-object-list"></a>Elenco di oggetti
 L'elenco di oggetti è costituito da due campi: il nome dell'oggetto (visualizzato in grassetto) e il tipo di oggetto.

 Il nome dell'oggetto visualizzato a sinistra del tipo di oggetto in grassetto viene recuperato dall'oggetto stesso usando la `Name` proprietà fornita <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> dall'interfaccia . <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, l'unico metodo su <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , restituisce per la <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> coclasse dell'interfaccia. La **finestra** Proprietà usa per ottenere il nome della coclasse, che viene visualizzato come <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> nome dell'oggetto nell'elenco a discesa.

 Se l'oggetto non dispone di una proprietà , non viene visualizzato un nome `Name` nell'area Nome dell'elenco di oggetti. È possibile aggiungere una proprietà Name all'oggetto se si vuole visualizzare il nome nell'elenco di oggetti.

 Se l'oggetto COM non implementa , nella finestra Proprietà viene visualizzato il nome dell'interfaccia al posto del nome dell'oggetto <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> sul lato sinistro dell'elenco. 

## <a name="see-also"></a>Vedi anche
- [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
