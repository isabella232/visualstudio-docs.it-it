---
title: Pulsanti della finestra proprietà | Microsoft Docs
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438401"
---
# <a name="properties-window-buttons"></a>Pulsanti della finestra Proprietà
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A seconda del linguaggio di sviluppo e il tipo di prodotto, alcuni pulsanti vengono visualizzati per impostazione predefinita nella barra degli strumenti per la **proprietà** finestra. In tutti i casi, il **Categorized**, **Alphabetized**, **proprietà**, e **pagine delle proprietà** vengono visualizzati i pulsanti. In Visual c# e Visual Basic, il **eventi** pulsante viene anche visualizzato. In determinate visivo C++ progetti, la **VC + + messaggi** e il **VC esegue l'override** vengono visualizzati i pulsanti. Pulsanti aggiuntivi potrebbero essere visualizzati per altri tipi di progetto. Per altre informazioni sui pulsanti nel **delle proprietà** finestra, vedere [finestra proprietà](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Implementazione di pulsanti della finestra proprietà  
 Quando si fa clic il **Categorized** pulsante, le chiamate di Visual Studio il <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> interfaccia sull'oggetto che ha lo stato attivo per ordinare le relative proprietà per categoria. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> viene implementato nel `IDispatch` oggetto che viene presentato il **proprietà** finestra.  
  
 Sono disponibili 11 categorie di proprietà predefiniti, che contengono valori negativi. È possibile definire categorie personalizzate, ma è consigliabile assegnare loro valori positivi per distinguerli dalle categorie predefinite.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> metodo restituisce il valore di categoria di proprietà appropriata per la proprietà specificata. Il <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> metodo restituisce una stringa che contiene il nome della categoria. È sufficiente fornire supporto per i valori di categoria personalizzata perché Visual Studio riconosce automaticamente i valori di categoria di proprietà standard.  
  
 Quando si sceglie la **Alphabetized** pulsante, le proprietà vengono visualizzate in ordine alfabetico in base al nome. I nomi vengono recuperati da `IDispatch` in base a un algoritmo di ordinamento localizzato.  
  
 Quando il **delle proprietà** finestra è aperta, il **proprietà** pulsante viene automaticamente visualizzato come selezionato. In altre parti dell'ambiente, viene visualizzato lo stesso pulsante, e si può fare clic per visualizzare il **proprietà** finestra.  
  
 Il **pagine delle proprietà** pulsante non è disponibile se `ISpecifyPropertyPages` non è implementata per l'oggetto selezionato. Proprietà dipendenti dalla configurazione di visualizzazione che sono in genere associate a soluzioni e progetti delle pagine delle proprietà, ma possono essere inoltre essere associato a elementi del progetto (ad esempio, in Visual C++).  
  
> [!NOTE]
> Non è possibile aggiungere i pulsanti della barra degli strumenti per la **proprietà** finestra usando il codice non gestito. Per aggiungere un pulsante della barra degli strumenti, è necessario creare un oggetto gestito che deriva da <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
