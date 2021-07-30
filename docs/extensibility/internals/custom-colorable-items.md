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
ms.workload:
- vssdk
ms.openlocfilehash: 2a7fdc1223527f4dc58a49442b24fc6fc3c5c816
ms.sourcegitcommit: 2694ab246eb857a1c607738a67198c46f826f106
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2021
ms.locfileid: "114995226"
---
# <a name="custom-colorable-items"></a>Elementi colorabili personalizzati
È possibile eseguire l'override dell'elenco di tipi per la colorazione, ad esempio parole chiave e commenti, implementando elementi colorabili personalizzati come parte del servizio di linguaggio.

## <a name="user-settings-of-colorable-items"></a>Impostazioni utente degli elementi colorabili
 È possibile visualizzare la finestra di  **dialogo** Tipi di carattere e colori scegliendo Opzioni dal **menu** Strumenti e quindi selezionando Tipi di carattere **e colori** in **Ambiente**. Quando si seleziona una visualizzazione, ad esempio  **Editor** di testo o Finestra di **comando,** la casella di riepilogo Visualizza elementi mostra tutti gli elementi colorabili per tale visualizzazione. È possibile visualizzare e modificare il tipo di carattere, le dimensioni, il colore di primo piano e il colore di sfondo per ogni elemento colorabile. Le scelte vengono archiviate in una cache nel Registro di sistema e accessibili dal nome dell'elemento colorabile.

## <a name="presentation-of-colorable-items"></a>Presentazione di elementi colorabili
 Poiché l'IDE gestisce le sostituzioni utente degli elementi colorabili nella finestra di dialogo Tipi di carattere e colori, è necessario specificare un nome solo per ogni elemento colorabile personalizzato.  Questo nome è quello visualizzato **nell'elenco Elementi** visualizzati. Gli elementi colorabili vengono visualizzati in ordine alfabetico. Per raggruppare gli elementi colorabili personalizzati del servizio di linguaggio, è possibile iniziare ogni nome con il nome della lingua, ad esempio **NewLanguage - Comment** e **NewLanguage - Keyword**.

> [!CAUTION]
> È necessario includere il nome della lingua nel nome dell'elemento colorabile per evitare conflitti con i nomi degli elementi colorabili esistenti. Se si modifica il nome di uno degli elementi colorabili durante lo sviluppo, è necessario reimpostare la cache creata al primo accesso agli elementi colorabili. È possibile reimpostare la cache sperimentale con lo strumento **CreateExpInstance,** installato con Visual Studio SDK, in genere nella directory seguente nella cartella di Visual Studio di installazione:
>
> *VSSDK\VisualStudioIntegration\Tools\Bin*
>
> Per reimpostare la cache, immettere **CreateExpInstance /Reset**. Per altre informazioni su **CreateExpInstance,** vedere [Utilità CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).

 Il primo elemento nell'elenco di elementi colorabili non viene mai fatto riferimento. Il primo elemento corrisponde a un indice di elemento colorabile di 0 e fornisce sempre i colori e gli attributi di testo predefiniti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per tale elemento. Il modo più semplice per gestire questo elemento senza riferimenti è fornire un elemento colorabile segnaposto nell'elenco come primo elemento.

## <a name="implement-custom-colorable-items"></a>Implementare elementi colorabili personalizzati

1. Definire gli elementi da colorare nel linguaggio, ad esempio Parola chiave, Operatore e Identificatore.

2. Creare un'enumerazione di questi elementi colorabili.

3. Associare i tipi di token restituiti da un parser o uno scanner ai valori enumerati.

    Ad esempio, i valori che rappresentano i tipi di token possono essere gli stessi nell'enumerazione di elementi colorabili personalizzati.

4. Nell'implementazione del metodo nell'oggetto compilare l'elenco di attributi con i valori dell'enumerazione di elementi colorabili personalizzati corrispondenti ai tipi di token restituiti dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> parser o dallo scanner.

5. Nella stessa classe che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> l'interfaccia , implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> e i relativi due metodi e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .

6. Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

7. Se si desidera supportare valori di colore a 24 bit o alti, implementare anche <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> l'interfaccia .

8. Nell'oggetto del servizio di linguaggio creare un elenco contenente gli oggetti, uno per ogni elemento colorabile che il parser o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> lo scanner può identificare.

    È possibile accedere a ogni elemento nell'elenco usando il valore corrispondente dell'enumerazione di elementi colorabili personalizzati. Usare i valori di enumerazione come indice nell'elenco. Il primo elemento dell'elenco non è mai accessibile, perché corrisponde allo stile di testo predefinito che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce sempre se stesso. È possibile compensare questo problema inserendo un segnaposto colorabile all'inizio dell'elenco.

9. Nell'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metodo , restituire il numero di elementi nell'elenco di elementi colorabili personalizzati.

10. Nell'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodo , restituire l'elemento colorabile richiesto dall'elenco.

    Per un esempio di come implementare le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfacce e , vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> .

## <a name="see-also"></a>Vedere anche
- [Modello di un servizio di linguaggio legacy](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Colorazione della sintassi negli editor personalizzati](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementare la colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)
- [Procedura: Usare elementi colorabili predefiniti](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
