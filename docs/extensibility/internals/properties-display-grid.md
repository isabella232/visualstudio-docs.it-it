---
title: Proprietà - Visualizzazione griglia | Microsoft Docs
description: Informazioni su dove si trovano i nomi delle proprietà e i campi dei valori delle proprietà nella griglia nel Finestra Proprietà e su come usare la griglia per estendere le proprietà.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d6ed5ce8863cef32c787d86a5d78c423d78fef4f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636132"
---
# <a name="properties-display-grid"></a>Griglia di visualizzazione delle proprietà

Nella **finestra Proprietà vengono** visualizzati i campi all'interno di una griglia. La colonna a sinistra contiene i nomi delle proprietà. la colonna di destra contiene i valori delle proprietà.

## <a name="work-with-the-grid"></a>Usare la griglia

L'elenco a due colonne mostra le proprietà indipendenti dalla configurazione che possono essere modificate in fase di progettazione e le relative impostazioni correnti. Si noti che tutte le proprietà potrebbero non essere visualizzate. Una proprietà può essere impostata come nascosta, ad esempio, implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> metodo . In particolare, per nascondere le proprietà con proprietà figlio:

1. Impostare il `pfDisplay` parametro in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> su `FALSE` .

2. Impostare il `pfHide` parametro in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> su `TRUE` .

Per eseguire il push delle informazioni **nella finestra** Proprietà, l'IDE usa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> viene chiamato dai pacchetti VSPackage per ogni finestra che contiene oggetti selezionabili con proprietà correlate da visualizzare nella **finestra** Proprietà. **Esplora soluzioni'implementazione** delle <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> chiamate di tramite `GetProperty` [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) nella gerarchia del progetto per acquisire gli oggetti esplorabili nella gerarchia.

Se il pacchetto VSPackage non supporta [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>), l'IDE tenta di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> usare usando il valore per [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) che l'elemento o gli elementi della gerarchia forniscono.

Il pacchetto VSPackage del progetto non deve essere creato perché il pacchetto di finestra fornito dall'IDE che lo implementa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> **(ad** esempio, Esplora soluzioni ) costruisce per <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> suo conto.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> è costituito da tre metodi chiamati dall'IDE:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> contiene il numero di oggetti selezionati da visualizzare nella **finestra** Proprietà.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> restituisce `IDispatch` gli oggetti selezionati per la visualizzazione nella **finestra** Proprietà.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> rende possibile la selezione da parte dell'utente di <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> qualsiasi oggetto restituito da . In questo modo il VSPackage può aggiornare visivamente la selezione visualizzata all'utente nell'interfaccia utente.

La **finestra** Proprietà estrae informazioni dagli `IDispatch` oggetti per recuperare le proprietà da esplorare. Il browser Proprietà usa `IDispatch` per chiedere all'oggetto quali proprietà supporta tramite una query su , `ITypeInfo` ottenuta da `IDispatch::GetTypeInfo` . Il browser usa quindi questi valori per popolare **la** finestra Proprietà e modificare i valori per le singole proprietà visualizzate nella griglia. Le informazioni sulle proprietà vengono mantenute all'interno dell'oggetto stesso.

Poiché gli oggetti restituiti supportano , il chiamante può ottenere informazioni quali il nome dell'oggetto chiamando o con un identificatore `IDispatch` `IDispatch::Invoke` di invio predefinito (DISPID) che rappresenta le `ITypeInfo::Invoke` informazioni desiderate. I DISPID dichiarati sono negativi per garantire che non siano in conflitto con gli identificatori definiti dall'utente.

Nella **finestra** Proprietà vengono visualizzati diversi tipi di campi a seconda degli attributi di proprietà specifiche di un oggetto selezionato. Questi campi includono caselle di modifica, elenchi a discesa e collegamenti a finestre di dialogo dell'editor personalizzate.

- I valori contenuti in un elenco enumerato vengono recuperati da una <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> query in `IDispatch` . I valori ottenuti da un elenco enumerato possono essere modificati nella griglia delle proprietà facendo doppio clic sul nome del campo oppure facendo clic sul valore e selezionando il nuovo valore dall'elenco a discesa. Per le proprietà con impostazioni predefinite degli elenchi enumerati, fare doppio clic sul nome della proprietà nell'elenco Proprietà per scorrere le opzioni disponibili. Per le proprietà predefinite con solo due opzioni, ad esempio true/false, fare doppio clic sul nome della proprietà per passare da una scelta all'altro.

- Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> è , a indicare che il valore è stato `false` modificato, il valore viene visualizzato in grassetto. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> viene usato per determinare se il valore può essere reimpostato sul valore originale. In questo caso, è possibile ripristinare l'impostazione predefinita facendo clic con il pulsante destro del mouse sul valore e scegliendo **Reimposta** dal menu visualizzato. In caso contrario, è necessario modificare manualmente il valore predefinito. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> consente inoltre di localizzare e nascondere i nomi delle proprietà visualizzate durante la fase di progettazione, ma non influisce sui nomi delle proprietà visualizzati in fase di esecuzione.

- Facendo clic sul pulsante con i puntini di sospensione (...) viene visualizzato un elenco di valori di proprietà che l'utente può selezionare, ad esempio una selezione colori o un elenco di tipi di carattere. <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> fornisce questi valori.

## <a name="see-also"></a>Vedi anche

- [Estendere le proprietà](../../extensibility/internals/extending-properties.md)
