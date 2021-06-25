---
title: Pulsanti della finestra Proprietà | Microsoft Docs
description: Informazioni sui pulsanti visualizzati per impostazione predefinita sulla barra degli strumenti per Finestra Proprietà e sull'implementazione dei pulsanti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a9c45d6cf0f271683c3c708bd71ef46377a5c5ca
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903450"
---
# <a name="properties-window-buttons"></a>Pulsanti della finestra Proprietà
A seconda del linguaggio di sviluppo e del tipo di prodotto, alcuni pulsanti vengono visualizzati per impostazione predefinita sulla barra degli strumenti della **finestra** Proprietà. In tutti i casi, vengono visualizzati i pulsanti **Categorized**, **Alphabetized**, **Properties** e **Property Pages.** In Visual C# e Visual Basic viene **visualizzato anche** il pulsante Eventi. In alcuni Visual C++ vengono visualizzati i **messaggi di VC++** e i pulsanti Override di **VC.** Per altri tipi di progetto possono essere visualizzati pulsanti aggiuntivi. Per altre informazioni sui pulsanti nella **finestra** Proprietà, vedere [Finestra Proprietà.](../../ide/reference/properties-window.md)

## <a name="implementation-of-properties-window-buttons"></a>Implementazione dei pulsanti della finestra Proprietà
 Quando si fa clic sul **pulsante Categorized** Visual Studio chiama l'interfaccia sull'oggetto con lo stato attivo per ordinare le proprietà <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> in base alla categoria. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> viene implementato `IDispatch` nell'oggetto presentato alla **finestra** Proprietà.

 Sono presenti 11 categorie di proprietà predefinite, che hanno valori negativi. È possibile definire categorie personalizzate, ma è consigliabile assegnare loro valori positivi per distinguerle dalle categorie predefinite.

 Il <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> metodo restituisce il valore della categoria di proprietà appropriato per la proprietà specificata. Il <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> metodo restituisce una stringa che contiene il nome della categoria. È necessario fornire il supporto solo per i valori di categoria personalizzati perché Visual Studio i valori di categoria delle proprietà standard.

 Quando si fa clic **sul pulsante Alfabetico,** le proprietà vengono visualizzate in ordine alfabetico in base al nome. I nomi vengono recuperati da in `IDispatch` base a un algoritmo di ordinamento localizzato.

 Quando la **finestra** Proprietà è aperta, il **pulsante** Proprietà viene visualizzato automaticamente come selezionato. In altre parti dell'ambiente viene visualizzato lo stesso pulsante ed è possibile fare clic su di esso per visualizzare la **finestra** Proprietà.

 Il **pulsante Pagine delle** proprietà non è disponibile se non è implementato per `ISpecifyPropertyPages` l'oggetto selezionato. Le pagine delle proprietà visualizzano proprietà dipendenti dalla configurazione che in genere sono associate a soluzioni e progetti, ma possono anche essere associate agli elementi del progetto (ad esempio, in Visual C++).

> [!NOTE]
> Non è possibile aggiungere pulsanti della barra **degli strumenti alla** finestra Proprietà usando codice non gestito. Per aggiungere un pulsante della barra degli strumenti, è necessario creare un oggetto gestito che deriva da <xref:System.Windows.Forms.Design.PropertyTab> .

## <a name="see-also"></a>Vedere anche
- [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
