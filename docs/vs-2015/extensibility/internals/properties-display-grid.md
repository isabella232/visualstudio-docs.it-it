---
title: Proprietà di visualizzazione griglia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5fd5e17d764336cda450c726023b209f89f194a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180387"
---
# <a name="properties-display-grid"></a>Griglia di visualizzazione delle proprietà
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il **proprietà** finestra Visualizza i campi all'interno di una griglia. La colonna a sinistra contiene i nomi delle proprietà; la colonna a destra contiene i valori delle proprietà.  
  
## <a name="working-with-the-grid"></a>Utilizzo della griglia  
 Nell'elenco di due colonne sono proprietà indipendenti dalla configurazione che può essere modificata in fase di progettazione e le relative impostazioni correnti. Si noti che tutte le proprietà potrebbero non essere visualizzate. Una proprietà può essere impostata come nascosta, ad esempio, implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> (metodo). In particolare, per nascondere le proprietà con proprietà figlio, vedere [nascondere le proprietà che hanno le proprietà figlio](../../misc/hiding-properties-that-have-child-properties.md).  
  
 Per inserire informazioni per il **delle proprietà** finestra, l'IDE Usa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> viene chiamato dai pacchetti VSPackage per ogni finestra che contiene oggetti selezionabili con le proprietà correlate da visualizzare nella **proprietà** finestra. **Esplora soluzioni**dell'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> chiamate `GetProperty` usando <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> nella gerarchia di progetto per acquisire gli oggetti visualizzabili nella gerarchia.  
  
 Se il pacchetto VSPackage non supporta <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, tenta di usare l'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> usando il valore per <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> che specifichino l'elemento della gerarchia o gli elementi.  
  
 Il progetto non è necessario creare VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> perché il pacchetto della finestra fornito dall'IDE che implementa (ad esempio, **Esplora soluzioni**) costruisce <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> per suo conto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> è costituito da tre metodi che vengono chiamati dall'IDE:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> contiene il numero di oggetti selezionati deve essere visualizzato nei **proprietà** finestra.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Restituisce il `IDispatch` gli oggetti selezionati deve essere visualizzato nei **proprietà** finestra.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> rende possibile per gli oggetti restituiti da <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> per essere selezionato dall'utente. In questo modo il pacchetto VSPackage aggiornare in modo visivo la selezione visualizzata all'utente nell'interfaccia utente.  
  
  Il **delle proprietà** finestra consente di estrarre informazioni dal `IDispatch` oggetti per recuperare le proprietà in fase di esplorazione. Usa il browser delle proprietà `IDispatch` per porre l'oggetto quali proprietà supporta eseguendo una query `ITypeInfo`, che viene ottenuto da `IDispatch::GetTypeInfo`. Il browser Usa quindi questi valori per popolare la **proprietà** finestra e modifica i valori per le singole proprietà visualizzati nella griglia. Le informazioni di proprietà viene mantenute all'interno dell'oggetto stesso.  
  
  Poiché supportano gli oggetti restituiti `IDispatch`, il chiamante può ottenere informazioni quali il nome dell'oggetto tramite la chiamata a `IDispatch::Invoke` o `ITypeInfo::Invoke` con ID predefiniti dispatch (DISPID) che rappresenta le informazioni desiderate. DISPID dichiarati sono negativo per verificare che non entrino in conflitto con identificatori definiti dall'utente.  
  
  Il **proprietà** finestra vengono visualizzati diversi tipi di campi in base gli attributi delle proprietà specifiche di un oggetto selezionato. Questi campi includono le caselle di modifica, elenchi a discesa e collegamenti a finestre di dialogo editor personalizzato.  
  
- I valori contenuti in un elenco enumerato vengono recuperati da un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> eseguire una query da `IDispatch`. I valori ottenuti da un elenco enumerato possono essere modificati nella griglia delle proprietà facendo doppio clic sul nome del campo o facendo clic su valore e selezionando il nuovo valore dall'elenco a discesa. Per le proprietà che hanno già impostazioni dagli elenchi enumerati, fare doppio clic sul nome della proprietà nell'elenco delle proprietà consente di scorrere le scelte disponibili. Per le proprietà predefinite con solo due opzioni, ad esempio true/false, fare doppio clic sul nome della proprietà da passare tra le scelte.  
  
- Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> è `false`, che indica che il valore è stato modificato, il valore viene visualizzato in grassetto. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> Consente di determinare se il valore può essere reimpostato sul valore originale. Se, pertanto, è possibile modificare il valore predefinito il valore di facendo clic e scegliendo **reimpostare** dal menu visualizzato. In caso contrario, è necessario modificare manualmente il valore sul valore predefinito. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> consente inoltre di localizzare e nascondere i nomi delle proprietà visualizzate durante la fase di progettazione, ma non influisce sui nomi delle proprietà visualizzate durante la fase di esecuzione.  
  
- Facendo clic sui puntini di sospensione (...) consente di visualizzare un elenco di valori di proprietà da cui l'utente può selezionare (ad esempio, una selezione colori o un elenco del tipo di carattere). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> Questi valori vengono forniti.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
