---
title: Pulsanti della finestra Proprietà | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b66015ef2e2ab0c8105b6f84486fa890adbf8b1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839696"
---
# <a name="properties-window-buttons"></a>Pulsanti della finestra Proprietà
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A seconda del linguaggio di sviluppo e del tipo di prodotto, per impostazione predefinita alcuni pulsanti vengono visualizzati nella barra degli strumenti della finestra **Proprietà** . In tutti i casi, vengono visualizzati i pulsanti **categorizzati**, in **ordine alfabetico**, **proprietà**e **pagine delle proprietà** . In Visual C# e Visual Basic viene visualizzato anche il pulsante **eventi** . In alcuni progetti di Visual C++, vengono visualizzati i **messaggi di VC + +** e i pulsanti delle **sostituzioni VC** . Per gli altri tipi di progetto possono essere visualizzati pulsanti aggiuntivi. Per ulteriori informazioni sui pulsanti nella finestra **Proprietà** , vedere [finestra Proprietà](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Implementazione dei pulsanti della finestra Proprietà  
 Quando si fa clic sul pulsante **categorizzato** , Visual Studio chiama l' <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> interfaccia sull'oggetto che ha lo stato attivo per ordinare le proprietà in base alla categoria. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> viene implementato nell' `IDispatch` oggetto presentato alla finestra **Proprietà** .  
  
 Sono presenti 11 categorie di proprietà predefinite, che hanno valori negativi. È possibile definire categorie personalizzate, ma è consigliabile assegnare loro valori positivi per distinguerli dalle categorie predefinite.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> metodo restituisce il valore della categoria di proprietà appropriato per la proprietà specificata. Il <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> metodo restituisce una stringa che contiene il nome della categoria. È sufficiente fornire supporto per i valori di categoria personalizzati perché Visual Studio conosce i valori della categoria di proprietà standard.  
  
 Quando si fa clic **sul pulsante in ordine alfabetico** , le proprietà vengono visualizzate in ordine alfabetico in base al nome. I nomi vengono recuperati in `IDispatch` base a un algoritmo di ordinamento localizzato.  
  
 Quando la finestra **Proprietà** è aperta, il pulsante **Proprietà** viene automaticamente visualizzato come selezionato. In altre parti dell'ambiente viene visualizzato lo stesso pulsante ed è possibile fare clic su di esso per visualizzare la finestra **Proprietà** .  
  
 Il pulsante **pagine delle proprietà** non è disponibile se `ISpecifyPropertyPages` non è implementato per l'oggetto selezionato. Le pagine delle proprietà visualizzano proprietà dipendenti dalla configurazione che in genere sono associate a soluzioni e progetti, ma possono essere anche associate agli elementi del progetto (ad esempio, in Visual C++).  
  
> [!NOTE]
> Non è possibile aggiungere pulsanti della barra degli strumenti alla finestra **Proprietà** utilizzando codice non gestito. Per aggiungere un pulsante della barra degli strumenti, è necessario creare un oggetto gestito che deriva da <xref:System.Windows.Forms.Design.PropertyTab> .  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
