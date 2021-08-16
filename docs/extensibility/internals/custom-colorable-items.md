---
title: Elementi colorabili personalizzati | Microsoft Docs
description: Informazioni su come creare elementi colorabili personalizzati come parte di un servizio di linguaggio eseguendo l'override degli elementi nella finestra di dialogo Tipi di carattere e colori, ad esempio parole chiave e commenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 662b440b716eed2f878f6ede3e21e7339ab209ded5055e8dbd0dcca02017d408
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121261372"
---
# <a name="custom-colorable-items"></a>Elementi colorabili personalizzati
È possibile eseguire l'override dell'elenco di tipi per la colorazione, ad esempio parole chiave e commenti, implementando elementi colorabili personalizzati come parte del servizio di linguaggio.

## <a name="user-settings-of-colorable-items"></a>Impostazioni utente degli elementi colorabili
 È possibile visualizzare la finestra di  **dialogo** Tipi di carattere e colori scegliendo Opzioni dal **menu** Strumenti e quindi selezionando Tipi di carattere e **colori** in **Ambiente**. Quando si seleziona una visualizzazione, ad esempio  **Editor** di testo o Finestra di comando **,** nella casella di riepilogo Elementi visualizzati vengono visualizzati tutti gli elementi colorabili per tale visualizzazione. È possibile visualizzare e modificare il tipo di carattere, le dimensioni, il colore di primo piano e il colore di sfondo per ogni elemento colorabile. Le scelte effettuate vengono archiviate in una cache nel Registro di sistema e sono accessibili dal nome dell'elemento colorabile.

## <a name="presentation-of-colorable-items"></a>Presentazione di elementi colorabili
 Poiché l'IDE gestisce le sostituzioni utente degli elementi colorabili nella finestra di dialogo Tipi di carattere e colori , è necessario specificare un nome solo per ogni elemento colorabile personalizzato.  Questo nome viene visualizzato **nell'elenco Elementi** visualizzati . Gli elementi colorabili vengono visualizzati in ordine alfabetico. Per raggruppare gli elementi colorabili personalizzati del servizio di linguaggio, è possibile iniziare ogni nome con il nome della lingua, ad esempio **NewLanguage - Comment** e **NewLanguage - Keyword**.

> [!CAUTION]
> È necessario includere il nome della lingua nel nome dell'elemento colorabile per evitare conflitti con i nomi di elementi colorabili esistenti. Se si modifica il nome di uno degli elementi colorabili durante lo sviluppo, è necessario reimpostare la cache creata al primo accesso agli elementi colorabili. È possibile reimpostare la cache sperimentale con lo strumento **CreateExpInstance,** installato con Visual Studio SDK, in genere nella directory seguente nella cartella Visual Studio di installazione:
>
> *VSSDK\VisualStudioIntegration\Tools\Bin*
>
> Per reimpostare la cache, immettere **CreateExpInstance /Reset**. Per altre informazioni su **CreateExpInstance,** vedere [Utilità CreateExpInstance.](../../extensibility/internals/createexpinstance-utility.md)

 Non viene mai fatto riferimento al primo elemento dell'elenco di elementi colorabili. Il primo elemento corrisponde a un indice colorabile di 0 e fornisce sempre i colori di testo e gli attributi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] predefiniti per tale elemento. Il modo più semplice per gestire questo elemento senza riferimenti è fornire un segnaposto colorabile nell'elenco come primo elemento.

## <a name="implement-custom-colorable-items"></a>Implementare elementi colorabili personalizzati

1. Definire gli elementi da colorare nella lingua, ad esempio Parola chiave, Operatore e Identificatore.

2. Creare un'enumerazione di questi elementi colorabili.

3. Associare i tipi di token restituiti da un parser o uno scanner ai valori enumerati.

    Ad esempio, i valori che rappresentano i tipi di token potrebbero essere gli stessi nell'enumerazione personalizzata degli elementi colorabili.

4. Nell'implementazione del metodo nell'oggetto compilare l'elenco di attributi con i valori dell'enumerazione di elementi colorabili personalizzati corrispondenti ai tipi di token restituiti dal parser o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> dallo scanner.

5. Nella stessa classe che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> l'interfaccia , implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> e i relativi due metodi, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .

6. Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

7. Se si desidera supportare valori di colore a 24 bit o alti, implementare anche <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> l'interfaccia .

8. Nell'oggetto servizio di linguaggio creare un elenco contenente gli oggetti, uno per ogni elemento colorabile che il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> parser o lo scanner può identificare.

    È possibile accedere a ogni elemento nell'elenco usando il valore corrispondente dall'enumerazione personalizzata degli elementi colorabili. Usare i valori di enumerazione come indice nell'elenco. Il primo elemento dell'elenco non è mai accessibile, perché corrisponde allo stile di testo predefinito che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce sempre se stesso. È possibile compensare questo problema inserendo un segnaposto colorabile all'inizio dell'elenco.

9. Nell'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metodo , restituire il numero di elementi nell'elenco di elementi colorabili personalizzati.

10. Nell'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodo , restituire l'elemento colorabile richiesto dall'elenco.

    Per un esempio di come implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> le interfacce e , vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> .

## <a name="see-also"></a>Vedi anche
- [Modello di un servizio di linguaggio legacy](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Colorazione della sintassi negli editor personalizzati](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementare la colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)
- [Procedura: Usare elementi colorabili predefiniti](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
