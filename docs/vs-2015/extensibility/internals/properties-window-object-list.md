---
title: Elenco di oggetti finestra delle proprietà | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87592deaec57b5638336cf191f12896cccbcb5b3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532958"
---
# <a name="properties-window-object-list"></a>Elenco di oggetti della finestra Proprietà
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [elenco di oggetti finestra proprietà](https://docs.microsoft.com/visualstudio/extensibility/internals/properties-window-object-list).  
  
Elenco di oggetti nel **proprietà** finestra è riportato un elenco di riepilogo a discesa che consente di modificare la selezione in altri oggetti disponibili all'interno di uno o più windows selezionati. Un oggetto diverso all'interno dell'elenco di selezione attiva una chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> per informare l'ambiente che è stato selezionato un nuovo oggetto. Le informazioni visualizzate nel **proprietà** finestra viene poi modificata per mostrare le proprietà associate all'oggetto appena selezionato.  
  
## <a name="the-object-list"></a>Elenco di oggetti  
 Elenco di oggetti è costituito da due campi: il nome dell'oggetto (visualizzato in grassetto) e il tipo di oggetto.  
  
 Il nome dell'oggetto visualizzato a sinistra del tipo di oggetto in grassetto viene recuperato dall'oggetto stesso tramite il `Name` proprietà fornita dal <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> interfaccia. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, l'unico metodo sul <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, restituisce <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> per coclasse tale interfaccia. Il **delle proprietà** utilizzati nella finestra <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> per ottenere il nome della coclasse, che viene visualizzato come il nome dell'oggetto nell'elenco a discesa.  
  
 Se l'oggetto non ha un `Name` proprietà, un nome non viene visualizzata nell'area di nome dell'elenco di oggetti. Se si desidera che il nome visualizzato nell'elenco di oggetti, è possibile aggiungere una proprietà Name per l'oggetto.  
  
 Se l'oggetto COM non implementa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, il **proprietà** viene visualizzato il nome di interfaccia al posto del nome di oggetto sul lato sinistro dell'elenco.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)

