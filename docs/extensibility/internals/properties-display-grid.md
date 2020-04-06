---
title: Griglia di visualizzazione delle proprietà Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d094c32ba8a64fc636f3fb6dfb2944dc3955628a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706181"
---
# <a name="properties-display-grid"></a>Griglia di visualizzazione delle proprietà

Nella finestra **Proprietà** vengono visualizzati i campi all'interno di una griglia. La colonna di sinistra contiene i nomi delle proprietà; la colonna di destra contiene i valori delle proprietà.

## <a name="work-with-the-grid"></a>Utilizzare la griglia

L'elenco a due colonne mostra le proprietà indipendenti dalla configurazione che possono essere modificate in fase di progettazione e le relative impostazioni correnti. Si noti che tutte le proprietà potrebbero non essere visualizzate. Una proprietà può essere impostata come nascosta, ad esempio, implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> metodo . In particolare, per nascondere le proprietà che hanno proprietà figlio:Specifically, to hide properties that have child properties:

1. Impostare `pfDisplay` il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> `FALSE`parametro in .

2. Impostare `pfHide` il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> `TRUE`parametro in .

Per eseguire il push delle informazioni <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>nella finestra **Proprietà,** l'IDE utilizza . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>viene chiamato da VSPackage per ogni finestra che contiene gli oggetti selezionabili con le proprietà correlate da visualizzare nel **proprietà** finestra. L'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> `GetProperty` **Esplora soluzioni**delle chiamate che usano [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) nella gerarchia del progetto per acquisire gli oggetti esplorabili nella gerarchia.

Se il pacchetto VSPackage non supporta [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>), l'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> tenta di utilizzare il valore per [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) che l'articolo o gli articoli della gerarchia forniscono.

Il progetto VSPackage non <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> è necessario creare perché il pacchetto di finestra fornito dall'IDE che lo implementa (ad esempio, **Esplora soluzioni**) costruisce <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> per suo conto.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>è costituito da tre metodi chiamati dall'IDE:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>contiene il numero di oggetti selezionati da visualizzare nella finestra **Proprietà.**

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>restituisce `IDispatch` gli oggetti selezionati per essere visualizzati nella finestra **Proprietà.**

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>rende possibile la selezione da parte <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> dell'utente di qualsiasi oggetto restituito da. In questo modo il pacchetto VSPackage aggiornare visivamente la selezione visualizzata all'utente nell'interfaccia utente.

La finestra **Proprietà** estrae le informazioni dagli `IDispatch` oggetti per recuperare le proprietà sfogliate. Il browser `IDispatch` Proprietà utilizza per chiedere all'oggetto `ITypeInfo`quali proprietà supporta `IDispatch::GetTypeInfo`tramite l'esecuzione di query , ottenuta da . Il browser utilizza quindi questi valori per popolare la finestra **Proprietà** e modificare i valori per le singole proprietà visualizzate nella griglia. Le informazioni sulle proprietà vengono mantenute all'interno dell'oggetto stesso.

Poiché gli oggetti `IDispatch`restituiti supportano , il chiamante può `IDispatch::Invoke` ottenere `ITypeInfo::Invoke` informazioni quali il nome dell'oggetto chiamando uno o con un identificatore di invio predefinito (DISPID) che rappresenta le informazioni desiderate. I DISPID dichiarati sono negativi per garantire che non siano in conflitto con gli identificatori definiti dall'utente.

Nella finestra **Proprietà** vengono visualizzati diversi tipi di campi a seconda degli attributi di proprietà specifiche di un oggetto selezionato. Questi campi includono caselle di modifica, elenchi a discesa e collegamenti alle finestre di dialogo dell'editor personalizzato.

- I valori contenuti in un elenco <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> enumerato vengono recuperati da una query in `IDispatch`. I valori ottenuti da un elenco enumerato possono essere modificati nella griglia delle proprietà facendo doppio clic sul nome del campo oppure facendo clic sul valore e selezionando il nuovo valore dall'elenco a discesa. Per le proprietà con impostazioni predefinite da elenchi enumerati, fare doppio clic sul nome della proprietà nell'elenco Proprietà per scorrere le scelte disponibili. Per le proprietà predefinite con solo due scelte, ad esempio true/false, fare doppio clic sul nome della proprietà per passare da una scelta all'altra.

- Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> `false`è , che indica che il valore è stato modificato, il valore viene visualizzato in grassetto. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>viene utilizzato per determinare se il valore può essere reimpostato sul valore originale. In tal caso, è possibile ripristinare l'impostazione predefinita facendo clic con il pulsante destro del mouse sul valore e scegliendo **Reimposta** dal menu visualizzato. In caso contrario, è necessario modificare manualmente il valore predefinito. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>consente inoltre di localizzare e nascondere i nomi delle proprietà visualizzate durante la fase di progettazione, ma non influisce sui nomi delle proprietà visualizzati in fase di esecuzione.

- Facendo clic sul pulsante con i puntini di sospensione (...) viene visualizzato un elenco di valori di proprietà da cui l'utente può selezionare (ad esempio una selezione colori o un elenco di tipi di carattere). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>fornisce questi valori.

## <a name="see-also"></a>Vedere anche

- [Estendere le proprietà](../../extensibility/internals/extending-properties.md)
