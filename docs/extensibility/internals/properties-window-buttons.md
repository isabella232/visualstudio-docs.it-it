---
title: Pulsanti della finestra Proprietà . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaa4db159ccb0ecf3d0e9c9243e23fcd0dacc455
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706178"
---
# <a name="properties-window-buttons"></a>Pulsanti della finestra Proprietà
A seconda del linguaggio di sviluppo e del tipo di prodotto, alcuni pulsanti vengono visualizzati per impostazione predefinita sulla barra degli strumenti della finestra **Proprietà.** In tutti i casi vengono visualizzati i pulsanti **Categorizzato**, **Alfabetico**, **Proprietà**e **Pagine delle proprietà.** In Visual C è e Visual Basic viene visualizzato anche il pulsante **Eventi.** In alcuni progetti di Visual C, vengono **visualizzati** i pulsanti Messaggi di VISUAL E C, quindi vengono visualizzati i pulsanti Messaggi di **Visual** C. È possibile visualizzare pulsanti aggiuntivi per altri tipi di progetto. Per ulteriori informazioni sui pulsanti nella finestra **Proprietà,** vedere [Finestra Proprietà](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Implementazione dei pulsanti della finestra Proprietà
 Quando si fa clic sul pulsante <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> **Categorizzato,** Visual Studio chiama l'interfaccia sull'oggetto che ha lo stato attivo per ordinare le proprietà per categoria. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>viene implementato `IDispatch` sull'oggetto presentato alla finestra **Proprietà.**

 Sono presenti 11 categorie di proprietà predefinite, che hanno valori negativi. È possibile definire categorie personalizzate, ma è consigliabile assegnare loro valori positivi per distinguerle dalle categorie predefinite.

 Il <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> metodo restituisce il valore della categoria di proprietà appropriata per la proprietà specificata. Il <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> metodo restituisce una stringa che contiene il nome della categoria. È sufficiente fornire il supporto per i valori di categoria personalizzati perché Visual Studio conosce i valori di categoria di proprietà standard.

 Quando si fa clic sul pulsante **In ordine alfabetico,** le proprietà vengono visualizzate in ordine alfabetico in base al nome. I nomi vengono `IDispatch` recuperati da in base a un algoritmo di ordinamento localizzato.

 Quando la finestra **Proprietà** è aperta, il pulsante **Proprietà** viene visualizzato automaticamente come selezionato. In altre parti dell'ambiente, viene visualizzato lo stesso pulsante ed è possibile fare clic su di esso per visualizzare la finestra **Proprietà.**

 Il pulsante Pagine delle `ISpecifyPropertyPages` **proprietà** non è disponibile se non è implementato per l'oggetto selezionato. Le pagine delle proprietà visualizzano le proprietà dipendenti dalla configurazione che sono in genere associate a soluzioni e progetti, ma possono anche essere associate agli elementi di progetto (ad esempio, in Visual C.

> [!NOTE]
> Non è possibile aggiungere pulsanti della barra degli strumenti alla finestra **Proprietà** utilizzando codice non gestito. Per aggiungere un pulsante della barra degli strumenti, è necessario creare un oggetto gestito che deriva da <xref:System.Windows.Forms.Design.PropertyTab>.

## <a name="see-also"></a>Vedere anche
- [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
