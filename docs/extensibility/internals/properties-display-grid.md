---
title: Proprietà Visualizza griglia | Microsoft Docs
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
ms.openlocfilehash: f9186d9c912f27ec1e782eb4c6e48de3b340a6c1fadbb711cc7c2db02ef7ab5d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401310"
---
# <a name="properties-display-grid"></a>Griglia di visualizzazione delle proprietà

Nella **finestra Proprietà** vengono visualizzati i campi all'interno di una griglia. La colonna a sinistra contiene i nomi delle proprietà. la colonna di destra contiene i valori delle proprietà.

## <a name="work-with-the-grid"></a>Usare la griglia

L'elenco a due colonne mostra le proprietà indipendenti dalla configurazione che possono essere modificate in fase di progettazione e le relative impostazioni correnti. Si noti che tutte le proprietà potrebbero non essere visualizzate. Una proprietà può essere impostata come nascosta, ad esempio, implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> metodo . In particolare, per nascondere le proprietà con proprietà figlio:

1. Impostare il `pfDisplay` parametro in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> su `FALSE` .

2. Impostare il `pfHide` parametro in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> su `TRUE` .

Per eseguire il push delle informazioni **nella finestra Proprietà,** l'IDE usa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> viene chiamato da VSPackage per ogni finestra che contiene oggetti selezionabili con proprietà correlate da visualizzare nella **finestra** Proprietà. **Esplora soluzioni'implementazione** delle <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> chiamate tramite `GetProperty` [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) nella gerarchia del progetto per acquisire gli oggetti esplorabili nella gerarchia.

Se il pacchetto VSPackage non supporta [l'__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>), l'IDE tenta di usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> usando il valore per [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) che l'elemento o gli elementi della gerarchia forniscono.

Il progetto VSPackage non deve creare perché il pacchetto finestra fornito dall'IDE che lo implementa (ad esempio, Esplora soluzioni ) costruisce per <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> suo  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> conto.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> è costituito da tre metodi chiamati dall'IDE:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> contiene il numero di oggetti selezionati da visualizzare nella **finestra** Proprietà.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> restituisce `IDispatch` gli oggetti selezionati per la visualizzazione nella **finestra** Proprietà.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> rende possibile la selezione di uno degli oggetti restituiti da <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> parte dell'utente. Ciò consente al VSPackage di aggiornare visivamente la selezione visualizzata all'utente nell'interfaccia utente.

La **finestra** Proprietà estrae informazioni dagli `IDispatch` oggetti per recuperare le proprietà da esplorare. Il browser Proprietà usa `IDispatch` per chiedere all'oggetto quali proprietà supporta tramite query su , ottenuto da `ITypeInfo` `IDispatch::GetTypeInfo` . Il browser usa quindi questi valori per popolare **la** finestra Proprietà e modificare i valori per le singole proprietà visualizzate nella griglia. Le informazioni sulle proprietà vengono mantenute all'interno dell'oggetto stesso.

Poiché gli oggetti restituiti supportano , il chiamante può ottenere informazioni quali il nome dell'oggetto chiamando o con un identificatore `IDispatch` `IDispatch::Invoke` dispatch predefinito (DISPID) che rappresenta le `ITypeInfo::Invoke` informazioni desiderate. I DISPID dichiarati sono negativi per assicurarsi che non siano in conflitto con gli identificatori definiti dall'utente.

Nella **finestra** Proprietà vengono visualizzati diversi tipi di campi a seconda degli attributi di proprietà specifiche di un oggetto selezionato. Questi campi includono caselle di modifica, elenchi a discesa e collegamenti a finestre di dialogo dell'editor personalizzate.

- I valori contenuti in un elenco enumerato vengono recuperati da una <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> query in `IDispatch` . I valori ottenuti da un elenco enumerato possono essere modificati nella griglia delle proprietà facendo doppio clic sul nome del campo oppure facendo clic sul valore e selezionando il nuovo valore dall'elenco a discesa. Per le proprietà con impostazioni predefinite da elenchi enumerati, fare doppio clic sul nome della proprietà nell'elenco Proprietà per scorrere le scelte disponibili. Per le proprietà predefinite con solo due opzioni, ad esempio true/false, fare doppio clic sul nome della proprietà per passare da una scelta all'altro.

- Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> è , a indicare che il valore è stato `false` modificato, il valore viene visualizzato in grassetto. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> viene usato per determinare se il valore può essere reimpostato sul valore originale. In tal caso, è possibile tornare all'impostazione predefinita facendo clic con il pulsante destro del mouse sul valore e scegliendo **Reimposta** dal menu visualizzato. In caso contrario, è necessario modificare manualmente il valore predefinito. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> consente anche di localizzare e nascondere i nomi delle proprietà visualizzate durante la fase di progettazione, ma non influisce sui nomi delle proprietà visualizzati durante la fase di esecuzione.

- Facendo clic sul pulsante con i puntini di sospensione (...) viene visualizzato un elenco di valori di proprietà da cui l'utente può selezionare ,ad esempio un selettore colori o un elenco di tipi di carattere. <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> fornisce questi valori.

## <a name="see-also"></a>Vedi anche

- [Estendere le proprietà](../../extensibility/internals/extending-properties.md)
