---
title: Griglia di visualizzazione delle proprietà | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180387"
---
# <a name="properties-display-grid"></a>Griglia di visualizzazione delle proprietà
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nella finestra **Proprietà** vengono visualizzati i campi all'interno di una griglia. La colonna sinistra contiene i nomi delle proprietà; la colonna a destra contiene i valori delle proprietà.  
  
## <a name="working-with-the-grid"></a>Uso della griglia  
 L'elenco a due colonne Mostra le proprietà indipendenti dalla configurazione che possono essere modificate in fase di progettazione e le relative impostazioni correnti. Si noti che è possibile che tutte le proprietà non vengano visualizzate. Una proprietà può essere impostata come nascosta, ad esempio implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> metodo. In particolare, per nascondere le proprietà con proprietà figlio, vedere [nascondere proprietà con proprietà figlio](../../misc/hiding-properties-that-have-child-properties.md).  
  
 Per eseguire il push delle informazioni nella finestra **Proprietà** , l'IDE utilizza <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> viene chiamato da Vspackage per ogni finestra che contiene oggetti selezionabili con proprietà correlate da visualizzare nella finestra **Proprietà** . **Esplora soluzioni**l'implementazione delle <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> chiamate `GetProperty` utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> nella gerarchia del progetto per acquisire gli oggetti esplorabili nella gerarchia.  
  
 Se il pacchetto VSPackage non supporta <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , l'IDE tenta di usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> usando il valore per <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> l'elemento della gerarchia o gli elementi forniti.  
  
 Non è necessario creare il <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> pacchetto VSPackage del progetto perché il pacchetto della finestra fornito dall'IDE che lo implementa (ad esempio, **Esplora soluzioni**) costruisce per <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> suo conto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> è costituito da tre metodi chiamati dall'IDE:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> contiene il numero di oggetti selezionati da visualizzare nella finestra **Proprietà** .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Restituisce gli `IDispatch` oggetti selezionati per essere visualizzati nella finestra **Proprietà** .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> rende possibile la selezione da parte dell'utente degli oggetti restituiti da <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> . Ciò consente al pacchetto VSPackage di aggiornare visivamente la selezione visualizzata all'utente nell'interfaccia utente.  
  
  La finestra **Proprietà** estrae informazioni dagli `IDispatch` oggetti per recuperare le proprietà visualizzate. Il browser Properties USA `IDispatch` per richiedere all'oggetto le proprietà supportate eseguendo una query `ITypeInfo` , ottenuta da `IDispatch::GetTypeInfo` . Il browser usa quindi questi valori per popolare la finestra **Proprietà** e modificare i valori per le singole proprietà visualizzate nella griglia. Le informazioni sulle proprietà vengono mantenute all'interno dell'oggetto stesso.  
  
  Poiché gli oggetti restituiti supportano `IDispatch` , il chiamante può ottenere informazioni, ad esempio il nome dell'oggetto, chiamando `IDispatch::Invoke` o `ITypeInfo::Invoke` con un identificatore di invio (DISPID) predefinito che rappresenta le informazioni desiderate. I DISPID dichiarati sono negativi per assicurarsi che non siano in conflitto con gli identificatori definiti dall'utente.  
  
  Nella finestra **Proprietà** vengono visualizzati diversi tipi di campi a seconda degli attributi di proprietà specifiche di un oggetto selezionato. Questi campi includono caselle di modifica, elenchi a discesa e collegamenti a finestre di dialogo dell'editor personalizzato.  
  
- I valori contenuti in un elenco enumerato vengono recuperati da una <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> query a `IDispatch` . È possibile modificare i valori ottenuti da un elenco enumerato nella griglia Proprietà facendo doppio clic sul nome del campo oppure facendo clic sul valore e selezionando il nuovo valore dall'elenco a discesa. Per le proprietà con impostazioni predefinite degli elenchi enumerati, fare doppio clic sul nome della proprietà nell'elenco delle proprietà per scorrere le opzioni disponibili. Per le proprietà predefinite con solo due opzioni, ad esempio true/false, fare doppio clic sul nome della proprietà per passare tra le opzioni.  
  
- Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> è `false` , indicante che il valore è stato modificato, il valore viene visualizzato in grassetto. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> viene utilizzato per determinare se il valore può essere reimpostato sul valore originale. In tal caso, è possibile tornare all'impostazione predefinita facendo clic con il pulsante destro del mouse sul valore e scegliendo **Reimposta** dal menu visualizzato. In caso contrario, è necessario ripristinare manualmente il valore predefinito. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> consente inoltre di localizzare e nascondere i nomi delle proprietà visualizzate in fase di progettazione, ma non influisce sui nomi delle proprietà visualizzati in fase di esecuzione.  
  
- Facendo clic sul pulsante con i puntini di sospensione (...) viene visualizzato un elenco di valori di proprietà da cui l'utente può selezionare, ad esempio una selezione colori o un elenco di tipi di carattere. <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> fornisce questi valori.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
